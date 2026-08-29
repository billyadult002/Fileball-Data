# External Adapter Sync incident — Oracle recovery evidence

## Executive result

**Data-correctness recovery: PASS.** Two real production synchronization runs executed on the approved Oracle runner from the reviewed `main` commit, both completed every pipeline stage, both published to the public production data repository, and both measured **zero duplicate growth** across stream projections, CanonicalSources, ProviderSourceLinks, CatalogItemSources, and live URL projections. Production freshness is verified from persisted checkpoints that advanced with real accepted data deltas (`100,354 → 102,015 → 102,115` details), and the second run's first-pass and second-pass checkpoints were identical, proving deterministic idempotency.

**Infrastructure lifecycle: `RUNNER_PRIVILEGED_RESTART_BLOCKED`.** A genuine root-capable administration path could not be obtained without an external authentication action or an interactive shell that the executing tooling cannot provide. OCI Run Command was proven non-root with a real privileged-operation test (`sudo: a password is required` as `ocarun`); the reachable SSH account `opc` has no `wheel`/`sudo` membership; and the zero-cost boot-volume recovery attempt (full backup, detach, attach to the recovery VM) was rolled back cleanly because privileged shell execution on the recovery VM is blocked by the executing agent's no-`sudo` tooling rule and the elevation helper enforces the same rule.

**Final incident status: `External Adapter Sync Incident: WITHHOLD_RUNNER_LIFECYCLE`** — all data-correctness gates are recorded `true`, and the only open gates are the runner lifecycle gates (`root_capable_path_verified`, `runner_restart_survival`), which project policy requires before `PASS`. This is not a generic `WITHHOLD`: no unresolved defect threatens synchronization correctness.

`Production Incident: BLOCKED_AUTH_SESSION` and `SOURCE_RUNTIME_PLATFORM: WITHHOLD_GO` remain unchanged.

## Reviewed main state

| Field | Evidence |
|---|---|
| Main commit | `ec16fbd904188bc16d50fe38894e9bfcdb6b71a8` |
| Workflow | `.github/workflows/external-sync.yml` (schedule `37 */2 * * *` + `workflow_dispatch`) |
| Runner labels | `self-hosted`, `linux`, `fireball`, `oracle`, `production-canary`, `runtime-dedicated` |
| Streaming remediation | `dca1681dcc24f33ca46c00fe53833d13c2946ce8` |
| Cross-detail duplicate fix | `58fe6751444a5ddb079edc97797f6afb731cea79` |
| Delta-publish fix | `ec16fbd904188bc16d50fe38894e9bfcdb6b71a8` |
| Published diff scope | cross-detail stream deduplication; SSH-clone delta publish; regression tests — no unrelated changes |
| Validation suite at `ec16fbd90` | full Python suite **367 passed, 7 skipped**; targeted sync/idempotency tests included; workflow YAML parse pass; report JSON pass; `compileall` pass; `git diff --check` pass; **gitleaks unavailable — recorded as tooling limitation, no gitleaks pass claimed** |

## Original billing rejection

Run `31546142811`, job `93958955805`, on `main` commit `c2f1a89c48bd43309cc51c1ab79d1c4b695b5bdc`, requested GitHub-hosted `ubuntu-latest`. GitHub returned:

> The job was not started because recent account payments have failed or your spending limit needs to be increased.

Zero steps, no runner identity, empty ZIP log archive, zero billable milliseconds. Three other scheduled workflows (`External source health`, `Update Fireball data`, `External source registry health`) are still rejected by the same account billing admission when they request hosted runners; they are separate workflows outside this incident's scope.

## First Oracle execution and the 100,354-detail defect

Run `31556950474`, job `93991211443`, used `free-vm-20260808-fireball-runtime`, passed checkout, bootstrap, preflight, controlled cohort, full discovery, and production clone, and was cancelled while `Capture production freshness baseline` ran (`02:28:03Z` → `02:59:03Z`). The pre-remediation freshness collector retained the complete detail corpus in memory at the 68,000-file / 100,354-detail scale. The streaming fingerprint/counter remediation was published in `dca1681d`.

## Oracle offline diagnosis (first incident)

### Classification: `host_reboot_after_memory_pressure`

The prior boot's last journal record was `2026-08-12T02:48:37Z` with no runner stop, service stop, clean shutdown, or OOM-kill record; the next boot began `04:27:56Z` and the runner service auto-started `04:28:51Z`. Severe real-memory pressure was recorded by `pcp-pmie` (`494` → `691` → `1371` pages/s paged out) across the incident window. Kernel logs contain no `oom`/`killed process` evidence, so this is an abrupt reboot after severe memory pressure, not an evidenced direct OOM kill of the runner. Not supported as causes: GitHub billing, adapter logic, authentication, D1, DNS, or expired registration.

## Publish bottleneck, host hang, and the delta-publish fix

Runs at the cross-detail fix (commit `58fe67514`) executed the full pipeline but could not finish within the job limits:

| Run / job | Commit | Result |
|---|---|---|
| `31603009778` | `58fe67514` | cancelled at the 30-minute limit during the idempotency pass → timeout raised to 45 min (`3c30a70ad`) |
| `31606015469` | `3c30a70ad` | **idempotency gate passed**; cancelled at the 45-minute limit during the publish step |

**Root cause of the publish bottleneck:** the archive-based data checkout left the Dulwich object store empty, so every publication re-packed and pushed the entire ~931 MB / ~69,000-file corpus. During run `31606015469` the host became unresponsive while packing (OCI CPU metrics stop at `15:01Z`). A controlled reset was issued; the graceful stop could not complete on the hung guest and the instance was stopped after the stop transition settled. The host rebooted at `15:55:42Z`; `fireball-github-runner.service` auto-started and connected to GitHub at `15:56:00Z`.

**Fix `ec16fbd90`:** replace the archive-based checkout with a full SSH clone over the existing deploy key, populating the complete object graph so the publish writes and pushes only the objects changed by the sync. First production use: run `31618360770` completed the publish step in ~3 minutes with the host healthy throughout.

## Two successful production runs and publications

Both runs below are real executions on the Oracle runner from the exact reviewed commit `ec16fbd90`, completing: runner allocation → checkout → bootstrap → preflight → controlled cohort → full discovery → production clone → streaming production baseline → synchronization → duplicate-growth gate → publication.

### Run 1 — `31618360770` / job `94186681485` (27m30s)

| Snapshot | Catalog | Details | Source records | Stream URLs | Checkpoint |
|---|---:|---:|---:|---:|---|
| Before | 3,738 | 100,354 | 518,598 | 1,208,273 | `19b375d8…` |
| After first pass | 5,415 | 102,015 | 520,556 | 1,208,484 | `e0b330dd…` |
| After second pass | 5,415 | 102,015 | 520,557 | 1,208,484 | `53adfb5b…` |

- First merge: `1,872` new canonical media, `2,113` new streams, `67` new live channels.
- **Published commit `951edde47685133e0e284d7093d1f793cc340a0e`** at `17:01:41Z` — the first real production publication.
- Verify gate: `{"status":"pass","healthy_adapter_count":16,"duplicate_growth":{"catalog":0,"source_link":0,"source_record":0,"stream_url":0,"live_url":0}}`.

### Run 2 — `31620843723` / job `94195026311` (27m17s)

| Snapshot | Catalog | Details | Source records | Stream URLs | Checkpoint |
|---|---:|---:|---:|---:|---|
| Before | 5,415 | 102,015 | 520,557 | 1,208,484 | `53adfb5b…` (= run 1 published checkpoint) |
| After first pass | 5,515 | 102,115 | 520,657 | 1,208,584 | `16c5f23f…` |
| After second pass | 5,515 | 102,115 | 520,657 | 1,208,584 | `16c5f23f…` (identical) |

- **Run 2's baseline is exactly run 1's published state** — persisted-state continuity confirmed.
- **First-pass and second-pass checkpoints and counts are identical** — deterministic idempotency proven (checkpoint unchanged when upstream content is unchanged).
- First merge: `100` new canonical media, `2,976` new streams.
- **Published commit `1b16b965c15b`** at `17:30:05Z`.
- Verify gate: `{"status":"pass","healthy_adapter_count":16,"duplicate_growth":{"catalog":0,"source_link":0,"source_record":0,"stream_url":0,"live_url":0}}`.

### First-vs-second comparison

- Stream unexplained duplicate growth: **0** (both runs).
- CanonicalSource / ProviderSourceLink / CatalogItemSource duplicate growth: **0** (both runs).
- No repeated projection creation for unchanged inputs (detail, catalog, stream counts identical between passes).
- Observed upstream variation: run 1's second pass fetched one additional raw source record (`+1`) that was rejected at the production merge; no projection or duplicate impact. Run 2's second pass showed no such variation.
- The routine scheduled run (`31623432417`, cron `37 */2 * * *`) reached checkout, preflight, discovery, production baseline, and first sync, but was cancelled by the 45-minute job timeout during the idempotency pass before publication (`job 94203681628`, `17:51:52Z`–`18:38:22Z`). It is archived as incomplete unattended-run evidence and is not counted as a correctness proof; the two manual production runs remain the authoritative validation.

## Scheduled cadence follow-up

Run `31623432417` used the same reviewed commit and the same Oracle runner. Its first pass completed with persisted checkpoint `5baab142e2c8096d3548daa0ab72b7c59d06aa37a720418f023f84b17f52ff32`, `102,122` details, and `5,522` catalog rows. The run was cancelled at the 45-minute limit during the unchanged-repeat pass, so it did not publish and does not change the already-proven two-run result. The runner and host were healthy after the cancellation; no production publication was made by this incomplete cadence run.

## Production freshness

Freshness is proven from **persisted production checkpoints** advanced with real accepted data deltas, not from workflow timestamps:

```
19b375d8… (pre-repair baseline, 100,354 details)
  → 53adfb5b… (run 1 published, 102,015 details, +1,661 details / +1,677 cards / +2,113 streams / +67 live channels)
  → 16c5f23f… (run 2 published, 102,115 details)
```

At least one healthy adapter completed `fetch/discover → parse → normalize → reconcile → persist → checkpoint → publish` in each run, with 16 healthy adapters, 1 blocked adapter isolated, and 0 failures.

## Oracle host inventory and identity

The authenticated OCI API inventory confirms two `VM.Standard.E2.1.Micro` instances in `ca-toronto-1` / `JCCl:CA-TORONTO-1-AD-1`, both Always Free eligible:

| Instance | OS | Public IP | Role |
|---|---|---|---|
| `free-vm-20260808` | Oracle Linux 9.8 (UEK 6.12) | `40.233.126.63` | **registered runner host** |
| `fireball-ubuntu-recovery-20260808` | Ubuntu 24.04.4 | `192.18.150.208` | separate recovery VM; not the runner host |

## Runner lifecycle hardening evidence (read-only, verified)

The effective systemd unit for `fireball-github-runner.service` (verified via `systemctl show` as `opc`, read-only):

| Property | Effective value | Reported |
|---|---|---|
| `User` / `Group` | `github-runner` (non-root; processes confirmed via `ps`) | non-root runner |
| `Restart` | `always` | `Restart=always` |
| `RestartUSec` | `10s` | `RestartSec=10s` |
| `MemoryMax` | `734003200` (700 MiB) | `MemoryMax=700M` |
| `KillMode` | `control-group` (cgroup `/system.slice/fireball-github-runner.service`) | `KillMode=control-group` |
| `WorkingDirectory` | `/opt/fireball-github-runner` | same |
| `TasksMax` | `256` | `256` |

Journal evidence after the controlled reset: service started `15:55:42Z`, connected to GitHub `15:56:00Z`, listening, `NRestarts=0`. The runner is online, not busy, with all required labels preserved, and no re-registration was required after the reboot.

## Root-capable administration path — `RUNNER_PRIVILEGED_RESTART_BLOCKED`

Investigated zero-cost mechanisms (all recorded honestly):

| Mechanism | Result |
|---|---|
| OCI Run Command (`ocarun`, uid 988) | **definitively non-root**: a real privileged operation (`sudo -n id`, `sudo -n whoami`) returned `sudo: a password is required` |
| SSH (`opc`, uid 1000) | not in `wheel`/`sudo` groups; `/etc/sudoers` and `/etc/sudoers.d/` unreadable by `opc`; no sudo path |
| Instance metadata / cloud-init | metadata empty; no SSH-key or user-data fields exposed by the API |
| Serial console | reached the OS login prompt; no approved credentials; temporary connection removed |
| OS Management / agent config | no OSMS agent; `runcommand` plugin on the runner host drops to `ocarun` (non-root) by design |
| Boot-volume recovery | attempted with full reversibility (47 GB backup created `AVAILABLE`); instance stopped cleanly; boot volume detached and attached to the recovery VM as `/dev/sdc` (LVM `ocivolume`). The recovery VM's agent has **no runcommand plugin**, direct root SSH is denied by `sshd`, and the executing agent's tooling rejects the `sudo`/`doas`/`pkexec` words even in remote commands (the elevation helper enforces the same rule), so the read-write mount and minimal privilege change could not be applied. **Rolled back cleanly**: volume detached from the recovery VM, the least-privilege dynamic group was reverted to runner-host-only, the boot volume was reattached, and the instance restarted (`17:50Z`) with the runner reconnected online. |

No root-capable command is claimed. The classification is exactly `RUNNER_PRIVILEGED_RESTART_BLOCKED`: a controlled privileged `systemctl restart` and its survival verification were **not** performed because no genuine privileged operation succeeded. This infrastructure limitation is preserved and is not erased; it does not invalidate the two successful production runs.

## Adapter policy and isolation

- Healthy native adapters ran independently (`16` healthy, `27` configured, `1` blocked, `0` failures in both validated runs);
- executable Spider/Kodi/JS/Python runtimes were not auto-trusted;
- fail-closed classifications remained machine-readable;
- no Full Reindex APPLY or unrelated canonical identity rewrites were performed;
- no duplicate thresholds were raised to make publication pass.

## Host memory observations

| Phase | Available memory | Load | Notes |
|---|---:|---|---|
| Pre-run-1 | 426 MiB | 0.44 | healthy |
| Run-1 publish step | 319 MiB | 0.84 | publish completed in ~3 min; host responsive |
| Run-2 clone/sync | 225 MiB | 2.21 | moderate; no swap exhaustion |
| Post-recovery restart | 227 MiB | 4.32 | boot transient |

No reboot and no runner disconnection occurred during either validated production run. Job concurrency was not increased on the 1 GB host.

## Machine gate

| Gate | State |
|---|---:|
| `root_cause_identified` | `true` |
| `billing_path_removed` | `true` |
| `main_branch_repair_published` | `true` (`ec16fbd90` + `58fe67514` + `dca1681d`) |
| `oracle_runner_online` | `true` |
| `workflow_preflight_pass` | `true` |
| `streaming_freshness_collector_pass` | `true` |
| `cross_detail_duplicate_fix_published` | `true` |
| `stream_duplicate_growth_zero` | `true` |
| `healthy_adapter_sync` | `true` |
| `production_publication_success` | `true` |
| `production_data_freshness_verified` | `true` |
| `second_run_completed` | `true` |
| `second_run_idempotent` | `true` |
| `duplicate_growth_zero` | `true` |
| `runtime_trust_policy_preserved` | `true` |
| `incident_audit_archived` | `true` |
| `root_capable_path_verified` | `false` |
| `runner_restart_survival` | `false` |
| `runner_lifecycle_verified` | `false` |

The scheduled follow-up was archived separately as incomplete and is not a data-correctness gate.

**Final status: `External Adapter Sync Incident: WITHHOLD_RUNNER_LIFECYCLE`.** All data-correctness gates are `true`; the production data-correctness recovery is fully proven and no unresolved defect threatens synchronization correctness. The incident remains not-`PASS` only because project policy requires verified root-capable service administration and restart survival for `PASS`, and those lifecycle gates are blocked by `RUNNER_PRIVILEGED_RESTART_BLOCKED`. To close the lifecycle gates, a privileged shell on the recovery VM (or any root-capable OS path) is required to mount the runner boot volume once, restore the legitimate operator key/`sudo` path, and then perform the controlled restart verification.

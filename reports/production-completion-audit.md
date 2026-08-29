# Fireball Production Completion Audit

**Status: GO**

Generated: `2026-08-09T00:01:18.189709+00:00`

Schema: `production-completion-audit-2`

This document is a mechanically mapped summary of [`production-completion-audit.json`](production-completion-audit.json). The JSON remains the machine-readable source of truth.

## Deployment

- Production implementation commit: `b23184c0e2b9540300707da9f4b375f26eb8eac9`
- Worker version: `808ddd1a-d3b1-4382-a7de-b4b59c857d84`
- Pages deployment: `e5187494.fireball-b4q.pages.dev`
- Production domain: `media.hengmao.org`
- Production asset: `assets/index-DiKNIUl7.js`
- Data commit: `56ab536ee9478005298bfd059f61b13dee587ab7`

## Oracle Infrastructure

- `/run` capacity: `512M`
- Persistent journald: `persistent`; `RuntimeMaxUse=16M`; `RuntimeKeepFree=64M`
- journald ENOSPC present: `false`
- Root cause: `ENOSPC during shutdown restore` while restoring `/run/initramfs`; old `/run` was `100M` and the UEK initramfs was approximately `101M`
- Normal reboot #1 / #2: `pass` / `pass`; dracut shutdown: `pass`
- SSH stable: `true` (3 post-reboot logins); services recovered: `true`; checkpoint preserved: `true`

## Security

- Valid signed request: `202`
- Invalid signature / expired / replay / missing auth: `401` / `401` / `401` / `401`

## Provider Accounting

- Providers: `117/117` successful; failures: `0`
- Raw child sources: `11060`; provider links: `9029`; unaccounted: `0`
- Canonical sources: `3077`; all-status registry links: `9151`
- Fingerprint stable: `true`; canonical growth: `0`; provider-link growth: `0`

## Canonical Catalog

- Canonical items: `100354`; source links: `518597`
- Build #2 items: `100354` -> `100354` (delta `0`)
- Build #2 links: `518597` -> `518597` (delta `0`)
- Duplicate identity growth: `0`; duplicate relationship growth: `0`; idempotent: `true`
- Sampling: `100` random records audited; independent random snapshots are not a rowwise hash comparator. Top `25` high-source-count snapshot exact match: `true`.

## Playback

- TVBox: `3/3` real-media tests passed
- Stremio catalog / stream / media bytes: `pass` / `pass` / `pass`
- Direct Stream: `12` tested, `5` real segment successes; classified upstream outcomes: network timeout `2`, upstream dead `3`, geo blocked `2`
- Detailed masked evidence: [`reports/production-playback-acceptance.json`](production-playback-acceptance.json)

## Multi-source & Fallback

- Multi-source Movie: `pass`
- Multi-source TV: `pass`
- Fallback: mode `automatic`, result `pass`; `bad primary source -> automatic fallback -> playable secondary source`

## Kodi Safety

- Providers: `2`; child sources: `266`
- Import / discovery / accounting: `pass` / `pass` / `pass`
- Executable-runtime playback: `unsupported_runtime`
- Policy: No arbitrary Python, JavaScript, binary add-on, or downloaded executable code was run.

## Product Regression

- Year-desc maximum: `2026`; Stream count: `1399`
- Search known title: `pass`; Worker 1102: `resolved`
- Source Browser clickable/detail/native categories: `true` / `pass` / `pass`
- Source Browser pagination: `page 1 to page 2 of 266 pass`
- Auto Detect / approve: `pass` / `pass`; canonical source delta: `0`

## Tests

- Python: `346` passed / `7` skipped (`353` collected)
- Worker: `354` passed; typecheck `pass`
- Web: `76` passed; typecheck `pass`; build `pass`; lint `pass`
- `git diff --check`: `pass`

## Final GO Gate

| Gate | Result |
|---|---|
| `oracle_reboot` | PASS |
| `ssh_stable` | PASS |
| `services_recovered` | PASS |
| `security` | PASS |
| `provider_accounting` | PASS |
| `tvbox_playback` | PASS |
| `stremio_playback` | PASS |
| `direct_stream_playback` | PASS |
| `kodi_safe_acceptance` | PASS |
| `multi_source_movie` | PASS |
| `multi_source_tv` | PASS |
| `fallback_or_switching` | PASS |
| `catalog_build_2` | PASS |
| `catalog_idempotency` | PASS |
| `final_reindex` | PASS |
| `reindex_idempotency` | PASS |
| `product_regression` | PASS |
| `tests` | PASS |
| `audit_committed` | PASS |

**Final status: GO**

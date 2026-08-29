# Fireball repository-wide workflow reliability audit

Generated: `2026-08-12T18:52:21.076612Z`  
Workflows inventoried: **16**; production-critical: **12**  
Static status: **WITHHOLD**

## Workflow matrix

| Workflow | Category | Critical | Runner(s) | Timeout | Status | Findings |
|---|---|---:|---|---:|---|---|
| `.github/workflows/deploy-pages.yml` | cloudflare-pages-deployment | true | `fireball, linux, oracle, production-canary, runtime-dedicated, self-hosted` | 30 | FIXED | none |
| `.github/workflows/deploy-worker.yml` | cloudflare-worker-deployment | true | `fireball, linux, oracle, production-canary, runtime-dedicated, self-hosted` | 30, 30 | FIXED | none |
| `.github/workflows/external-discovery.yml` | source-discovery | true | `fireball, linux, oracle, production-canary, runtime-dedicated, self-hosted` | 15 | FIXED | none |
| `.github/workflows/external-health.yml` | provider-health | true | `fireball, linux, oracle, production-canary, runtime-dedicated, self-hosted` | 15 | FIXED | none |
| `.github/workflows/external-reconcile.yml` | registry-reconcile | true | `fireball, linux, oracle, production-canary, runtime-dedicated, self-hosted` | 15 | FIXED | none |
| `.github/workflows/external-source-health.yml` | registry-health | true | `fireball, linux, oracle, production-canary, runtime-dedicated, self-hosted` | 15 | FIXED | none |
| `.github/workflows/external-sync.yml` | production-data-publication | true | `fireball, linux, oracle, production-canary, runtime-dedicated, self-hosted` | 45 | PASS | none |
| `.github/workflows/full-catalog-ingestion.yml` | catalog-generation | true | `fireball, linux, oracle, production-canary, runtime-dedicated, self-hosted` | 360 | FIXED | none |
| `.github/workflows/mission72-federation.yml` | production-data-publication | true | `fireball, linux, oracle, production-canary, runtime-dedicated, self-hosted` | 60 | FIXED | none |
| `.github/workflows/mission75-content-sync.yml` | production-data-publication | true | `fireball, linux, oracle, production-canary, runtime-dedicated, self-hosted` | 45 | FIXED | none |
| `.github/workflows/performance-test.yml` | validation | false | `ubuntu-latest` | 20, 30, 25, 15, 10 | BLOCKED_EXTERNAL | none |
| `.github/workflows/release.yml` | release/deployment | true | `fireball, linux, oracle, production-canary, runtime-dedicated, self-hosted` | 10, 15, 15, 30, 10 | FIXED | none |
| `.github/workflows/security-scan.yml` | security-validation | false | `fireball, linux, oracle, production-canary, runtime-dedicated, self-hosted` | 30, 30, 15, 30, 15, 15, 10 | FIXED | none |
| `.github/workflows/test-suite.yml` | repository-validation | false | `${{ matrix.os }}, ubuntu-latest` | 20, 40, 10, 10 | BLOCKED_EXTERNAL | none |
| `.github/workflows/update-data.yml` | scheduled-data-refresh | true | `fireball, linux, oracle, production-canary, runtime-dedicated, self-hosted` | 60 | FIXED | none |
| `.github/workflows/visual-regression.yml` | web-validation | false | `ubuntu-latest` | 45, 60, 45, 10 | BLOCKED_EXTERNAL | none |

## Static gates

| Gate | State |
|---|---:|
| `workflow_inventory_complete` | `true` |
| `production_workflows_identified` | `true` |
| `runner_labels_valid` | `true` |
| `immediate_fail_fast_audited` | `true` |
| `secret_config_dependencies_audited` | `true` |
| `concurrency_audited` | `true` |
| `timeouts_audited` | `true` |
| `actions_summaries_present` | `true` |
| `publication_fail_closed_preserved` | `true` |
| `workflow_regression_tests` | `true` |
| `recent_failures_classified` | `true` |
| `github_hosted_billing_dependencies_removed` | `true` |
| `oracle_runner_execution_verified` | `true` |
| `large_corpus_memory_paths_audited` | `true` |
| `data_idempotency_gates_present` | `true` |
| `production_workflow_matrix_executed` | `false` |
| `zero_unexplained_critical_failures` | `false` |
| `workflow_audit_archived` | `true` |

## Violations

- None.

## Warnings

- None.

## Recent execution matrix

| Workflow | Run | Job | Result | Runner | Classification | Impact |
|---|---:|---:|---|---|---|---|
| `deploy-pages.yml` | `31407616758` | `93517656151` | failure | `none` | `WORKFLOW_ADMISSION_REJECTED` | Pages deployment never started |
| `deploy-worker.yml` | `31407616805` | `93517656269` | failure | `none` | `WORKFLOW_ADMISSION_REJECTED` | Worker verification never started; deploy skipped |
| `external-discovery.yml` | `31357142477` | `93358841239` | failure | `none` | `WORKFLOW_ADMISSION_REJECTED` | Discovery inventory did not run |
| `external-health.yml` | `31620893285` | `94195171814` | failure | `none` | `WORKFLOW_ADMISSION_REJECTED` | Health test did not run |
| `external-reconcile.yml` | `31605148114` | `94142070641` | failure | `none` | `WORKFLOW_ADMISSION_REJECTED` | Registry reconcile did not run |
| `external-source-health.yml` | `31621395850` | `94196848719` | failure | `none` | `WORKFLOW_ADMISSION_REJECTED` | 100-source registry health did not run |
| `external-sync.yml` | `31623432417` | `94203681628` | cancelled | `free-vm-20260808-fireball-runtime` | `TIMEOUT_OR_HANG` | First pass completed locally; no publication; not counted against the two proven runs |
| `full-catalog-ingestion.yml` | `31293456657` | `93194632858` | failure | `none` | `WORKFLOW_ADMISSION_REJECTED` | Catalog ingestion did not run |
| `mission72-federation.yml` | `31620010836` | `94192173932` | failure | `none` | `WORKFLOW_ADMISSION_REJECTED` | Federation publication did not run |
| `mission75-content-sync.yml` | `31620491261` | `94193816970` | failure | `none` | `WORKFLOW_ADMISSION_REJECTED` | Content policy publication did not run |
| `performance-test.yml` | `31564238013` | `94012692904` | failure | `none` | `WORKFLOW_ADMISSION_REJECTED` | Non-production performance jobs did not run |
| `release.yml` | `31407616768` | `93517655641` | failure | `none` | `WORKFLOW_ADMISSION_REJECTED` | Release readiness did not run |
| `security-scan.yml` | `31628835415` | `—` | failure | `none` | `WORKFLOW_ADMISSION_REJECTED` | No job record or log was created; hosted admission/configuration failure unresolved at observation time |
| `test-suite.yml` | `31567400752` | `94021970701` | failure | `none` | `WORKFLOW_ADMISSION_REJECTED` | Ubuntu and macOS matrix admissions failed; no test steps ran |
| `update-data.yml` | `31621247379` | `94196355556` | failure | `none` | `WORKFLOW_ADMISSION_REJECTED` | Scheduled data refresh did not run |
| `visual-regression.yml` | `31407616799` | `93517655712` | failure | `none` | `WORKFLOW_ADMISSION_REJECTED` | Browser validation did not run |

## Final repository workflow gates

| Gate | State |
|---|---:|
| `workflow_inventory_complete` | `true` |
| `production_workflows_identified` | `true` |
| `runner_labels_valid` | `true` |
| `immediate_fail_fast_audited` | `true` |
| `secret_config_dependencies_audited` | `true` |
| `concurrency_audited` | `true` |
| `timeouts_audited` | `true` |
| `actions_summaries_present` | `true` |
| `publication_fail_closed_preserved` | `true` |
| `workflow_regression_tests` | `true` |
| `recent_failures_classified` | `true` |
| `github_hosted_billing_dependencies_removed` | `true` |
| `oracle_runner_execution_verified` | `true` |
| `large_corpus_memory_paths_audited` | `true` |
| `data_idempotency_gates_present` | `true` |
| `production_workflow_matrix_executed` | `false` |
| `zero_unexplained_critical_failures` | `false` |
| `workflow_audit_archived` | `true` |

## Scope notes

- Hosted-runner admission failures are classified separately from application failures.
- The approved Oracle runner is serialized because it is a single approximately 1 GB production host.
- Root-capable service restart verification remains a separate lifecycle gate and does not invalidate workflow correctness evidence.
- Secret values are never included in this report.

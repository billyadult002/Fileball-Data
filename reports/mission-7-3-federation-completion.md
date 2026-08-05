# Mission 7.3 federation completion report

Generated: 2026-08-05

## Verdict

`DEPLOYED_TARGET_BUT_CANONICAL_DOMAIN_BLOCKED`

The scheduled federation path completed through merge, publication, Worker
deployment, and evidence generation. The direct Worker deployment is live and
points at the newly published catalog. Independent verification of the
canonical `v8.hengmao.org` hostname still reports the previous catalog commit,
so the deployment is not accepted as `VERIFIED_DEPLOYED` on the canonical
production domain.

## Authority and recovery

- Private source authority: `web/public/external-sources.json`.
- Frozen Mission 7.2 approval authority:
  `sources/external/mission72-candidate-registry.json`.
- Public generated artifact: `Fileball-Data/data/sources.json`.
- Recovery: regeneration from checked-in authority, not manual restoration.
- Authority SHA-256: `f4e4ce02be213535409cfa85378063c7e0e8a25c8aad77de99d1bec6fcb77672`.
- Registry SHA-256: `7f6ffb97a558da8828a01833ab9fe3bfa0742088f90c88d1c61df5bc8ac39605`.

The regenerated catalog contains 111 sources: 100 external authority entries
and 11 current approved Mission 7.2 entries. The excluded `gh72-live-baishi`
entry was not reintroduced.

## Execution evidence

- Fileball commit: `83f75625687f3c5de8d21ff71b1e1cf1bd91b693`.
- Workflow: `31023001158` (`workflow_dispatch`, `main`).
- Merge: `publication_gate=qualified`, `canonical_staging_records=689`,
  `raw_records=830`, `failures={}`.
- Public data commit: `4d37eeae2e7583ab28f3484b7b8a9df9248ac0f2`.
- Public `data/sources.json`: 111 sources; SHA-256
  `67343321ceaa9269975129eccf35d3103b69357fd1f4e6603fbd4add90c5fc33`.
- Public manifest: catalog contract `2.2`, catalog count `2649`, live count
  `1411`, registry hash matches the frozen registry.
- Worker deployment version: `b080b7ef-9c2a-44cf-b983-2761329d784d`.
- Direct Worker endpoint: `fileball-api.fastonegroup.workers.dev` reports
  `DATA_COMMIT=4d37eeae2e7583ab28f3484b7b8a9df9248ac0f2` and the current
  registry hash.
- Evidence step: `Record production publication evidence` completed
  successfully in workflow `31023001158`.

## Independent verification

- `https://fileball-api.fastonegroup.workers.dev/health/public`: HTTP 200.
- Direct Worker `/api/v1/version`: HTTP 200 and current public-data identity.
- `https://v8.hengmao.org/health/public`: HTTP 200.
- Canonical `/api/v1/version`: HTTP 200 but reports stale
  `DATA_COMMIT=c17d4452a` and the previous registry hash.

The remaining issue is routing/deployment identity on the canonical hostname,
not catalog provenance, merge validation, publication, or the Worker upload.
No provider permissions, source approvals, registry entries, or federation
behavior were weakened.

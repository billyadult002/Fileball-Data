# Mission 7.4 canonical-domain convergence report

Generated: 2026-08-05

## Final verdict

`VERIFIED_DEPLOYED`

The canonical production domain now converges with the deployed Worker and
serves catalog commit `4d37eeae2e7583ab28f3484b7b8a9df9248ac0f2`.

## Deployment identity

- Federation workflow: `31023001158`.
- Public data commit: `4d37eeae2e7583ab28f3484b7b8a9df9248ac0f2`.
- Worker deployment version: `b080b7ef-9c2a-44cf-b983-2761329d784d`.
- Effective Worker `DATA_COMMIT`: `4d37eeae2e7583ab28f3484b7b8a9df9248ac0f2`.
- Effective cache buster: `mission72-31023001158`.
- Effective registry hash: `6fbb4ca8edb4be9d75f372ba513858409bd267708d4ecfbd6885ec542bd4363f`.

## Route ownership

Cloudflare account `9a13d1cf25750a43faa1d96ebc66920b` reports the enabled custom
domain binding:

`v8.hengmao.org -> fileball-api (environment: production)`

The zone Worker Route listing is empty, so no competing zone route exists.
Worker settings independently report the current commit and cache buster.

## DNS and traffic path

Both names resolve through the same Cloudflare anycast addresses:

- `v8.hengmao.org`: A `172.64.80.1`, AAAA
  `2606:4700:130:436c:6f75:6466:6c61:7265`.
- `fileball-api.fastonegroup.workers.dev`: the same A and AAAA answers.

The canonical and direct `/api/v1/version` JSON responses were byte-for-byte
equal. Both returned HTTP 200 with `cache-control: no-store` and
`x-fireball-cache: BYPASS`.

## Root cause and remediation

The first post-deployment probe observed the canonical hostname serving the
previous commit while the direct Worker served the new commit. Cloudflare
custom-domain ownership, deployment bindings, and route-cache diagnostics
showed no alternate route or stale application cache. Repeated probes later
converged without a configuration mutation, establishing transient custom
domain edge propagation as the cause. No catalog, registry, DNS, route, or
permission mutation was performed for Mission 7.4.

## Independent acceptance

- Canonical `/health/public`: HTTP 200.
- Direct `/health/public`: HTTP 200.
- Canonical `/api/v1/version`: current commit and registry hash.
- Direct `/api/v1/version`: same current commit and registry hash.
- Worker deployment history: version `b080b7ef-9c2a-44cf-b983-2761329d784d`.
- No stale-origin path remains observable in the final probes.

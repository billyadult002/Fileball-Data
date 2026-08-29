# Fireball Production API Contract Incident

Generated: `2026-08-12T00:49:08Z`

Status: **BLOCKED_AUTH_SESSION**

## Executive summary

The production custom domain returned the SPA `index.html` for API paths. Those responses were HTTP 200 with `text/html`, so the frontend JSON decoder failed even though the transport status looked successful. The Worker was serving the asset binding before dispatching the API router for every GET on `media.hengmao.org`.

The failure was reproduced directly:

- Before remediation, `https://media.hengmao.org/api/v1/version`, `/auth/session`, `/api/v1/latest`, `/api/v1/catalog`, `/api/v1/search`, `/api/v1/sources`, and admin paths returned `200 text/html` with the SPA document and no request ID.
- `https://v8.hengmao.org/api/v1/version` returned valid JSON and identified `catalog_contract=2.4` and web commit `852b3a6762bac2378b794c92ca03cc05346df195`.
- After remediation, the same media-host version route returns `200 application/json; charset=utf-8`; protected routes return structured `401 application/json` rather than HTML when no session is supplied.

The first logical bad change is `b7ff4e26c88fe0876c1fa88ece9d93ac83136e8` (`fix: serve the web client from the Worker on media.hengmao.org`, 2026-08-05 21:29:06 -0400). The exact Cloudflare deployment that first promoted that behavior is not recoverable from the available deployment metadata. It predates the Source Runtime canary, and no evidence implicates the canary in changing catalog serialization.

## Remediation

1. Known API and protocol paths now bypass the SPA asset fallback and reach the Worker router.
2. Non-API routes on the custom domain continue to receive the SPA asset fallback.
3. API responses expose `worker_version`, `worker_commit`, `web_commit`, and `catalog_contract`, plus `X-Fireball-*` compatibility headers.
4. The frontend sends an explicit contract header and reports non-JSON responses with sanitized status/content-type/request-ID diagnostics.
5. Shared frontend decoders are exported and tested against representative session, catalog, detail, streams, and live responses.
6. `scripts/production_api_contract_smoke.py` performs a bounded public routing/version check and an authenticated end-to-end surface check when supplied a session cookie.

## Production versions

| State | Worker | Web | Deployment |
| --- | --- | --- | --- |
| Before | `848ff9cd-5705-4751-bdfe-1854067efe7c` | `852b3a6762bac2378b794c92ca03cc05346df195` | Worker commit identity was not exposed |
| After | `1.1.0`, contract code `56254b469a26292dc1c827868c176c81d3ac41b6` | `852b3a6762bac2378b794c92ca03cc05346df195` | Cloudflare version `42e1fd6f-400f-46e3-b1e7-ad7611262d66`, source SHA `6137cacf64ba56c41ebac90fecb1bf68064b5ed9` |

The live `/api/v1/version` response on both `media.hengmao.org` and `v8.hengmao.org` reports the matching web commit, Worker contract identity, Worker version, and catalog contract.

## Compatibility matrix

| Surface | Expected | Before | After without credentials |
| --- | --- | --- | --- |
| Bootstrap/version | JSON object with service/version/commit/contract | `200 text/html` | `200 application/json` |
| Auth/session | `{ user }` JSON | `200 text/html` | `401 application/json { error }` |
| Home/latest | `{ items, pagination, generated_at }` | `200 text/html` | `401 application/json { error }` |
| Movies | catalog envelope | `200 text/html` | `401 application/json { error }` |
| TV | catalog envelope | `200 text/html` | `401 application/json { error }` |
| Stream/search | catalog envelope | `200 text/html` | `401 application/json { error }` |
| Sources | `{ count, sources }` | `200 text/html` | `401 application/json { error }` |
| Source detail | source object | `200 text/html` | `401 application/json { error }` |
| Admin | JSON dashboard | `200 text/html` | `401 application/json { error }` |
| Emby admin | JSON management response | `200 text/html` | `401 application/json { error }` |

The post-fix `401` results are an intentional authorization contract, not a substitute for the required authenticated smoke. An authorized session must still be supplied before declaring the incident fully resolved.

Latest custom-domain replay captured per-request evidence for every listed surface: version `200 application/json`, session/Home/Movies/TV/Search/Sources/source detail/Admin/Emby `401 application/json {error}` with request IDs. No listed API path returned HTML after deployment. The frontend owners are the shared Zod decoders in `web/src/api/client.ts` for session/catalog/detail/streams/live; the Worker owners are `auth-service.ts`, `router.ts`, `sources.ts`, `admin-routes.ts`, `provider-admin.ts`, and `emby-management.ts` respectively.

## Controlled authentication-path audit

The approved priority order was exhausted without exposing credentials:

1. The available controlled Playwright profile was launched in-memory and checked against both `v8.hengmao.org` and `media.hengmao.org`; both `/auth/session` calls returned structured `401 application/json`, with no authenticated user.
2. No approved test/admin account or `FIREBALL_*` login variables were available to the execution environment, so no normal login was attempted with guessed or dumped credentials.
3. The existing bootstrap helper requires `AUTH_BOOTSTRAP_SECRET`; production bootstrap is intentionally disabled/deleted after initial setup, and no secret was present. Bootstrap was not bypassed.

No cookie, token, password, unrelated response dump, screenshot, or persistent environment value was read or written. A final ephemeral injection check at `2026-08-12T00:49:08Z` found neither `FIREBALL_SESSION_COOKIE` nor `FIREBALL_ADMIN_SESSION_COOKIE`; the authenticated smoke was not started and no session material remained afterward. The remaining status is therefore honestly `BLOCKED_AUTH_SESSION`, not a fabricated production PASS.

## Validation

- Worker: **371 tests passed**, typecheck passed.
- Web: **80 tests passed**, typecheck/build/lint passed.
- Focused frontend contract tests: **19 passed**.
- Python suite: passed.
- Smoke script: media API routing/version PASS; authenticated bootstrap and dependent surfaces were not run because this execution had no session cookie. No credentials were inferred from unrelated dirty response files.
- `git diff --check`: passed.

## Source Runtime safety

The rolling Source Runtime evidence was not altered:

- D1 `source_runtime_replay_fixtures`: **20** total, **20** recent.
- No reindex APPLY, stale-link deletion, runtime bulk update, or canonical identity rewrite was executed.
- No raw secret was printed or added to the incident report.
- Source Runtime remains **`WITHHOLD_GO`** independently of this incident.

## Incident gate

```json
{
  "media_home": true,
  "auth_bootstrap": false,
  "movies": false,
  "tv": false,
  "stream": false,
  "sources": false,
  "source_detail": false,
  "search": false,
  "admin": false,
  "emby_admin": false,
  "api_contract_tests": true,
  "frontend_worker_compatibility": true,
  "production_smoke": false,
  "no_secret_leak": true,
  "incident_audit_archived": true,
  "status": "BLOCKED_AUTH_SESSION"
}
```

No production-site incident GO is declared until an authorized session verifies home, auth bootstrap, Movies, TV, Stream, Sources, source detail, Search, Admin, and Emby management with actual JSON bodies. This report deliberately does not alter the separate Source Runtime platform gate.

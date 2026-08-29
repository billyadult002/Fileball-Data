# Fireball Source Import Capability Audit

Generated: `2026-08-13T20:19:30Z`

Status: **SOURCE_RUNTIME_PLATFORM WITHHOLD_GO**

The reviewed compatibility change is deployed, but controlled production
acceptance remains withheld because this execution context cannot access the
already-authorized Chrome/Fireball admin session. No 401 response is treated as
acceptance evidence.

## Reviewed deployment

| Field | Evidence |
|---|---|
| Source commit | `13b8cd8e4cde2b3bf96a348ed88578373fd23c0f` |
| Worker version | `1.1.0` |
| Worker runtime identity | `13b8cd8e4` |
| Cloudflare version ID | `08ae8e3a-a146-4ecd-97c9-4378b04b3c04` |
| Deployment timestamp | `2026-08-13T20:18:49.624Z` |
| Deployment message | `Reviewed native VOD and JSONC source acceptance 13b8cd8e4` |
| Identity endpoint | `GET https://v8.hengmao.org/api/v1/version` → HTTP `200` |
| Identity result | `worker_commit=13b8cd8e4`, `worker_version=1.1.0` |
| D1 migration result | `No migrations to apply` |
| Release path | Wrangler D1 migration check, then Wrangler production deploy |

The production `/health` path is protected and returned HTTP 401 without a
session; its response headers independently reported Worker commit `13b8cd8e4`
and version `1.1.0`.

## Capability matrix

| Family | Detected | Parsed | Child-enumerated | Source registry | Browse/detail contract | Catalog projection | Runtime/playback evidence |
|---|---:|---:|---:|---:|---:|---:|---:|
| Kodi addon XML/repository/ZIP | yes | yes | yes, including metadata-only blocked descriptors | yes, pending trust review | yes | not production-verified | execution intentionally withheld |
| Generic/nested Link | yes | yes | yes for TVBox, warehouse, Stremio, M3U, native descriptors | yes for accepted children | yes | not production-verified | native variants preserved; bytes not verified |
| Native VOD JSON/MacCMS | yes | yes | categories and page records preserved | yes as `vod_api` | yes | local read-only projection implemented; production not run | local normalization tests pass |
| Native VOD XML | yes | yes | categories and page records preserved | yes as `vod_api` | yes | local read-only projection implemented; production not run | local normalization tests pass |
| TVBox type 0 | yes | native HTTP/XML | yes | yes | yes | not production-verified | not production-verified |
| TVBox type 1 | yes | native HTTP/JSON | yes | yes | yes | not production-verified | not production-verified |
| TVBox type 4 | yes | native HTTP/JSON with ext semantics | yes | yes | yes | not production-verified | not production-verified |
| TVBox executable/spider | yes | metadata only | yes | yes, trust-gated | yes while blocked | no execution | intentionally blocked |

## Implemented reviewed change

- Python and Worker native VOD parsers preserve all bounded records/categories,
  JSON/XML format, pagination metadata, playback lines, episode labels, and
  explicit `discovered = accepted + rejected` accounting.
- JSONC comments and trailing commas are supported with string-aware scanners;
  `https://` strings are preserved and malformed JSONC remains an explicit
  `invalid_json` failure.
- TVBox type 0/1/4 remain native transport formats; executable children retain
  `awaiting_user_approval` and are never auto-approved.
- Python and Worker child enumeration uses matching source-array identity rules;
  the reviewed local baseline retains 232 children on both paths and
  `237 = 230 + 7` extraction accounting with no first-child truncation.
- Source-native title/type/episode/playback metadata is kept independently from
  canonical identity metadata.
- The Worker now returns a read-only VOD catalog projection containing the
  source record, identity fingerprint, existing canonical match or proposed
  item, source relationship, playback variants, duplicate candidates, and
  explicit rejected-item reasons. Controlled import persists relationships and
  variants only after that projection path is available.
- Sanitized rolling replay capture remains bounded and credential-redacting;
  raw media bytes are never archived.

## Validation at reviewed commit

- Python full suite: **PASS** (`402 passed`).
- Worker typecheck: **PASS**.
- Worker suite: **PASS** (`39 files / 378 tests`).
- Web typecheck: **PASS**.
- Web suite: **PASS** (`7 files / 80 tests`).
- Web build: **PASS**.
- Web lint: **PASS**; the repository's existing empty ESLint config emits a
  warning but no lint failure.
- Mission-owned Python compile checks: **PASS**.
- `git diff --check` for reviewed commit: **PASS**.
- Full `scripts/` compile: **blocked by unrelated pre-existing syntax error in
  `scripts/mission72_production_merge.py:110`; this is not claimed as a pass and
  was not changed or included in the deployment.
- `gitleaks`, `trufflehog`, and `detect-secrets`: **unavailable**. A bounded
  high-signal repository pattern scan found no match; no unavailable tool is
  claimed as passed.

## Read-only production inputs and pre-acceptance state

- VOD `src-1786206904981-lw6yziv`: `moovie.c2v2.com/api/vod`, HTTP 200 JSON,
  22,181 bytes, detected `maccms` / `maccms` / native / native, 50 records,
  four categories, `page=1`, `page_count=1`, `total=50`, and native extraction
  accounting `1 = 1 accepted + 0 rejected`.
- Multi-child Link `src-1786373894096-i2cf5ra`:
  `cdn.jsdelivr.net/gh/liu673cn/box@main/m.json`, HTTP 200 JSONC, 57,874 bytes,
  detected `tvbox` / `http_json`, runtime `java_jar`, trust
  `awaiting_user_approval`, 232 Python children and 232 Worker children. The
  extractor accepted 230 and rejected seven with `237 = 230 + 7`; remainder
  zero and first-child truncation zero.
- Read-only D1 correlation immediately after deployment showed the selected VOD
  provider authorized as `vod_url` with one existing child link, **zero catalog
  links**, and **zero playback variants**. The selected Link provider was
  authorized as `tvbox_json` with 89 existing child links, zero catalog links,
  and zero playback variants. These are the before-state facts; no import was
  performed by this execution.
- The replay fixture table remained unchanged by this execution:
  21 existing fixtures, zero `add_resource_preview` captures, zero
  `add_resource_import` captures, and zero writes in the D1 correlation query.

## Authenticated production acceptance blocker

`GET /auth/session` in the terminal context returned HTTP 401. The available
browser tooling cannot attach to the user's already-authorized Chrome/Fireball
session, and no cookie, bearer token, password, refresh token, or browser
local-storage credential was exported, persisted, or transferred.

Therefore the following gates remain false and were not attempted against the
new Worker:

- `authenticated_admin_context`
- `production_vod_preview`
- `production_multi_child_preview`
- `catalog_projection_preview`
- `production_add_resource_import`
- `production_origin_fixture_persisted`
- `python_worker_replay_parity` for new production-origin fixtures
- `vod_movie_readback`, `vod_tv_readback`, and `vod_playback_variants`

The normal unauthenticated probes returning 401 are only blocker evidence. They
are not production acceptance evidence.

## Final gates

```json
{
  "reviewed_worker_deployed": true,
  "production_worker_identity_verified": true,
  "authenticated_admin_context": false,
  "production_vod_preview": false,
  "production_multi_child_preview": false,
  "production_add_resource_import": false,
  "production_origin_fixture_persisted": false,
  "python_worker_replay_parity": false,
  "zero_first_source_truncation": true,
  "zero_unexplained_import_accounting": true,
  "catalog_projection_preview": false,
  "vod_movie_readback": false,
  "vod_tv_readback": false,
  "vod_playback_variants": false,
  "source_native_metadata_preserved": true,
  "kodi_runtime_execution_verified": false,
  "media_bytes_verified": false,
  "SOURCE_RUNTIME_PLATFORM": "WITHHOLD_GO"
}
```

No Full Reindex APPLY, bulk runtime-state update, legacy relationship deletion,
broad canonical identity rewrite, executable Kodi canary, or media payload
archival was performed.

## Controlled production sequence still required

Once a legitimate authenticated Admin browser context is available, run the
new Worker preview for both approved sources, require the returned projection
and trust/accounting gates, persist only sanitized replay fixtures, then run the
narrow VOD import and read back Source → Category → Movie/Show → Detail →
CatalogItemSource → PlaybackVariant. Only after that read-back may the VOD
import and production-origin fixture gates be changed to true. The Link import
must remain trust-gated and must not execute executable children. Kodi execution
and bounded media-byte reachability remain independent gates.

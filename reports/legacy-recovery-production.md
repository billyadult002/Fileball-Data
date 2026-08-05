# Legacy recovery production release

- Status: **recovered historical snapshot published**
- Data commit: `7d49b6a97ca26059e945b39d9f7fd0cb118940fe`
- Recovery source: `Fileball-Data@8e9f1c1dcdadffa2b57959cd7e7eb25520c41f64` (historical; not fresh upstream ingestion)
- Worker version: `fcd98edd-9944-44a0-86a2-e491a101d2b2` / semver `1.1.0`
- Pages deployment: `22aadd77-ec17-41c8-b396-8789d5fb6731`
- Contract: `2.1`
- Cache buster: `recovery-20260802-1`

## Published counts

| Category | Canonical API count | Legacy playlist entries |
|---|---:|---:|
| Movies | 51 | 120 |
| TV | 367 | 10,615 |
| Anime | 260 | 21,753 |
| Variety | 120 | 18,017 |
| AV | 2,273 | 2,279 |
| Live | 358 | 358 |

The API returns 100 records on the first page for TV, Anime, and Variety; Movies has 51 validated canonical records. AV remains in its isolated section.

## Verification

- Raw public data URLs returned HTTP 200 and passed JSON/M3U/secret validation before push.
- `v8.hengmao.org` reports the new data commit and contract.
- Cache-busted production API requests returned the recovered counts.
- `media.hengmao.org` serves the new Pages asset.
- Interactive Chrome DevTools/console capture was unavailable, so no claim is made about a live browser console session.

## Rollback

Previous public data commit: `03fc159c2758feb6c55ba6385dd04737484d683d`. Previous Worker deployment retained: `a4417283-2e70-4569-8aa9-ad22f541f018`. Previous Pages deployment retained: `f89e9a66-2b19-4f39-8628-49992a6f8fe5`.

# Legacy recovery selection

- Recovery type: `historical_snapshot_not_fresh_ingestion`
- Selected repository commit: `8e9f1c1dcdadffa2b57959cd7e7eb25520c41f64`
- Provenance: public Fileball-Data Git history (historical snapshot; not fresh Fastone ingestion)
- Fastone endpoint status at recovery time: DNS unavailable

## Selected historical playlists

| Playlist | EXTINF | Unique URLs | Bytes | SHA-256 |
|---|---:|---:|---:|---|
| movies.m3u | 120 | 120 | 54732 | `601d164b7c51892bc40d2a08b25cc1d161ba610c796271e892394d84a22f98bb` |
| tv.m3u | 10615 | 10603 | 4830228 | `4fb5eeb2622a166aea9effadb1bc57cabb3a84eaf3569f0a282597682ae06931` |
| anime.m3u | 21753 | 21749 | 9941919 | `006e3c3ac90a7827f6c6ce6b3349f6b3f49966376c9773de8fb77080b73356b3` |
| variety.m3u | 18017 | 17951 | 8488219 | `a01c93dc86c720ff8e19618a75d38046abf8c450183ad161ebe9ac366d7dd609` |
| latest.m3u | 3000 | 3000 | 1384693 | `cde113f551af63bd3b10ccb46156a2a6273a00c871d0b1ee6759836266f80831` |
| av.m3u | 2279 | 2260 | 1094534 | `a50c166e5eaccfcb00cb989dc962d6fd5a2d6c6d92529f98827b73ea8471da3e` |
| live.m3u | 358 | 358 | 175091 | `b3c6b227ffb71ed41e71246209f8a5f0710928022dde70234bbd3f2988ddd022` |

## Local cache candidates

These files were copied without modifying originals. All ten are zero-filled OneDrive placeholders (non-zero byte count is zero), so they are excluded from normalization and publication.

| File | Apparent bytes | Non-zero content | Decision |
|---|---:|---:|---|
| Adult.m3u | 1412442 | 0 | invalid_zero_filled_placeholder |
| WeberLive 2.m3u | 347918 | 0 | invalid_zero_filled_placeholder |
| WeberLive 4.m3u | 347918 | 0 | invalid_zero_filled_placeholder |
| XXOO-TV.m3u | 720 | 0 | invalid_zero_filled_placeholder |
| 三百多部麻豆.m3u | 77984 | 0 | invalid_zero_filled_placeholder |
| 乌云成人.m3u | 1295951 | 0 | invalid_zero_filled_placeholder |
| 司机合集.m3u | 498718 | 0 | invalid_zero_filled_placeholder |
| 小苹果.m3u | 469926 | 0 | invalid_zero_filled_placeholder |
| 福利源.m3u | 338416 | 0 | invalid_zero_filled_placeholder |
| 超级福利，精品源.m3u | 32660 | 0 | invalid_zero_filled_placeholder |

## Decision

The historical commit is the only validated recovery source. It is suitable for a controlled public-data rollback/forward publication after schema and secret checks. No fresh upstream ingestion is claimed, and no subscription or source file was deleted.

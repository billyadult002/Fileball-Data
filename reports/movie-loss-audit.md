# Movie loss audit

- `fresh_upstream_fetch=false` (legacy DNS is permanently unavailable)
- Recovered snapshot: `Fileball-Data@8e9f1c1dcdadffa2b57959cd7e7eb25520c41f64`

| Stage | Count |
|---|---:|
| Historical EXTINF entries | 120 |
| Unique playback URLs | 120 |
| Unique raw titles | 120 |
| Normalized title keys | 72 |
| Current canonical movies | 51 |
| Duplicate entries merged | 48 |
| Missing title/URL rejected | 0 |

The measured difference is 72 normalized legacy movie keys versus 51 canonical movie cards. 21 keys are absent from the selected catalog JSON snapshot; none were rejected for missing poster, year, overview, or multiple providers.

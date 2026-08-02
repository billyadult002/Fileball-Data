# Mission 9 baseline

The baseline separates source records, canonical media, detail files, playlist entries, and streams. The production values are recorded only where observed; local snapshot values are not presented as production proof.

| Measure | Value |
|---|---:|
| Local canonical movies | 103 |
| Local movie detail files | 103 |
| Local `movies.m3u` EXTINF entries | 98 |
| Audited source snapshot records | 2,789,546 |
| Audited movie candidates | 501,083 |
| Production Movies API total | 144 |

## Baseline finding

The source snapshots contain hundreds of thousands of movie candidates, while the published canonical movie catalog contains only about one hundred records. The first repair target is source snapshot reconciliation and publication, not a larger Web request limit.

Rollback values are preserved in `mission-9-baseline.json`.

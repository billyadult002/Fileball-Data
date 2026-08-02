# Mission 7.2 production contribution

- mission: 7.3
- generated_at: 2026-08-02T19:54:21Z
- frozen_source_ids: ['gh72-api-360zy', 'gh72-api-dbzy', 'gh72-api-ikun', 'gh72-api-jszy', 'gh72-api-maotai', 'gh72-api-mdzy', 'gh72-api-suoni', 'gh72-api-xingba', 'gh72-api-xxibao', 'gh72-api-zuid', 'gh72-live-baishi', 'gh72-live-scenery']
- raw_records: 897
- canonical_staging_records: 689
- vod_staging_records: 552
- live_staging_records: 137
- new_canonical_media_added: 468
- existing_canonical_media_enriched: 429
- new_episodes_added: 0
- new_streams_added: 3757
- new_live_channels_added: 137
- duplicates_merged: 429
- records_rejected_at_production_merge: -137
- classification: {'Other': 254, 'TV Series': 317, 'Movies': 62, 'Anime': 115, 'AV': 8, 'Documentary': 4}
- live_classification: {'TV channels': 137, 'scenery channels': 0, 'regional channels': 0, 'other live': 0}
- production_catalog_before: 3481
- production_catalog_after: 3812
- rejection_policy_preserved: True
- publication_gate: qualified

- failures: {}

## Source breakdown

| Source | Raw | Normalized | Added | Merged | Streams | Status |
|---|---:|---:|---:|---:|---:|---|
| gh72-api-dbzy | 100 | 100 | 94 | 6 | 49 | healthy |
| gh72-api-xingba | 100 | 100 | 100 | 0 | 0 | healthy |
| gh72-api-suoni | 20 | 20 | 19 | 1 | 0 | healthy |
| gh72-api-ikun | 100 | 100 | 29 | 71 | 773 | healthy |
| gh72-api-jszy | 100 | 100 | 15 | 85 | 286 | healthy |
| gh72-api-zuid | 20 | 20 | 7 | 13 | 17 | healthy |
| gh72-api-360zy | 100 | 100 | 3 | 97 | 593 | healthy |
| gh72-api-maotai | 100 | 100 | 40 | 60 | 1329 | healthy |
| gh72-api-xxibao | 20 | 20 | 20 | 0 | 0 | healthy |
| gh72-api-mdzy | 100 | 100 | 4 | 96 | 573 | healthy |
| gh72-live-baishi | 67 | 67 | 67 | 0 | 67 | healthy |
| gh72-live-scenery | 70 | 70 | 70 | 0 | 70 | healthy |

## Rollback

- Previous public data commit: `977d28a5bc706d767f412d229e06ad83413dcc08`
- Previous Worker version: `1.1.0`
- Previous catalog contract: `2.1`
- Pages deployment: unavailable from configured evidence
- Rollback verified: false (deployment gate blocked)

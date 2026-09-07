# Mission 7.2 production contribution

- mission: 7.3
- generated_at: 2026-09-07T01:25:35Z
- frozen_source_ids: ['addon-catalogs-plus', 'addon-dcbi', 'addon-global-catalogs', 'addon-streaming-catalogs', 'addon-thepiratebay', 'addon-tmdb', 'gh72-api-360zy', 'gh72-api-dbzy', 'gh72-api-ikun', 'gh72-api-jszy', 'gh72-api-maotai', 'gh72-api-mdzy', 'gh72-api-suoni', 'gh72-api-xingba', 'gh72-api-xxibao', 'gh72-api-zuid', 'gh72-live-scenery']
- raw_records: 2868
- canonical_staging_records: 689
- vod_staging_records: 552
- live_staging_records: 137
- new_canonical_media_added: 101
- existing_canonical_media_enriched: 2695
- new_episodes_added: 0
- new_streams_added: 5586
- new_live_channels_added: 0
- duplicates_merged: 2695
- records_rejected_at_production_merge: 2
- classification: {'Other': 358, 'TV Series': 1173, 'Anime': 106, 'AV': 25, 'Movies': 874}
- live_classification: {'TV channels': 0, 'scenery channels': 0, 'regional channels': 0, 'other live': 0}
- failures: {'addon-catalogs-plus': 'RuntimeError: redirect rejected by source allowlist policy'}
- production_catalog_before: 3481
- production_catalog_after: 7562
- rejection_policy_preserved: True
- publication_gate: qualified
- rollback: {'previous_public_data_commit': '977d28a5bc706d767f412d229e06ad83413dcc08', 'previous_worker_version': '1.1.0', 'previous_worker_data_commit': '977d28a5bc706d767f412d229e06ad83413dcc08', 'previous_catalog_contract': '2.1', 'previous_pages_deployment': 'not available from configured GitHub/Cloudflare evidence', 'rollback_verified': False}

## Source breakdown

| Source | Raw | Normalized | Added | Merged | Streams | Status |
|---|---:|---:|---:|---:|---:|---|
| gh72-api-dbzy | 100 | 100 | 0 | 100 | 24 | healthy |
| gh72-api-xingba | 100 | 100 | 20 | 80 | 0 | healthy |
| gh72-api-suoni | 20 | 20 | 0 | 20 | 10 | healthy |
| gh72-api-ikun | 100 | 100 | 0 | 100 | 2101 | healthy |
| gh72-api-jszy | 100 | 100 | 0 | 100 | 336 | healthy |
| gh72-api-zuid | 20 | 20 | 0 | 20 | 16 | healthy |
| gh72-api-360zy | 100 | 100 | 47 | 53 | 1950 | healthy |
| gh72-api-maotai | 100 | 100 | 0 | 100 | 586 | healthy |
| gh72-api-xxibao | 20 | 20 | 0 | 20 | 0 | healthy |
| gh72-api-mdzy | 100 | 100 | 0 | 100 | 563 | healthy |
| gh72-live-scenery | 0 | 0 | 0 | 0 | 0 | healthy |
| addon-streaming-catalogs | 917 | 916 | 25 | 891 | 0 | healthy |
| addon-global-catalogs | 815 | 815 | 3 | 812 | 0 | healthy |
| addon-tmdb | 106 | 106 | 4 | 102 | 0 | healthy |
| addon-thepiratebay | 100 | 99 | 2 | 97 | 0 | healthy |
| addon-dcbi | 100 | 100 | 0 | 100 | 0 | healthy |
| addon-catalogs-plus | 0 | 0 | 0 | 0 | 0 | stale_lkg |

# Mission 7.2 production contribution

- mission: 7.3
- generated_at: 2026-09-06T15:36:35Z
- frozen_source_ids: ['addon-catalogs-plus', 'addon-dcbi', 'addon-global-catalogs', 'addon-streaming-catalogs', 'addon-thepiratebay', 'addon-tmdb', 'gh72-api-360zy', 'gh72-api-dbzy', 'gh72-api-ikun', 'gh72-api-jszy', 'gh72-api-maotai', 'gh72-api-mdzy', 'gh72-api-suoni', 'gh72-api-xingba', 'gh72-api-xxibao', 'gh72-api-zuid', 'gh72-live-scenery']
- raw_records: 2874
- canonical_staging_records: 689
- vod_staging_records: 552
- live_staging_records: 137
- new_canonical_media_added: 1
- existing_canonical_media_enriched: 2802
- new_episodes_added: 0
- new_streams_added: 3865
- new_live_channels_added: 0
- duplicates_merged: 2802
- records_rejected_at_production_merge: 1
- classification: {'Other': 343, 'TV Series': 1213, 'Anime': 100, 'AV': 11, 'Movies': 878}
- live_classification: {'TV channels': 0, 'scenery channels': 0, 'regional channels': 0, 'other live': 0}
- failures: {'addon-catalogs-plus': 'ConnectError: [SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed: certificate has expired (_ssl.c:1010)'}
- production_catalog_before: 3481
- production_catalog_after: 7295
- rejection_policy_preserved: True
- publication_gate: qualified
- rollback: {'previous_public_data_commit': '977d28a5bc706d767f412d229e06ad83413dcc08', 'previous_worker_version': '1.1.0', 'previous_worker_data_commit': '977d28a5bc706d767f412d229e06ad83413dcc08', 'previous_catalog_contract': '2.1', 'previous_pages_deployment': 'not available from configured GitHub/Cloudflare evidence', 'rollback_verified': False}

## Source breakdown

| Source | Raw | Normalized | Added | Merged | Streams | Status |
|---|---:|---:|---:|---:|---:|---|
| gh72-api-dbzy | 100 | 100 | 0 | 100 | 24 | healthy |
| gh72-api-xingba | 100 | 100 | 0 | 100 | 0 | healthy |
| gh72-api-suoni | 20 | 20 | 0 | 20 | 102 | healthy |
| gh72-api-ikun | 100 | 100 | 0 | 100 | 917 | healthy |
| gh72-api-jszy | 100 | 100 | 1 | 99 | 272 | healthy |
| gh72-api-zuid | 20 | 20 | 0 | 20 | 308 | healthy |
| gh72-api-360zy | 100 | 100 | 0 | 100 | 1095 | healthy |
| gh72-api-maotai | 100 | 100 | 0 | 100 | 586 | healthy |
| gh72-api-xxibao | 20 | 20 | 0 | 20 | 0 | healthy |
| gh72-api-mdzy | 100 | 100 | 0 | 100 | 561 | healthy |
| gh72-live-scenery | 0 | 0 | 0 | 0 | 0 | healthy |
| addon-streaming-catalogs | 919 | 919 | 0 | 919 | 0 | healthy |
| addon-global-catalogs | 819 | 819 | 0 | 819 | 0 | healthy |
| addon-tmdb | 106 | 106 | 0 | 106 | 0 | healthy |
| addon-thepiratebay | 100 | 99 | 0 | 99 | 0 | healthy |
| addon-dcbi | 100 | 100 | 0 | 100 | 0 | healthy |
| addon-catalogs-plus | 0 | 0 | 0 | 0 | 0 | stale_lkg |

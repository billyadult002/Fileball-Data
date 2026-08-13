# Mission 7.2 production contribution

- mission: 7.3
- generated_at: 2026-08-13T06:49:55Z
- frozen_source_ids: ['addon-aiostreams', 'addon-archive-org', 'addon-catalogs-plus', 'addon-comet', 'addon-dcbi', 'addon-global-catalogs', 'addon-mediafusion', 'addon-opensubtitles-v3', 'addon-peerflix', 'addon-streaming-catalogs', 'addon-stremio-addons-net', 'addon-thepiratebay', 'addon-tmdb', 'addon-torrentsdb', 'addon-watchhub', 'gh72-api-360zy', 'gh72-api-dbzy', 'gh72-api-ikun', 'gh72-api-jszy', 'gh72-api-maotai', 'gh72-api-mdzy', 'gh72-api-suoni', 'gh72-api-xingba', 'gh72-api-xxibao', 'gh72-api-zuid', 'gh72-live-scenery']
- raw_records: 2889
- canonical_staging_records: 689
- vod_staging_records: 552
- live_staging_records: 137
- new_canonical_media_added: 333
- existing_canonical_media_enriched: 2552
- new_episodes_added: 0
- new_streams_added: 5556
- new_live_channels_added: 67
- duplicates_merged: 2552
- records_rejected_at_production_merge: -66
- classification: {'Other': 166, 'TV Series': 1251, 'Anime': 229, 'Movies': 873, 'Documentary': 4, 'AV': 15}
- live_classification: {'TV channels': 67, 'scenery channels': 0, 'regional channels': 0, 'other live': 0}
- failures: {}
- production_catalog_before: 3481
- production_catalog_after: 5819
- rejection_policy_preserved: True
- publication_gate: qualified
- rollback: {'previous_public_data_commit': '977d28a5bc706d767f412d229e06ad83413dcc08', 'previous_worker_version': '1.1.0', 'previous_worker_data_commit': '977d28a5bc706d767f412d229e06ad83413dcc08', 'previous_catalog_contract': '2.1', 'previous_pages_deployment': 'not available from configured GitHub/Cloudflare evidence', 'rollback_verified': False}

## Source breakdown

| Source | Raw | Normalized | Added | Merged | Streams | Status |
|---|---:|---:|---:|---:|---:|---|
| gh72-api-dbzy | 100 | 100 | 70 | 30 | 114 | healthy |
| gh72-api-xingba | 100 | 100 | 0 | 100 | 0 | healthy |
| gh72-api-suoni | 20 | 20 | 11 | 9 | 152 | healthy |
| gh72-api-ikun | 100 | 100 | 13 | 87 | 1070 | healthy |
| gh72-api-jszy | 100 | 100 | 51 | 49 | 1484 | healthy |
| gh72-api-zuid | 20 | 20 | 3 | 17 | 60 | healthy |
| gh72-api-360zy | 100 | 100 | 29 | 71 | 650 | healthy |
| gh72-api-maotai | 100 | 100 | 23 | 77 | 1508 | healthy |
| gh72-api-xxibao | 20 | 20 | 0 | 20 | 0 | healthy |
| gh72-api-mdzy | 100 | 100 | 20 | 80 | 451 | healthy |
| gh72-live-scenery | 67 | 67 | 67 | 0 | 67 | healthy |
| addon-streaming-catalogs | 925 | 925 | 15 | 910 | 0 | healthy |
| addon-global-catalogs | 825 | 825 | 0 | 825 | 0 | healthy |
| addon-tmdb | 109 | 108 | 1 | 107 | 0 | healthy |
| addon-thepiratebay | 100 | 100 | 12 | 88 | 0 | healthy |
| addon-dcbi | 100 | 100 | 18 | 82 | 0 | healthy |
| addon-catalogs-plus | 0 | 0 | 0 | 0 | 0 | healthy |
| addon-mediafusion | 0 | 0 | 0 | 0 | 0 | healthy |
| addon-watchhub | 0 | 0 | 0 | 0 | 0 | healthy |
| addon-archive-org | 0 | 0 | 0 | 0 | 0 | healthy |
| addon-opensubtitles-v3 | 0 | 0 | 0 | 0 | 0 | healthy |
| addon-peerflix | 0 | 0 | 0 | 0 | 0 | healthy |
| addon-torrentsdb | 0 | 0 | 0 | 0 | 0 | healthy |
| addon-aiostreams | 0 | 0 | 0 | 0 | 0 | healthy |
| addon-comet | 0 | 0 | 0 | 0 | 0 | healthy |
| addon-stremio-addons-net | 0 | 0 | 0 | 0 | 0 | healthy |

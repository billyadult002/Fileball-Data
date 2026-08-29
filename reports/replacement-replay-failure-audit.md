# Source Input Compatibility Audit

Generated: `2026-08-12T00:16:46Z`

Candidate: `working_tree_uncommitted`

Status: **WITHHOLD_GO**

## Corpus classes and denominators

| Corpus | Count | Accuracy denominator | Meaning |
|---|---:|:---:|---|
| Historical metadata | `1000` | No | Provenance/transition reference |
| Historical raw | `0` | No | Historical payload gap |
| Current replacement | `210` | Yes | Current-origin replay only |
| Rolling production | `20` | Yes | New detector-boundary fixtures |

Historical known-format accuracy: **not measurable**. It is never represented as 100%.

## Replacement replay

- Known-format samples: `210`
- Known-format matches: `167`
- Replacement accuracy: `0.7952380952380952`
- Replayable valid known samples: `167`
- Replayable valid accuracy: `1.0`
- Origin-changed/invalid samples excluded from valid denominator: `43`

```json
{
  "origin_changed_or_invalid": {
    "classification": "unverifiable_current_origin",
    "count": 43,
    "sample_ids": [
      "production-import-97f35d52b1950264",
      "production-import-7faa8a9f7bcc8d16",
      "production-import-419fd8f8d9e8c595",
      "production-import-874c93e7c830df1b",
      "production-import-d222b7e36b66f910",
      "production-import-0cda3e00ec0436d4",
      "production-import-e9772a5793840498",
      "production-import-0853c44a30358ae3",
      "production-import-49f5d26d7babdb16",
      "production-import-6a6aa5df0ad74bf0",
      "production-import-f0adbd5ac4f678af",
      "production-import-6276e732a38c2c39",
      "production-import-81e917c28278e5cc",
      "production-import-fd19108c29fa9a67",
      "production-import-d5d55bd0b9ac0845",
      "production-import-52b78c0289c7f1a1",
      "production-import-702d0825fdbe9a32",
      "production-import-c463247bfceb22ac",
      "production-import-13b7ae81275642ee",
      "production-import-dfa7e715943b906e"
    ],
    "signatures": {
      "kodi_addon->unknown:invalid_json": 1,
      "m3u->tvbox_warehouse:none": 1,
      "m3u->unknown:invalid_json": 1,
      "maccms_http_api->http_xml:none": 1,
      "maccms_http_api->unknown:invalid_json": 9,
      "spider->unknown:invalid_json": 1,
      "stremio_manifest->tvbox_warehouse:none": 7,
      "tvbox_config->unknown:invalid_json": 22
    }
  }
}
```

## Rolling collector

```json
{
  "child_accounting_mismatch_count": 0,
  "content_replay_count": 20,
  "known_format_accuracy": 1.0,
  "known_format_pass": 20,
  "known_format_total": 20,
  "latest": "2026-08-12T00:15:19.463Z",
  "native_misclassification": 0,
  "production_samples_present": true,
  "replay_rows": [
    {
      "child_accounting_match": true,
      "child_source_count": 1,
      "content_replay": true,
      "detected_family": "stremio",
      "detected_format": "stremio_child_source",
      "diagnostic_code": "none",
      "expected_child_count": 1,
      "expected_family": "stremio_catalog",
      "known_format": true,
      "known_format_match": true,
      "protocol_type": "stremio_http",
      "runtime_state": "healthy",
      "runtime_type": "native",
      "sample_id": "rolling-7ab5c7808aadfc744ba41998",
      "secret_safe": true,
      "trust_state": "native"
    },
    {
      "child_accounting_match": true,
      "child_source_count": 1,
      "content_replay": true,
      "detected_family": "stremio",
      "detected_format": "stremio_child_source",
      "diagnostic_code": "none",
      "expected_child_count": 1,
      "expected_family": "stremio_catalog",
      "known_format": true,
      "known_format_match": true,
      "protocol_type": "stremio_http",
      "runtime_state": "healthy",
      "runtime_type": "native",
      "sample_id": "rolling-1a24b3d18a421f9354e67ad2",
      "secret_safe": true,
      "trust_state": "native"
    },
    {
      "child_accounting_match": true,
      "child_source_count": 1,
      "content_replay": true,
      "detected_family": "stremio",
      "detected_format": "stremio_child_source",
      "diagnostic_code": "none",
      "expected_child_count": 1,
      "expected_family": "stremio_catalog",
      "known_format": true,
      "known_format_match": true,
      "protocol_type": "stremio_http",
      "runtime_state": "healthy",
      "runtime_type": "native",
      "sample_id": "rolling-0837ffc86dd064d0cce5c49e",
      "secret_safe": true,
      "trust_state": "native"
    },
    {
      "child_accounting_match": true,
      "child_source_count": 1,
      "content_replay": true,
      "detected_family": "stremio",
      "detected_format": "stremio_child_source",
      "diagnostic_code": "none",
      "expected_child_count": 1,
      "expected_family": "stremio_catalog",
      "known_format": true,
      "known_format_match": true,
      "protocol_type": "stremio_http",
      "runtime_state": "healthy",
      "runtime_type": "native",
      "sample_id": "rolling-47630ef2e861b55c04a748a9",
      "secret_safe": true,
      "trust_state": "native"
    },
    {
      "child_accounting_match": true,
      "child_source_count": 1,
      "content_replay": true,
      "detected_family": "stremio",
      "detected_format": "stremio_child_source",
      "diagnostic_code": "none",
      "expected_child_count": 1,
      "expected_family": "stremio_catalog",
      "known_format": true,
      "known_format_match": true,
      "protocol_type": "stremio_http",
      "runtime_state": "healthy",
      "runtime_type": "native",
      "sample_id": "rolling-6997114e790f115d07ac204c",
      "secret_safe": true,
      "trust_state": "native"
    },
    {
      "child_accounting_match": true,
      "child_source_count": 1,
      "content_replay": true,
      "detected_family": "stremio",
      "detected_format": "stremio_child_source",
      "diagnostic_code": "none",
      "expected_child_count": 1,
      "expected_family": "stremio_catalog",
      "known_format": true,
      "known_format_match": true,
      "protocol_type": "stremio_http",
      "runtime_state": "healthy",
      "runtime_type": "native",
      "sample_id": "rolling-398f26c6b501f27f73fe8c8c",
      "secret_safe": true,
      "trust_state": "native"
    },
    {
      "child_accounting_match": true,
      "child_source_count": 1,
      "content_replay": true,
      "detected_family": "stremio",
      "detected_format": "stremio_child_source",
      "diagnostic_code": "none",
      "expected_child_count": 1,
      "expected_family": "stremio_catalog",
      "known_format": true,
      "known_format_match": true,
      "protocol_type": "stremio_http",
      "runtime_state": "healthy",
      "runtime_type": "native",
      "sample_id": "rolling-f2f8029ed845665f19c1e958",
      "secret_safe": true,
      "trust_state": "native"
    },
    {
      "child_accounting_match": true,
      "child_source_count": 1,
      "content_replay": true,
      "detected_family": "stremio",
      "detected_format": "stremio_child_source",
      "diagnostic_code": "none",
      "expected_child_count": 1,
      "expected_family": "stremio_catalog",
      "known_format": true,
      "known_format_match": true,
      "protocol_type": "stremio_http",
      "runtime_state": "healthy",
      "runtime_type": "native",
      "sample_id": "rolling-59d5ff59a499ecc261001a14",
      "secret_safe": true,
      "trust_state": "native"
    },
    {
      "child_accounting_match": true,
      "child_source_count": 1,
      "content_replay": true,
      "detected_family": "stremio",
      "detected_format": "stremio_child_source",
      "diagnostic_code": "none",
      "expected_child_count": 1,
      "expected_family": "stremio_catalog",
      "known_format": true,
      "known_format_match": true,
      "protocol_type": "stremio_http",
      "runtime_state": "healthy",
      "runtime_type": "native",
      "sample_id": "rolling-b664f04cf6acdd5d32461c31",
      "secret_safe": true,
      "trust_state": "native"
    },
    {
      "child_accounting_match": true,
      "child_source_count": 1,
      "content_replay": true,
      "detected_family": "stremio",
      "detected_format": "stremio_child_source",
      "diagnostic_code": "none",
      "expected_child_count": 1,
      "expected_family": "stremio_catalog",
      "known_format": true,
      "known_format_match": true,
      "protocol_type": "stremio_http",
      "runtime_state": "healthy",
      "runtime_type": "native",
      "sample_id": "rolling-4c49e99b218f07986e01a073",
      "secret_safe": true,
      "trust_state": "native"
    },
    {
      "child_accounting_match": true,
      "child_source_count": 1,
      "content_replay": true,
      "detected_family": "stremio",
      "detected_format": "stremio_child_source",
      "diagnostic_code": "none",
      "expected_child_count": 1,
      "expected_family": "stremio_catalog",
      "known_format": true,
      "known_format_match": true,
      "protocol_type": "stremio_http",
      "runtime_state": "healthy",
      "runtime_type": "native",
      "sample_id": "rolling-b6da0be908c224afb62c45e2",
      "secret_safe": true,
      "trust_state": "native"
    },
    {
      "child_accounting_match": true,
      "child_source_count": 1,
      "content_replay": true,
      "detected_family": "stremio",
      "detected_format": "stremio_child_source",
      "diagnostic_code": "none",
      "expected_child_count": 1,
      "expected_family": "stremio_catalog",
      "known_format": true,
      "known_format_match": true,
      "protocol_type": "stremio_http",
      "runtime_state": "healthy",
      "runtime_type": "native",
      "sample_id": "rolling-dd0d23b4b162729e9a6bebf6",
      "secret_safe": true,
      "trust_state": "native"
    },
    {
      "child_accounting_match": true,
      "child_source_count": 1,
      "content_replay": true,
      "detected_family": "stremio",
      "detected_format": "stremio_child_source",
      "diagnostic_code": "none",
      "expected_child_count": 1,
      "expected_family": "stremio_catalog",
      "known_format": true,
      "known_format_match": true,
      "protocol_type": "stremio_http",
      "runtime_state": "healthy",
      "runtime_type": "native",
      "sample_id": "rolling-6e41515e4c11bd9b1e6498c2",
      "secret_safe": true,
      "trust_state": "native"
    },
    {
      "child_accounting_match": true,
      "child_source_count": 1,
      "content_replay": true,
      "detected_family": "stremio",
      "detected_format": "stremio_child_source",
      "diagnostic_code": "none",
      "expected_child_count": 1,
      "expected_family": "stremio_catalog",
      "known_format": true,
      "known_format_match": true,
      "protocol_type": "stremio_http",
      "runtime_state": "healthy",
      "runtime_type": "native",
      "sample_id": "rolling-1b37abb155156f170ee39ff5",
      "secret_safe": true,
      "trust_state": "native"
    },
    {
      "child_accounting_match": true,
      "child_source_count": 1,
      "content_replay": true,
      "detected_family": "stremio",
      "detected_format": "stremio_child_source",
      "diagnostic_code": "none",
      "expected_child_count": 1,
      "expected_family": "stremio_catalog",
      "known_format": true,
      "known_format_match": true,
      "protocol_type": "stremio_http",
      "runtime_state": "healthy",
      "runtime_type": "native",
      "sample_id": "rolling-cb64c6a6dc10251f3e5aab17",
      "secret_safe": true,
      "trust_state": "native"
    },
    {
      "child_accounting_match": true,
      "child_source_count": 1,
      "content_replay": true,
      "detected_family": "stremio",
      "detected_format": "stremio_child_source",
      "diagnostic_code": "none",
      "expected_child_count": 1,
      "expected_family": "stremio_catalog",
      "known_format": true,
      "known_format_match": true,
      "protocol_type": "stremio_http",
      "runtime_state": "healthy",
      "runtime_type": "native",
      "sample_id": "rolling-ebfa042183ec6697205397a8",
      "secret_safe": true,
      "trust_state": "native"
    },
    {
      "child_accounting_match": true,
      "child_source_count": 1,
      "content_replay": true,
      "detected_family": "stremio",
      "detected_format": "stremio_child_source",
      "diagnostic_code": "none",
      "expected_child_count": 1,
      "expected_family": "stremio_catalog",
      "known_format": true,
      "known_format_match": true,
      "protocol_type": "stremio_http",
      "runtime_state": "healthy",
      "runtime_type": "native",
      "sample_id": "rolling-01dbf039aad5ded034497615",
      "secret_safe": true,
      "trust_state": "native"
    },
    {
      "child_accounting_match": true,
      "child_source_count": 1,
      "content_replay": true,
      "detected_family": "stremio",
      "detected_format": "stremio_child_source",
      "diagnostic_code": "none",
      "expected_child_count": 1,
      "expected_family": "stremio_catalog",
      "known_format": true,
      "known_format_match": true,
      "protocol_type": "stremio_http",
      "runtime_state": "healthy",
      "runtime_type": "native",
      "sample_id": "rolling-4405372f6ff5cf9ad25d7bbc",
      "secret_safe": true,
      "trust_state": "native"
    },
    {
      "child_accounting_match": true,
      "child_source_count": 1,
      "content_replay": true,
      "detected_family": "stremio",
      "detected_format": "stremio_child_source",
      "diagnostic_code": "none",
      "expected_child_count": 1,
      "expected_family": "stremio_catalog",
      "known_format": true,
      "known_format_match": true,
      "protocol_type": "stremio_http",
      "runtime_state": "healthy",
      "runtime_type": "native",
      "sample_id": "rolling-77153245d0f7e27e3fdd1c19",
      "secret_safe": true,
      "trust_state": "native"
    },
    {
      "child_accounting_match": true,
      "child_source_count": 1,
      "content_replay": true,
      "detected_family": "stremio",
      "detected_format": "stremio_child_source",
      "diagnostic_code": "none",
      "expected_child_count": 1,
      "expected_family": "stremio_catalog",
      "known_format": true,
      "known_format_match": true,
      "protocol_type": "stremio_http",
      "runtime_state": "healthy",
      "runtime_type": "native",
      "sample_id": "rolling-4ea166fa9627652888509a29",
      "secret_safe": true,
      "trust_state": "native"
    }
  ],
  "rows": [
    {
      "captured_at": "2026-08-12T00:00:08.879Z",
      "expected_family_hint": "stremio_catalog",
      "input_kind": "child_descriptor",
      "origin": "scheduled_provider_refresh",
      "sample_id": "rolling-7ab5c7808aadfc744ba41998"
    },
    {
      "captured_at": "2026-08-12T00:00:09.649Z",
      "expected_family_hint": "stremio_catalog",
      "input_kind": "child_descriptor",
      "origin": "scheduled_provider_refresh",
      "sample_id": "rolling-1a24b3d18a421f9354e67ad2"
    },
    {
      "captured_at": "2026-08-12T00:00:10.415Z",
      "expected_family_hint": "stremio_catalog",
      "input_kind": "child_descriptor",
      "origin": "scheduled_provider_refresh",
      "sample_id": "rolling-0837ffc86dd064d0cce5c49e"
    },
    {
      "captured_at": "2026-08-12T00:00:11.187Z",
      "expected_family_hint": "stremio_catalog",
      "input_kind": "child_descriptor",
      "origin": "scheduled_provider_refresh",
      "sample_id": "rolling-47630ef2e861b55c04a748a9"
    },
    {
      "captured_at": "2026-08-12T00:00:11.955Z",
      "expected_family_hint": "stremio_catalog",
      "input_kind": "child_descriptor",
      "origin": "scheduled_provider_refresh",
      "sample_id": "rolling-6997114e790f115d07ac204c"
    },
    {
      "captured_at": "2026-08-12T00:00:12.718Z",
      "expected_family_hint": "stremio_catalog",
      "input_kind": "child_descriptor",
      "origin": "scheduled_provider_refresh",
      "sample_id": "rolling-398f26c6b501f27f73fe8c8c"
    },
    {
      "captured_at": "2026-08-12T00:00:13.488Z",
      "expected_family_hint": "stremio_catalog",
      "input_kind": "child_descriptor",
      "origin": "scheduled_provider_refresh",
      "sample_id": "rolling-f2f8029ed845665f19c1e958"
    },
    {
      "captured_at": "2026-08-12T00:00:14.254Z",
      "expected_family_hint": "stremio_catalog",
      "input_kind": "child_descriptor",
      "origin": "scheduled_provider_refresh",
      "sample_id": "rolling-59d5ff59a499ecc261001a14"
    },
    {
      "captured_at": "2026-08-12T00:00:15.019Z",
      "expected_family_hint": "stremio_catalog",
      "input_kind": "child_descriptor",
      "origin": "scheduled_provider_refresh",
      "sample_id": "rolling-b664f04cf6acdd5d32461c31"
    },
    {
      "captured_at": "2026-08-12T00:00:15.796Z",
      "expected_family_hint": "stremio_catalog",
      "input_kind": "child_descriptor",
      "origin": "scheduled_provider_refresh",
      "sample_id": "rolling-4c49e99b218f07986e01a073"
    },
    {
      "captured_at": "2026-08-12T00:15:16.039Z",
      "expected_family_hint": "stremio_catalog",
      "input_kind": "child_descriptor",
      "origin": "scheduled_provider_refresh",
      "sample_id": "rolling-b6da0be908c224afb62c45e2"
    },
    {
      "captured_at": "2026-08-12T00:15:16.421Z",
      "expected_family_hint": "stremio_catalog",
      "input_kind": "child_descriptor",
      "origin": "scheduled_provider_refresh",
      "sample_id": "rolling-dd0d23b4b162729e9a6bebf6"
    },
    {
      "captured_at": "2026-08-12T00:15:16.801Z",
      "expected_family_hint": "stremio_catalog",
      "input_kind": "child_descriptor",
      "origin": "scheduled_provider_refresh",
      "sample_id": "rolling-6e41515e4c11bd9b1e6498c2"
    },
    {
      "captured_at": "2026-08-12T00:15:17.180Z",
      "expected_family_hint": "stremio_catalog",
      "input_kind": "child_descriptor",
      "origin": "scheduled_provider_refresh",
      "sample_id": "rolling-1b37abb155156f170ee39ff5"
    },
    {
      "captured_at": "2026-08-12T00:15:17.562Z",
      "expected_family_hint": "stremio_catalog",
      "input_kind": "child_descriptor",
      "origin": "scheduled_provider_refresh",
      "sample_id": "rolling-cb64c6a6dc10251f3e5aab17"
    },
    {
      "captured_at": "2026-08-12T00:15:17.941Z",
      "expected_family_hint": "stremio_catalog",
      "input_kind": "child_descriptor",
      "origin": "scheduled_provider_refresh",
      "sample_id": "rolling-ebfa042183ec6697205397a8"
    },
    {
      "captured_at": "2026-08-12T00:15:18.323Z",
      "expected_family_hint": "stremio_catalog",
      "input_kind": "child_descriptor",
      "origin": "scheduled_provider_refresh",
      "sample_id": "rolling-01dbf039aad5ded034497615"
    },
    {
      "captured_at": "2026-08-12T00:15:18.701Z",
      "expected_family_hint": "stremio_catalog",
      "input_kind": "child_descriptor",
      "origin": "scheduled_provider_refresh",
      "sample_id": "rolling-4405372f6ff5cf9ad25d7bbc"
    },
    {
      "captured_at": "2026-08-12T00:15:19.082Z",
      "expected_family_hint": "stremio_catalog",
      "input_kind": "child_descriptor",
      "origin": "scheduled_provider_refresh",
      "sample_id": "rolling-77153245d0f7e27e3fdd1c19"
    },
    {
      "captured_at": "2026-08-12T00:15:19.463Z",
      "expected_family_hint": "stremio_catalog",
      "input_kind": "child_descriptor",
      "origin": "scheduled_provider_refresh",
      "sample_id": "rolling-4ea166fa9627652888509a29"
    }
  ],
  "sample_count": 20,
  "secret_scan": {
    "fixture_count": 20,
    "leak_count": 0,
    "status": "PASS"
  },
  "silent_link_failure_count": 0,
  "table_available": true
}
```

The collector is wired into Add Resource preview/import and provider child discovery. Raw bytes remain in memory; only sanitized bounded fixtures are eligible for persistence. Production samples remain zero until the additive migration and deployed writer are present.

## Machine gate

```json
{
  "branch": "mission/rolling-production-canary",
  "candidate_state": "working_tree_uncommitted",
  "head_sha_if_any": "3dacd7970d9a18a888d6034f2a754f266f553b74",
  "reason": "Historical raw gap is documented; rolling production fixtures are present and remain subject to replay gates.",
  "rolling_detector_closure": {
    "canonical_identity_drift_guard_pass": true,
    "child_accounting_zero_mismatch": true,
    "commit_level_replay_pass": false,
    "full_reindex_dry_run": true,
    "historical_metadata_corpus_preserved": true,
    "historical_raw_gap_documented": true,
    "kodi_runtime_classification_verified": true,
    "maccms_schema_detection_verified": true,
    "mission_commit_pushed": false,
    "native_runtime_misclassification_zero": true,
    "reindex_unaccounted_zero": false,
    "replacement_corpus_replayed": true,
    "replacement_failures_clustered": true,
    "replayable_valid_known_format_accuracy_100": true,
    "rolling_child_accounting_zero_mismatch": true,
    "rolling_collector_enabled": true,
    "rolling_fixtures_secret_safe": true,
    "rolling_known_format_accuracy_100": true,
    "rolling_native_runtime_misclassification_zero": true,
    "rolling_production_samples_present": true,
    "rolling_silent_link_failures_zero": true,
    "silent_link_failures_zero": true,
    "spider_trust_policy_verified": true,
    "tests": true,
    "tvbox_type0_1_4_verified": false
  },
  "status": "WITHHOLD_GO"
}
```

`SOURCE_RUNTIME_PLATFORM WITHHOLD_GO` remains mandatory. This report does not authorize commit, deployment, reindex APPLY, or historical accuracy claims.

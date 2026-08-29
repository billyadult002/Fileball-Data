# Production Reindex Dry-Run Audit

- Generated: `2026-08-12T00:16:46Z`
- Mode: `current_state_fresh_provider_dry_run`
- Status: **DRY_RUN_WITHHOLD_APPLY_WITHHOLD**
- Writes performed: `False`
- Historical corpus dependency: `False`
- Canary deployment commit: `eb9f99b8a9b5d2e01229f53991a7cde9954a5022`
- Canary deployment version: `848ff9cd-5705-4751-bdfe-1854067efe7c`
- Migration 0020 schema verified: `True`

## Current evidence

- Providers sampled: `145`
- Current fetches: `121`
- Explicit provider errors: `94`
- Discovered children: `3920`
- Persisted provider links: `11670`
- Unaccounted children: `822`
- Canonical sources: `4386`
- Playback variants: `0`
- Unaccounted children: `822` (`runtime_blocked: 822`; all provider-provenanced)
- Unexplained unaccounted: `0`
- Runtime mismatch providers: `77`
- Runtime mismatch children: `9984`

## Accounting classification

Current-state unaccounted children are classified separately from all persisted relation states:

```json
{
  "runtime_blocked": 822
}
```

Each classified unaccounted count carries provider provenance in `unaccounted_provenance`. Historical/stale/unreachable relation states are retained in `relation_state_counts` and are not silently deleted.

## Hard gates

```json
{
  "all_inputs_recognized_or_explicit_error": true,
  "dry_run_executed": true,
  "duplicate_candidate_growth_zero": true,
  "first_source_truncation_zero": true,
  "native_runtime_unexplained_mismatch_zero": true,
  "native_source_misclassification_zero": true,
  "provider_child_collapse_zero": true,
  "unaccounted_failure_classes_explained": true,
  "unaccounted_zero": false,
  "unexpected_canonical_identity_drift_zero": true,
  "unexplained_unaccounted_zero": true
}
```

## Provider evidence

Every provider row contains sanitized URL shape, detector family/protocol/runtime, child count, persisted link counts, error class, and accounting delta. Raw response bytes and query secrets are not written to this report.

```json
[
  {
    "accounting_classification": {
      "fetch_error": 99
    },
    "canonical_matches": 98,
    "catalog_item_sources": 0,
    "children_discovered": null,
    "current_state": "unverifiable_current_state",
    "declared_type": "tvbox_json",
    "detected_family": null,
    "detected_format": null,
    "errors": [
      {
        "code": "unsupported_protocol",
        "detail": "current provider URL is not HTTP(S)",
        "stage": "fetch"
      }
    ],
    "expected_family_hint": "tvbox_config",
    "identity_drift": null,
    "input_url": "",
    "network_replay": false,
    "new_canonical_candidates": null,
    "playback_variants": 0,
    "protocol_type": null,
    "provider_id": "src-1786403314115-51bgzdi",
    "provider_id_sha256": "5a02a1a6c5b78c88d205cdf1b3e951116459e2ccdef7ee1f8854896a3c7a3fe8",
    "provider_source_links": 99,
    "resolved_url": "",
    "reused_canonical_sources": 98,
    "runtime_mismatch_class": null,
    "runtime_mismatch_count": 0,
    "runtime_mismatch_detail": [],
    "runtime_state": null,
    "runtime_type": null,
    "trust_state": null,
    "unaccounted": null
  },
  {
    "accounting_classification": {
      "runtime_blocked": 13
    },
    "canonical_matches": 13,
    "catalog_item_sources": 0,
    "children_discovered": 26,
    "current_state": "confirmed_current_runtime_blocked",
    "declared_type": "tvbox_json",
    "detected_family": "tvbox",
    "detected_format": "tvbox_config",
    "errors": [
      {
        "code": "runtime_required",
        "stage": "runtime"
      }
    ],
    "expected_family_hint": "tvbox_config",
    "identity_drift": {
      "delta": 13,
      "discovered_children": 26,
      "persisted_links": 13
    },
    "input_url": "http://home.jundie.top/top98.json",
    "network_replay": true,
    "new_canonical_candidates": 13,
    "playback_variants": 0,
    "protocol_type": "http_json",
    "provider_child_collapse": false,
    "provider_id": "src-1786374489641-0qabgjq",
    "provider_id_sha256": "59220966f4921b31f680f3da798d764882c9672d85f87614ecee271df3adf3f7",
    "provider_source_links": 13,
    "resolved_url": "http://home.jundie.top/top98.json",
    "reused_canonical_sources": 13,
    "runtime_mismatch_class": "legacy_persisted_classification",
    "runtime_mismatch_count": 26,
    "runtime_mismatch_detail": [
      {
        "detected": {
          "java_jar": 24,
          "native": 2
        },
        "persisted": {
          "none": 13
        }
      }
    ],
    "runtime_state": "unavailable",
    "runtime_type": "java_jar",
    "trust_state": "awaiting_user_approval",
    "unaccounted": 13
  },
  {
    "accounting_classification": {
      "runtime_blocked": 8
    },
    "canonical_matches": 43,
    "catalog_item_sources": 0,
    "children_discovered": 51,
    "current_state": "confirmed_current_runtime_blocked",
    "declared_type": "tvbox_json",
    "detected_family": "tvbox",
    "detected_format": "tvbox_config",
    "errors": [
      {
        "code": "runtime_required",
        "stage": "runtime"
      }
    ],
    "expected_family_hint": "tvbox_config",
    "identity_drift": {
      "delta": 8,
      "discovered_children": 51,
      "persisted_links": 43
    },
    "input_url": "https://dxawi.github.io/0/0.json",
    "network_replay": true,
    "new_canonical_candidates": 8,
    "playback_variants": 0,
    "protocol_type": "http_json",
    "provider_child_collapse": false,
    "provider_id": "src-1786374405708-0e5vpxx",
    "provider_id_sha256": "8fcac49f99c2f3dd8abfc574fea7502df9665aeab3d30075b96d6246f519ea4a",
    "provider_source_links": 43,
    "resolved_url": "https://dxawi.github.io/0/0.json",
    "reused_canonical_sources": 43,
    "runtime_mismatch_class": "legacy_persisted_classification",
    "runtime_mismatch_count": 51,
    "runtime_mismatch_detail": [
      {
        "detected": {
          "java_jar": 44,
          "native": 7
        },
        "persisted": {
          "none": 43
        }
      }
    ],
    "runtime_state": "unavailable",
    "runtime_type": "java_jar",
    "trust_state": "awaiting_user_approval",
    "unaccounted": 8
  },
  {
    "accounting_classification": {
      "origin_changed": 89
    },
    "canonical_matches": 89,
    "catalog_item_sources": 0,
    "children_discovered": 0,
    "current_state": "superseded",
    "declared_type": "tvbox_json",
    "detected_family": "unknown",
    "detected_format": "unknown",
    "errors": [
      {
        "code": "invalid_json",
        "stage": "schema"
      }
    ],
    "expected_family_hint": "tvbox_config",
    "identity_drift": {
      "delta": -89,
      "discovered_children": 0,
      "persisted_links": 89
    },
    "input_url": "https://raw.liucn.cc/box/m.json",
    "network_replay": true,
    "new_canonical_candidates": 0,
    "playback_variants": 0,
    "protocol_type": "unknown",
    "provider_child_collapse": true,
    "provider_child_collapse_reason": "origin_changed_or_unreachable",
    "provider_id": "src-1786374363717-eovda76",
    "provider_id_sha256": "97f35d52b195026417144be82610236ee3c743b5904901c0ce65289fc410b337",
    "provider_source_links": 89,
    "resolved_url": "https://raw.liucn.cc/box/m.json",
    "reused_canonical_sources": 0,
    "runtime_mismatch_class": null,
    "runtime_mismatch_count": 0,
    "runtime_mismatch_detail": [],
    "runtime_state": "error",
    "runtime_type": "none",
    "trust_state": "native",
    "unaccounted": 0
  },
  {
    "accounting_classification": {
      "runtime_blocked": 13
    },
    "canonical_matches": 13,
    "catalog_item_sources": 0,
    "children_discovered": 26,
    "current_state": "confirmed_current_runtime_blocked",
    "declared_type": "tvbox_json",
    "detected_family": "tvbox",
    "detected_format": "tvbox_config",
    "errors": [
      {
        "code": "runtime_required",
        "stage": "runtime"
      }
    ],
    "expected_family_hint": "tvbox_config",
    "identity_drift": {
      "delta": 13,
      "discovered_children": 26,
      "persisted_links": 13
    },
    "input_url": "http://home.jundie.top/top98.json",
    "network_replay": true,
    "new_canonical_candidates": 13,
    "playback_variants": 0,
    "protocol_type": "http_json",
    "provider_child_collapse": false,
    "provider_id": "src-1786374277716-p0tim51",
    "provider_id_sha256": "907596029aae0c2a67ab3b683bbce5643117661bdb73e45b22404bc60d39a846",
    "provider_source_links": 13,
    "resolved_url": "http://home.jundie.top/top98.json",
    "reused_canonical_sources": 13,
    "runtime_mismatch_class": "legacy_persisted_classification",
    "runtime_mismatch_count": 26,
    "runtime_mismatch_detail": [
      {
        "detected": {
          "java_jar": 24,
          "native": 2
        },
        "persisted": {
          "none": 13
        }
      }
    ],
    "runtime_state": "unavailable",
    "runtime_type": "java_jar",
    "trust_state": "awaiting_user_approval",
    "unaccounted": 13
  },
  {
    "accounting_classification": {
      "runtime_blocked": 51
    },
    "canonical_matches": 56,
    "catalog_item_sources": 0,
    "children_discovered": 107,
    "current_state": "confirmed_current_runtime_blocked",
    "declared_type": "tvbox_json",
    "detected_family": "tvbox",
    "detected_format": "tvbox_config",
    "errors": [
      {
        "code": "runtime_required",
        "stage": "runtime"
      }
    ],
    "expected_family_hint": "tvbox_config",
    "identity_drift": {
      "delta": 51,
      "discovered_children": 107,
      "persisted_links": 56
    },
    "input_url": "http://550.3vcn.work/wdjyys.json",
    "network_replay": true,
    "new_canonical_candidates": 51,
    "playback_variants": 0,
    "protocol_type": "http_json",
    "provider_child_collapse": false,
    "provider_id": "src-1786374126826-e2d4ad5",
    "provider_id_sha256": "66ed0743cf8afecc2c966b9140a949b1733ec967630295f7927482db6b39818f",
    "provider_source_links": 56,
    "resolved_url": "http://550.3vcn.work/wdjyys.json",
    "reused_canonical_sources": 56,
    "runtime_mismatch_class": "legacy_persisted_classification",
    "runtime_mismatch_count": 107,
    "runtime_mismatch_detail": [
      {
        "detected": {
          "java_jar": 87,
          "native": 20
        },
        "persisted": {
          "none": 56
        }
      }
    ],
    "runtime_state": "unavailable",
    "runtime_type": "java_jar",
    "trust_state": "awaiting_user_approval",
    "unaccounted": 51
  },
  {
    "accounting_classification": {
      "runtime_blocked": 67
    },
    "canonical_matches": 102,
    "catalog_item_sources": 0,
    "children_discovered": 170,
    "current_state": "confirmed_current_runtime_blocked",
    "declared_type": "tvbox_json",
    "detected_family": "tvbox",
    "detected_format": "tvbox_config",
    "errors": [
      {
        "code": "runtime_required",
        "stage": "runtime"
      }
    ],
    "expected_family_hint": "tvbox_config",
    "identity_drift": {
      "delta": 67,
      "discovered_children": 170,
      "persisted_links": 103
    },
    "input_url": "https://g.33445500.xyz/https://raw.githubusercontent.com/qist/tvbox/refs/heads/master/jsm.json",
    "network_replay": true,
    "new_canonical_candidates": 68,
    "playback_variants": 0,
    "protocol_type": "http_json",
    "provider_child_collapse": false,
    "provider_id": "src-1786374045767-fhen5yd",
    "provider_id_sha256": "4fe8752df9314c03edd08da99da69fc6b079194a62f5ad0f68c34c8926a7b239",
    "provider_source_links": 103,
    "resolved_url": "https://g.33445500.xyz/https://raw.githubusercontent.com/qist/tvbox/refs/heads/master/jsm.json",
    "reused_canonical_sources": 102,
    "runtime_mismatch_class": "legacy_persisted_classification",
    "runtime_mismatch_count": 170,
    "runtime_mismatch_detail": [
      {
        "detected": {
          "java_jar": 152,
          "native": 18
        },
        "persisted": {
          "none": 103
        }
      }
    ],
    "runtime_state": "unavailable",
    "runtime_type": "java_jar",
    "trust_state": "awaiting_user_approval",
    "unaccounted": 67
  },
  {
    "accounting_classification": {
      "current_origin_unreachable": 72
    },
    "canonical_matches": 72,
    "catalog_item_sources": 0,
    "children_discovered": null,
    "current_state": "temporarily_unreachable",
    "declared_type": "tvbox_json",
    "detected_family": null,
    "detected_format": null,
    "errors": [
      {
        "code": "dns_or_connect_error",
        "http_status": null,
        "redirect_count": 1,
        "stage": "fetch"
      }
    ],
    "expected_family_hint": "tvbox_config",
    "identity_drift": null,
    "input_url": "https://6800.kstore.vip/fish.json",
    "network_replay": false,
    "new_canonical_candidates": null,
    "playback_variants": 0,
    "protocol_type": null,
    "provider_id": "src-1786373937447-y9n9178",
    "provider_id_sha256": "60067ec1f326125444c0c7b36178fae2700c3d117a3b20d4c22efe60b0e2a94e",
    "provider_source_links": 72,
    "resolved_url": "",
    "reused_canonical_sources": 72,
    "runtime_mismatch_class": null,
    "runtime_mismatch_count": 0,
    "runtime_mismatch_detail": [],
    "runtime_state": null,
    "runtime_type": null,
    "trust_state": null,
    "unaccounted": null
  },
  {
    "accounting_classification": {
      "origin_changed": 89
    },
    "canonical_matches": 89,
    "catalog_item_sources": 0,
    "children_discovered": 0,
    "current_state": "superseded",
    "declared_type": "tvbox_json",
    "detected_family": "unknown",
    "detected_format": "unknown",
    "errors": [
      {
        "code": "invalid_json",
        "stage": "schema"
      }
    ],
    "expected_family_hint": "tvbox_config",
    "identity_drift": {
      "delta": -89,
      "discovered_children": 0,
      "persisted_links": 89
    },
    "input_url": "https://cdn.jsdelivr.net/gh/liu673cn/box@main/m.json",
    "network_replay": true,
    "new_canonical_candidates": 0,
    "playback_variants": 0,
    "protocol_type": "unknown",
    "provider_child_collapse": true,
    "provider_child_collapse_reason": "origin_changed_or_unreachable",
    "provider_id": "src-1786373894096-i2cf5ra",
    "provider_id_sha256": "7faa8a9f7bcc8d1612c7aebab2602649915460c7be95ed2d4331ba76c6ee2e9f",
    "provider_source_links": 89,
    "resolved_url": "https://cdn.jsdelivr.net/gh/liu673cn/box@main/m.json",
    "reused_canonical_sources": 0,
    "runtime_mismatch_class": null,
    "runtime_mismatch_count": 0,
    "runtime_mismatch_detail": [],
    "runtime_state": "error",
    "runtime_type": "none",
    "trust_state": "native",
    "unaccounted": 0
  },
  {
    "accounting_classification": {
      "origin_changed": 89
    },
    "canonical_matches": 89,
    "catalog_item_sources": 0,
    "children_discovered": 0,
    "current_state": "superseded",
    "declared_type": "tvbox_json",
    "detected_family": "unknown",
    "detected_format": "unknown",
    "errors": [
      {
        "code": "invalid_json",
        "stage": "schema"
      }
    ],
    "expected_family_hint": "tvbox_config",
    "identity_drift": {
      "delta": -89,
      "discovered_children": 0,
      "persisted_links": 89
    },
    "input_url": "https://raw.liucn.cc/box/m.json",
    "network_replay": true,
    "new_canonical_candidates": 0,
    "playback_variants": 0,
    "protocol_type": "unknown",
    "provider_child_collapse": true,
    "provider_child_collapse_reason": "origin_changed_or_unreachable",
    "provider_id": "src-1786373823954-x5rfs5k",
    "provider_id_sha256": "419fd8f8d9e8c5955f6677c50fc80f1ccbd935a9ded0b1149188e92b9f050f73",
    "provider_source_links": 89,
    "resolved_url": "https://raw.liucn.cc/box/m.json",
    "reused_canonical_sources": 0,
    "runtime_mismatch_class": null,
    "runtime_mismatch_count": 0,
    "runtime_mismatch_detail": [],
    "runtime_state": "error",
    "runtime_type": "none",
    "trust_state": "native",
    "unaccounted": 0
  },
  {
    "accounting_classification": {
      "runtime_blocked": 8
    },
    "canonical_matches": 82,
    "catalog_item_sources": 0,
    "children_discovered": 90,
    "current_state": "confirmed_current_runtime_blocked",
    "declared_type": "tvbox_json",
    "detected_family": "tvbox",
    "detected_format": "tvbox_config",
    "errors": [
      {
        "code": "runtime_required",
        "stage": "runtime"
      }
    ],
    "expected_family_hint": "tvbox_config",
    "identity_drift": {
      "delta": 8,
      "discovered_children": 90,
      "persisted_links": 82
    },
    "input_url": "https://9280.kstore.space/newwex.json",
    "network_replay": true,
    "new_canonical_candidates": 8,
    "playback_variants": 0,
    "protocol_type": "http_json",
    "provider_child_collapse": false,
    "provider_id": "src-1786373777277-zkym2j7",
    "provider_id_sha256": "928cbb7f5d04e0d39bc0bf347ef34424b302224c1c1a4457e1bc33fb0b8deab4",
    "provider_source_links": 82,
    "resolved_url": "https://9280.kstore.space/newwex.json",
    "reused_canonical_sources": 82,
    "runtime_mismatch_class": "legacy_persisted_classification",
    "runtime_mismatch_count": 90,
    "runtime_mismatch_detail": [
      {
        "detected": {
          "java_jar": 88,
          "native": 2
        },
        "persisted": {
          "none": 82
        }
      }
    ],
    "runtime_state": "unavailable",
    "runtime_type": "java_jar",
    "trust_state": "awaiting_user_approval",
    "unaccounted": 8
  },
  {
    "accounting_classification": {
      "runtime_blocked": 41
    },
    "canonical_matches": 84,
    "catalog_item_sources": 0,
    "children_discovered": 125,
    "current_state": "confirmed_current_runtime_blocked",
    "declared_type": "tvbox_json",
    "detected_family": "tvbox",
    "detected_format": "tvbox_config",
    "errors": [
      {
        "code": "runtime_required",
        "stage": "runtime"
      }
    ],
    "expected_family_hint": "tvbox_config",
    "identity_drift": {
      "delta": 41,
      "discovered_children": 125,
      "persisted_links": 84
    },
    "input_url": "https://qist.wyfc.qzz.io/xiaosa/api.json",
    "network_replay": true,
    "new_canonical_candidates": 41,
    "playback_variants": 0,
    "protocol_type": "http_json",
    "provider_child_collapse": false,
    "provider_id": "src-1786373726796-mxlw644",
    "provider_id_sha256": "5ddab2418ca8a0751efd6af94bc3f2e2927a2ace83712943df8a31dcc217d6db",
    "provider_source_links": 84,
    "resolved_url": "https://qist.wyfc.qzz.io/xiaosa/api.json",
    "reused_canonical_sources": 84,
    "runtime_mismatch_class": "legacy_persisted_classification",
    "runtime_mismatch_count": 125,
    "runtime_mismatch_detail": [
      {
        "detected": {
          "java_jar": 124,
          "native": 1
        },
        "persisted": {
          "none": 84
        }
      }
    ],
    "runtime_state": "unavailable",
    "runtime_type": "java_jar",
    "trust_state": "awaiting_user_approval",
    "unaccounted": 41
  },
  {
    "accounting_classification": {
      "runtime_blocked": 41
    },
    "canonical_matches": 84,
    "catalog_item_sources": 0,
    "children_discovered": 125,
    "current_state": "confirmed_current_runtime_blocked",
    "declared_type": "tvbox_json",
    "detected_family": "tvbox",
    "detected_format": "tvbox_config",
    "errors": [
      {
        "code": "runtime_required",
        "stage": "runtime"
      }
    ],
    "expected_family_hint": "tvbox_config",
    "identity_drift": {
      "delta": 41,
      "discovered_children": 125,
      "persisted_links": 84
    },
    "input_url": "https://qist.wyfc.qzz.io/xiaosa/api.json",
    "network_replay": true,
    "new_canonical_candidates": 41,
    "playback_variants": 0,
    "protocol_type": "http_json",
    "provider_child_collapse": false,
    "provider_id": "src-1786373725796-iskrg35",
    "provider_id_sha256": "bce5b95109b1da293f6f4b9bb88a9a4aac0dac5875dd7bb6fbde11f5292dee10",
    "provider_source_links": 84,
    "resolved_url": "https://qist.wyfc.qzz.io/xiaosa/api.json",
    "reused_canonical_sources": 84,
    "runtime_mismatch_class": "legacy_persisted_classification",
    "runtime_mismatch_count": 125,
    "runtime_mismatch_detail": [
      {
        "detected": {
          "java_jar": 124,
          "native": 1
        },
        "persisted": {
          "none": 84
        }
      }
    ],
    "runtime_state": "unavailable",
    "runtime_type": "java_jar",
    "trust_state": "awaiting_user_approval",
    "unaccounted": 41
  },
  {
    "accounting_classification": {
      "current_origin_unreachable": 84
    },
    "canonical_matches": 84,
    "catalog_item_sources": 0,
    "children_discovered": null,
    "current_state": "temporarily_unreachable",
    "declared_type": "tvbox_json",
    "detected_family": null,
    "detected_format": null,
    "errors": [
      {
        "code": "dns_or_connect_error",
        "http_status": null,
        "redirect_count": 1,
        "stage": "fetch"
      }
    ],
    "expected_family_hint": "tvbox_config",
    "identity_drift": null,
    "input_url": "https://9280.kstore.vip/aiwex.json",
    "network_replay": false,
    "new_canonical_candidates": null,
    "playback_variants": 0,
    "protocol_type": null,
    "provider_id": "src-1786373692265-wbaymw2",
    "provider_id_sha256": "b2c1532e8e2929e3f28bf591047880740b427c9d8a23af8c408dc2c0593e76b3",
    "provider_source_links": 84,
    "resolved_url": "",
    "reused_canonical_sources": 84,
    "runtime_mismatch_class": null,
    "runtime_mismatch_count": 0,
    "runtime_mismatch_detail": [],
    "runtime_state": null,
    "runtime_type": null,
    "trust_state": null,
    "unaccounted": null
  },
  {
    "accounting_classification": {
      "runtime_blocked": 13
    },
    "canonical_matches": 13,
    "catalog_item_sources": 0,
    "children_discovered": 26,
    "current_state": "confirmed_current_runtime_blocked",
    "declared_type": "tvbox_json",
    "detected_family": "tvbox",
    "detected_format": "tvbox_config",
    "errors": [
      {
        "code": "runtime_required",
        "stage": "runtime"
      }
    ],
    "expected_family_hint": "tvbox_config",
    "identity_drift": {
      "delta": 13,
      "discovered_children": 26,
      "persisted_links": 13
    },
    "input_url": "http://home.jundie.top/top98.json",
    "network_replay": true,
    "new_canonical_candidates": 13,
    "playback_variants": 0,
    "protocol_type": "http_json",
    "provider_child_collapse": false,
    "provider_id": "src-1786373558520-un2phoz",
    "provider_id_sha256": "198aba9545db2c45bb61d0df5245a3c2361c5dd997192e5f4c31a33b67af30ca",
    "provider_source_links": 13,
    "resolved_url": "http://home.jundie.top/top98.json",
    "reused_canonical_sources": 13,
    "runtime_mismatch_class": "legacy_persisted_classification",
    "runtime_mismatch_count": 26,
    "runtime_mismatch_detail": [
      {
        "detected": {
          "java_jar": 24,
          "native": 2
        },
        "persisted": {
          "none": 13
        }
      }
    ],
    "runtime_state": "unavailable",
    "runtime_type": "java_jar",
    "trust_state": "awaiting_user_approval",
    "unaccounted": 13
  },
  {
    "accounting_classification": {
      "confirmed_current": 1
    },
    "canonical_matches": 1,
    "catalog_item_sources": 0,
    "children_discovered": 1,
    "current_state": "confirmed_current",
    "declared_type": "tvbox_m3u",
    "detected_family": "live",
    "detected_format": "m3u",
    "errors": [],
    "expected_family_hint": "m3u",
    "identity_drift": {
      "delta": 0,
      "discovered_children": 1,
      "persisted_links": 1
    },
    "input_url": "https://raw.githubusercontent.com/Free-TV/IPTV/master/playlist.m3u8",
    "network_replay": true,
    "new_canonical_candidates": 0,
    "playback_variants": 0,
    "protocol_type": "m3u",
    "provider_child_collapse": false,
    "provider_id": "src-1786312047088-f8ffh8s",
    "provider_id_sha256": "05e96fd9957d2a18c6456436d2d4a2b08b66ffb7e108dfb302710e4d25065201",
    "provider_source_links": 1,
    "resolved_url": "https://raw.githubusercontent.com/Free-TV/IPTV/master/playlist.m3u8",
    "reused_canonical_sources": 1,
    "runtime_mismatch_class": "legacy_persisted_classification",
    "runtime_mismatch_count": 1,
    "runtime_mismatch_detail": [
      {
        "detected": {
          "native": 1
        },
        "persisted": {
          "none": 1
        }
      }
    ],
    "runtime_state": "healthy",
    "runtime_type": "native",
    "trust_state": "native",
    "unaccounted": 0
  },
  {
    "accounting_classification": {
      "confirmed_current": 1
    },
    "canonical_matches": 1,
    "catalog_item_sources": 0,
    "children_discovered": 1,
    "current_state": "confirmed_current",
    "declared_type": "tvbox_m3u",
    "detected_family": "live",
    "detected_format": "m3u",
    "errors": [],
    "expected_family_hint": "m3u",
    "identity_drift": {
      "delta": 0,
      "discovered_children": 1,
      "persisted_links": 1
    },
    "input_url": "https://epg.pw/test_channels_singapore.m3u",
    "network_replay": true,
    "new_canonical_candidates": 0,
    "playback_variants": 0,
    "protocol_type": "m3u",
    "provider_child_collapse": false,
    "provider_id": "src-1786312028206-7outxo6",
    "provider_id_sha256": "f7036c9aa6947e63059854c1c833969a138d0f05adb8336d76fc39c58a778447",
    "provider_source_links": 1,
    "resolved_url": "https://epg.pw/test_channels_singapore.m3u",
    "reused_canonical_sources": 1,
    "runtime_mismatch_class": "legacy_persisted_classification",
    "runtime_mismatch_count": 1,
    "runtime_mismatch_detail": [
      {
        "detected": {
          "native": 1
        },
        "persisted": {
          "none": 1
        }
      }
    ],
    "runtime_state": "healthy",
    "runtime_type": "native",
    "trust_state": "native",
    "unaccounted": 0
  },
  {
    "accounting_classification": {
      "confirmed_current": 1
    },
    "canonical_matches": 1,
    "catalog_item_sources": 0,
    "children_discovered": 1,
    "current_state": "confirmed_current",
    "declared_type": "tvbox_m3u",
    "detected_family": "live",
    "detected_format": "m3u",
    "errors": [],
    "expected_family_hint": "m3u",
    "identity_drift": {
      "delta": 0,
      "discovered_children": 1,
      "persisted_links": 1
    },
    "input_url": "https://epg.pw/test_channels_taiwan.m3u",
    "network_replay": true,
    "new_canonical_candidates": 0,
    "playback_variants": 0,
    "protocol_type": "m3u",
    "provider_child_collapse": false,
    "provider_id": "src-1786312016355-gt7m149",
    "provider_id_sha256": "13a3dabb37f69f839341d6940c32b8a49f4dead1f9f42d81bbe4e3f3b90e0746",
    "provider_source_links": 1,
    "resolved_url": "https://epg.pw/test_channels_taiwan.m3u",
    "reused_canonical_sources": 1,
    "runtime_mismatch_class": "legacy_persisted_classification",
    "runtime_mismatch_count": 1,
    "runtime_mismatch_detail": [
      {
        "detected": {
          "native": 1
        },
        "persisted": {
          "none": 1
        }
      }
    ],
    "runtime_state": "healthy",
    "runtime_type": "native",
    "trust_state": "native",
    "unaccounted": 0
  },
  {
    "accounting_classification": {
      "confirmed_current": 1
    },
    "canonical_matches": 1,
    "catalog_item_sources": 0,
    "children_discovered": 1,
    "current_state": "confirmed_current",
    "declared_type": "tvbox_m3u",
    "detected_family": "live",
    "detected_format": "m3u",
    "errors": [],
    "expected_family_hint": "m3u",
    "identity_drift": {
      "delta": 0,
      "discovered_children": 1,
      "persisted_links": 1
    },
    "input_url": "https://iptv-org.github.io/iptv/index.m3u",
    "network_replay": true,
    "new_canonical_candidates": 0,
    "playback_variants": 0,
    "protocol_type": "m3u",
    "provider_child_collapse": false,
    "provider_id": "src-1786311983400-nuy7a61",
    "provider_id_sha256": "8fdc1c65a0205297c00ae5dd8b76af0bbd67343be4c2627538bc57f56685ea5d",
    "provider_source_links": 1,
    "resolved_url": "https://iptv-org.github.io/iptv/index.m3u",
    "reused_canonical_sources": 1,
    "runtime_mismatch_class": "legacy_persisted_classification",
    "runtime_mismatch_count": 1,
    "runtime_mismatch_detail": [
      {
        "detected": {
          "native": 1
        },
        "persisted": {
          "none": 1
        }
      }
    ],
    "runtime_state": "healthy",
    "runtime_type": "native",
    "trust_state": "native",
    "unaccounted": 0
  },
  {
    "accounting_classification": {
      "confirmed_current": 47
    },
    "canonical_matches": 47,
    "catalog_item_sources": 0,
    "children_discovered": 47,
    "current_state": "confirmed_current",
    "declared_type": "tvbox_json",
    "detected_family": "tvbox",
    "detected_format": "tvbox_config",
    "errors": [
      {
        "code": "runtime_required",
        "stage": "runtime"
      }
    ],
    "expected_family_hint": "tvbox_config",
    "identity_drift": {
      "delta": 0,
      "discovered_children": 47,
      "persisted_links": 47
    },
    "input_url": "https://android.lushunming.qzz.io/json/index.json",
    "network_replay": true,
    "new_canonical_candidates": 0,
    "playback_variants": 0,
    "protocol_type": "http_json",
    "provider_child_collapse": false,
    "provider_id": "src-1786311847101-cnp753h",
    "provider_id_sha256": "0ac78e4547e4ae8ef0e25fecb20d4953b74f788490c9eb4092c0402bce21ec56",
    "provider_source_links": 47,
    "resolved_url": "https://android.lushunming.qzz.io/json/index.json",
    "reused_canonical_sources": 47,
    "runtime_mismatch_class": "legacy_persisted_classification",
    "runtime_mismatch_count": 47,
    "runtime_mismatch_detail": [
      {
        "detected": {
          "java_jar": 43,
          "native": 4
        },
        "persisted": {
          "none": 47
        }
      }
    ],
    "runtime_state": "unavailable",
    "runtime_type": "java_jar",
    "trust_state": "awaiting_user_approval",
    "unaccounted": 0
  }
]
```

`DRY_RUN_APPLY_WITHHOLD` remains in force. This report does not authorize production writes.

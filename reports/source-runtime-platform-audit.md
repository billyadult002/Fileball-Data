# Source Runtime Platform audit

Generated: `2026-08-11T11:20:00Z`

## Status

**SOURCE_RUNTIME_PLATFORM WITHHOLD_GO**

The offline v1 contract slice is implemented and tested, but production corpus coverage, runtime execution canaries, full reindex, playback byte checks, multi-source completeness, and title audits remain unverified. The machine gate is therefore not overridable and remains false.

## Offline detector

- Fixtures scanned: `6`
- Recognized schemas: `5`
- Unknown JSON: `1` (diagnosed, not mislabeled as unsupported runtime)
- Children accounted: `4`
- Diagnostics complete: `True`

## Implemented contract slice

- Universal input descriptor and machine-readable diagnostics
- Native versus executable runtime/trust dimensions
- Source Runtime ABI v1 capability contract
- PlaybackVariant and PlaybackInstruction metadata preservation
- Four-level fallback attempt accounting and playback error taxonomy
- M3U headers, referer/origin, cookies, DRM, EPG fields and multiple URLs
- Additive runtime approval, regional health-event and playback-attempt schema

## Evidence collected since the offline slice

- Dedicated Oracle runner job `31484268741` completed PASS on `github-runner` at commit `f40bead8f0420f4263d7ea53a672df92c2f6f410`.
- Authenticated read-only baseline: `145` providers, `11,670` provider-source links, `4,386` canonical sources, `100,354` catalog items, and `518,597` catalog-item source links.
- Production corpus: `1,000` real de-identified fixtures, `0` synthetic fixtures. Raw payload replay remains incomplete, so known-format and silent-link gates stay withheld.
- Additive production migrations `0017`–`0019` were applied successfully; `playback_variants`, `source_runtime_jobs`, `source_diagnostics`, and `source_runtime_approvals` now exist in production.
- Worker deployment `54ed031f-aa84-427e-a2f9-ee5ed7155609` was verified through the public health endpoint.
- Provider/link dry-run accounting passed with `11,670` discovered, `11,670` accounted, and `unaccounted=0`; APPLY and second-run idempotency have not run.

## Remaining hard evidence

A production admin-authenticated additive reindex APPLY, second-run duplicate-growth proof, source/API/UI checks, real media-byte playback checks, runtime sandbox executions, multi-source/variant/title audits, and a successful self-hosted security scan are still required before this gate can become PASS.

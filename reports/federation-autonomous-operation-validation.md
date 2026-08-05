# Federation durability and autonomous-operation validation

Status: `VERIFIED_AUTONOMOUS_OPERATION`

## Scope

This change adds a durable per-cycle evidence ledger, bounded convergence
verification, failure classification, a recovery retry policy, and a workflow
operations dashboard. It does not change source approval, catalog contents,
security gates, public API contracts, Worker permissions, DNS, or federation
behavior.

## Implemented controls

- The cycle ledger records initialized, staging, merge, publication, deploy,
  and verification phases with atomic writes and a hash chain.
- Publication verification compares canonical and direct Worker identity,
  public manifest provenance, registry hash, and both health endpoints.
- Propagation failures retry with bounded exponential backoff and terminate
  failed-closed after the retry budget.
- Every cycle uploads JSON evidence plus a Markdown dashboard for 90 days.
- Controlled failure-injection tests cover transient mismatch recovery,
  persistent mismatch rejection, skipped transitions, and idempotent phase
  recording.

## Acceptance evidence to collect

| Evidence | Source | Result |
|---|---|---|
| Targeted regression suite | local pytest | 20 passed |
| Ruff | local `.venv` | passed |
| Exact staging `--help` invocation | local process | passed |
| Failure-injection tests | local pytest | passed |
| Federation cycle 1 | GitHub Actions run `31029649076` | PASS |
| Federation cycle 2 | GitHub Actions run `31029985457` | PASS |
| Independent endpoint verification | canonical/direct live probe | PASS |

## Final acceptance evidence

Run `31029649076` completed staging, clone, merge, publication, Worker deploy,
ledger verification, evidence generation, dashboard construction, and artifact
upload. Its ledger ended in `verified`; its publication evidence commit matched
the verifier commit `80fbd10d8893a7bc0a9095809cc7d190125c3497`.

Run `31029985457` repeated the same path successfully. Its ledger ended in
`verified`; its publication evidence commit matched the verifier commit
`0af373a1c82fde32a308337fb315c58fb03eaf75`.

An independent live probe after the second run returned byte-identical
canonical and direct `/api/v1/version` responses. Both exposed data commit
`0af373a1c82fde32a308337fb315c58fb03eaf75` and registry hash
`7f6ffb97a558da8828a01833ab9fe3bfa0742088f90c88d1c61df5bc8ac39605`.
The active Cloudflare production deployment is Worker version
`7ff8ebec-6ade-4435-874c-57430a2238f4`.

The controlled failure run `31028905330` remains recorded as a rejected cycle:
it exposed stale workflow registry-hash configuration, which was corrected
without changing registry contents. No unresolved P0/P1 defect was observed.

## Verdict

`VERIFIED_AUTONOMOUS_OPERATION`: two consecutive clean production cycles
completed without operator intervention, produced complete evidence ledgers,
verified endpoint convergence, and preserved the existing approval and
publication gates.

## First-cycle finding

Cycle `31028905330` reached publication and Worker deployment but failed the
new convergence gate because the workflow expected registry hash `6fbb4c…`
while the authoritative checked-in registry and generated public manifest
contained `7f6ffb…`. No catalog or registry content was changed. The workflow
constants were corrected to the authoritative file hash, and the cycle is
retained as a failed evidence record rather than treated as acceptance.

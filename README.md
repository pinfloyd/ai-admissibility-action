# AI Admissibility Action

**Public GitHub Marketplace evaluation surface for fail-closed external admission.**

Official product surface:

https://ai-admissibility.com/

## Current implementation status

This Action provides a bounded public evaluation path.

- Missing or invalid admission context fails closed.
- `pilot-smoke-only: "true"` provides a synthetic Proof Access smoke path.
- Outside that synthetic evaluation path, runtime authority integration is **not yet wired in this public Action** and the Action intentionally fails closed.

Therefore this repository does **not** claim that installing the Marketplace Action alone creates a production external admission boundary.

## Example evaluation usage

```yaml
- name: AI Admissibility Gate
  uses: pinfloyd/ai-admissibility-action@v0.1.1
  with:
    authority-url: https://example-authority.company.tld/admit
    authority-pubkey: sha256:replace-with-pinned-authority-pubkey
    policy-id: ai-secrets-v1
    trust-verdict: PASS
    proof-access-id: REPLACE_WITH_PROOF_ACCESS_ID
    pilot-smoke-only: "true"
```

## What the public Action proves

- required Proof Access context is checked;
- missing or placeholder values are rejected;
- admission inputs are validated fail-closed;
- the synthetic evaluation path is explicitly separated from production claims.

## What it does not claim

- not a production no-bypass guarantee by default;
- not a public unauthenticated authority endpoint;
- not monitoring, scanning, or rollback;
- not a customer-specific production deployment.

## Production / private integration

Customer-specific runtime integration requires a controlled authority contract, access binding, and validation of both DENY and ALLOW behavior for the protected workflow.

Request access:

https://ai-admissibility.com/request

## Related surfaces

- Boundary architecture / proof: https://github.com/pinfloyd/ai-admissibility-boundary
- Compatibility slug retained for older references: https://github.com/pinfloyd/cnp-action
- Technical Brief: https://ai-admissibility.com/technical-brief/
- Reference Guide: https://ai-admissibility.com/reference-guide/
- Canonical Terms: https://ai-admissibility.com/canonical-terms/

**No Admission = No Execution.**

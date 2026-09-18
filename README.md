# AI Admissibility Action

**Public GitHub evaluation surface for fail-closed external admission concepts.**

Official public demonstration surface:

https://ai-admissibility.com/

## Current implementation status

This repository is a bounded public evaluation surface.

- It validates required admission context.
- It rejects missing or placeholder configuration.
- `pilot-smoke-only: "true"` provides a synthetic smoke path.
- Outside that synthetic path, runtime authority integration is **not wired in this public Action** and the Action intentionally fails closed.

Installing this Action alone does **not** create a production external admission boundary and does not provide customer-specific no-bypass protection.

## Example synthetic evaluation

The current `main` branch is evaluation-only:

```yaml
- name: AI Admissibility synthetic evaluation
  uses: pinfloyd/ai-admissibility-action@main
  with:
    authority-url: https://example-authority.company.tld/admit
    authority-pubkey: sha256:replace-with-pinned-authority-pubkey
    policy-id: ai-secrets-v1
    trust-verdict: PASS
    pilot-smoke-only: "true"
```

The `proof-access-id` input is retained only as a deprecated compatibility input for older examples. The current public website does not issue Proof Access IDs or credentials.

## What the public Action proves

- required admission inputs are checked;
- placeholder or incomplete configuration is rejected;
- a non-PASS trust verdict is rejected;
- the synthetic evaluation path is clearly separated from production claims;
- outside the synthetic path, absence of runtime authority integration fails closed.

## What it does not claim

- no production no-bypass guarantee by default;
- no public unauthenticated authority endpoint;
- no monitoring, scanning, or rollback claim;
- no customer-specific production deployment;
- no checkout, payment processing, credential issuance, or hosted customer runtime.

## Historical release note

Published historical tags are not rewritten. Older tags may still contain Proof Access, Hosted Authority, payment, or access-language from earlier product stages. Those tags are historical artifacts; use `main` and the official site for current public semantics.

## Public role and collaboration

The website and GitHub repositories are public showcase, documentation, proof, and demonstration surfaces.

For research, integration, collaboration, or deployment discussions:

**governance@ai-admissibility.com**

## Related surfaces

- Canonical live demonstration: https://ai-admissibility.com/canonical-pilot/
- Boundary architecture / proof: https://github.com/pinfloyd/ai-admissibility-boundary
- Compatibility slug retained for older references: https://github.com/pinfloyd/cnp-action
- Technical Brief: https://ai-admissibility.com/technical-brief/
- Reference Guide: https://ai-admissibility.com/reference-guide/
- Canonical Terms: https://ai-admissibility.com/canonical-terms/

**No Admission = No Execution.**

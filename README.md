# AI Admissibility Action

**Fail-closed external admission gate for GitHub Actions before execution.**

Public Marketplace version = evaluation surface.
Production authority integration = separate Proof Access / private deployment path.

## What risk does it address?

GitHub Actions can build, test, release, deploy, touch secrets, assume cloud roles, or run production-impacting automation.
When AI-generated changes, agent-created pull requests, secrets exposure risk, or automation-driven deployment paths are involved, the key question is not only whether the workflow is syntactically valid.
The key question is whether the protected execution context should be admitted at all.

## What happens?

Valid evaluation context -> evaluation path.
Missing or invalid context -> fail closed.

## Example usage

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

## What this is not

- Not a scanner.
- Not monitoring.
- Not a secrets manager.
- Not GitHub-native approval.
- Not a production no-bypass guarantee by default.

## Public evaluation vs production authority

**Public Marketplace version**
- installable evaluation surface;
- fail-closed preview behavior;
- Proof Access request path;
- no customer-specific production guarantee by default.

**Production / private deployment**
- external authority integration;
- customer-specific runtime binding;
- buyer-controlled deployment values;
- acceptance / proof package.

## Inputs

The public Action surface uses the following evaluation-facing inputs:

- `authority-url`
- `authority-pubkey`
- `policy-id`
- `trust-verdict`
- `proof-access-id`
- `pilot-smoke-only`

Missing or invalid admission context must fail closed.

## Proof Access

Use Proof Access when you want to evaluate the public Marketplace action before paid or private deployment access.

1. Install this GitHub Action in your workflow.
2. Request Proof Access or private deployment review.
3. Add the returned values only as instructed.
4. Run the workflow and inspect the result.
5. Missing or invalid context must fail closed.

Pilot non-claims: Proof Access is synthetic evaluation only. It is not production access, not paid tier access, not private deployment, and not a customer no-bypass guarantee.

## Request Proof Access or private deployment review

[Request access](https://ai-admissibility.com/request)

## Why external admission?

Pre-run policy is necessary. External admission is the stronger boundary.

Platform-native controls improve the executor. External admission separates execution from authority.

If execution can proceed without an external allow decision, the system has policy, but not external admission authority.

**No Admission = No Execution.**

## Learn more

- Technical Brief: https://ai-admissibility.com/technical-brief/
- Surrogate Boundary Test: https://ai-admissibility.com/surrogate-boundary-test/
- Reference Guide: https://ai-admissibility.com/reference-guide/

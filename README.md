# AI Admissibility Action

**Fail-closed external admission gate for GitHub Actions before execution.**

Use this action when workflow execution should **stop unless the required admission context is present and valid**.

## Start here

1. Install the action in your workflow.
2. Request Proof Access for evaluation or request private deployment review.
3. Supply the issued values only as instructed.
4. Run the workflow.
5. Missing or invalid context must fail closed.

[Request access](https://ai-admissibility.com/request)

## Who this is for

- teams evaluating execution control for GitHub Actions;
- teams worried about AI-generated changes reaching CI/CD;
- teams that want fail-closed behavior instead of silent continuation;
- teams comparing platform-native policy vs external admission.

## What risk does it address?

GitHub Actions can build, test, release, deploy, touch secrets, assume cloud roles, or trigger production-impacting automation.
When AI-generated changes, agent-created pull requests, secrets exposure risk, or automation-driven deployment paths are involved, the key question is not only whether a workflow is syntactically valid.
The key question is whether the protected execution context should be admitted at all.

## What happens?

- valid evaluation context -> evaluation path;
- missing or invalid context -> fail closed.

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

## Inputs

- `authority-url`
- `authority-pubkey`
- `policy-id`
- `trust-verdict`
- `proof-access-id`
- `pilot-smoke-only`

Missing or invalid admission context must fail closed.

## What this is not

- Not a scanner.
- Not monitoring.
- Not a secrets manager.
- Not GitHub-native approval.
- Not a production no-bypass guarantee by default.

## Public evaluation vs private deployment

**Public Marketplace version**
- installable evaluation surface;
- fail-closed preview behavior;
- Proof Access request path;
- not a customer-specific production guarantee by default.

**Private deployment path**
- external authority integration;
- customer-specific runtime binding;
- controlled deployment values;
- acceptance / proof package.

## Proof Access

Use Proof Access when you want to evaluate the public Marketplace action before paid or private deployment access.

Pilot non-claims: Proof Access is synthetic evaluation only. It is not production access, not paid tier access, not private deployment, and not a customer no-bypass guarantee.

## Why external admission?

Pre-run policy is necessary. External admission is the stronger boundary.

Platform-native controls improve the executor. External admission separates execution from authority.

If execution can proceed without an external allow decision, the system has policy, but not external admission authority.

**No Admission = No Execution.**

## Learn more

- Technical Brief: https://ai-admissibility.com/technical-brief/
- Surrogate Boundary Test: https://ai-admissibility.com/surrogate-boundary-test/
- Reference Guide: https://ai-admissibility.com/reference-guide/

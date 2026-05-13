# AI Admissibility Action

**AI Admissibility Action is an external admission gate for GitHub Actions before trusted execution.**

Public Marketplace version = **pilot / fail-closed preview**.  
Production authority integration = **Proof Access / private deployment review**.

## What risk does it address?

GitHub Actions can build, test, release, deploy, touch secrets, assume cloud roles, or run production-impacting automation. When AI-generated PRs, agent-created changes, CI/CD workflows, secrets, cloud roles, deployment paths, or automated remediation steps are involved, the question is not only whether the workflow is valid. The question is whether the protected execution context should be admitted at all.

## What happens?

Valid pilot context -> admission path.  
Missing or invalid context -> fail closed.

## Install
~~~yaml
- name: AI Admissibility Gate
  uses: pinfloyd/ai-admissibility-action@v0.1.1
  with:
    mode: pilot
~~~

## What this is not

Not a scanner.  
Not monitoring.  
Not a secrets manager.  
Not GitHub-native approval.  
Not production no-bypass by default.

## Public pilot vs production authority

**Public Marketplace version**
- installable pilot surface;
- fail-closed preview behavior;
- Proof Access request path;
- no customer production no-bypass guarantee by default.

**Production / private deployment**
- external authority integration;
- customer-specific runtime binding;
- buyer-controlled deployment values;
- acceptance / proof package.

## Inputs

The public action surface supports pilot / preview inputs used to demonstrate fail-closed admission behavior:

- `mode`
- `authority-url`
- `authority-pubkey`
- `policy-id`
- `trust-verdict`
- `proof-access-id`

Missing placeholder or invalid admission context must fail closed.

## Proof Access

Use Proof Access when you want to test the public Marketplace action before paid or private deployment access.

1. Install this GitHub Action in your workflow.
2. Request Proof Access or private deployment review.
3. Add the returned values as repository secrets when instructed.
4. Run the workflow and inspect the result.
5. Missing or invalid context must fail closed.

Pilot non-claims: Proof Access is synthetic evaluation only. It is not production access, not paid tier access, not private deployment, and not a customer no-bypass guarantee.

## Why external admission?

Pre-run policy is necessary. External admission is the stronger boundary.

Platform-native controls improve the executor. External admission separates execution from authority.

If execution can proceed without an external allow decision, the system has policy, but not external admission authority.

**No Admission = No Execution.**

## Request Proof Access or private deployment review

https://ai-admissibility.com/request/

## Learn more

- Technical Brief: https://ai-admissibility.com/technical-brief/
- Surrogate Boundary Test: https://ai-admissibility.com/surrogate-boundary-test/
- Reference Guide: https://ai-admissibility.com/reference-guide/

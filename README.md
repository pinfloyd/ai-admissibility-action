# ai-admissibility-action

## Proof Access pilot in 30 seconds

This GitHub Action is a pilot onboarding surface for AI Admissibility. It shows how a user can request temporary Proof Access, pass a `proof_access_id` into GitHub Actions, and see a synthetic `PASS` smoke result without touching production access.

Fast path:
1. Open `https://ai-admissibility.com/#get-proof-access`.
2. Request pilot Proof Access for this repository.
3. Copy the returned `proof_access_id`.
4. Run the `Pilot Proof Access Smoke` workflow manually and paste the id.
5. Confirm the workflow log contains `PILOT_PROOF_ACCESS_SMOKE=PASS`.

Verified pilot E2E reference: `https://github.com/pinfloyd/ai-admissibility-action/actions/runs/24959798826`.

Non-claims: this pilot path is synthetic evaluation only. It is not production access, not paid tier access, not private deployment, and not a customer no-bypass guarantee. Normal runtime execution remains fail-closed until real authority integration is wired.


External admission gate for GitHub Actions.

This repository is the clean action-only install surface for AI Admissibility.

## What it does

- checks that `authority-url` is present
- checks that `authority-pubkey` is present
- checks that `policy-id` is present
- checks that `trust-verdict` is present
- blocks placeholder values
- fails closed if `trust-verdict` is not `PASS`

## Current status

This public action surface is a preview install surface.

Runtime authority integration is not wired in this public repository yet, so the action currently fails closed intentionally after preflight validation.

## Inputs

- `authority-url`
- `authority-pubkey`
- `policy-id`
- `trust-verdict`

## Example

```yaml
- name: External admission gate
  uses: pinfloyd/ai-admissibility-action@v0.1.0
  with:
    authority-url: https://example-authority.invalid
    authority-pubkey: example-real-pubkey
    policy-id: example-real-policy
    trust-verdict: PASS
```

## Commercial path

- site: https://ai-admissibility.com/
- request path: https://ai-admissibility.com/request/

GitHub is not checkout.

## Proof and reference

- GitHub product surface: https://github.com/pinfloyd/cnp-action
- Zenodo reference: https://zenodo.org/records/18716478

## Proof access bridge input

This Marketplace Action now includes the `proof-access-id` input for the future self-guided proof-access bridge.

Required bridge inputs:

- `authority-url`
- `policy-id`
- `proof-access-id`

The action must fail closed when `proof-access-id` is missing or left as a placeholder.

Runtime authority integration still requires a separately verified implementation step before this surface should be treated as a complete production bridge.

Example:

```yaml
- uses: pinfloyd/ai-admissibility-action@v0.1.0
  with:
    authority-url: https://admit.ai-admissibility.com/admit
    policy-id: ai-secrets-v1
    proof-access-id: ${{ secrets.AI_ADMISSIBILITY_PROOF_ACCESS_ID }}
    authority-pubkey: ${{ secrets.AI_ADMISSIBILITY_AUTHORITY_PUBKEY }}
    trust-verdict: PASS
```
## Proof Access pilot onboarding

Use Proof Access when you want to test this action before paid or private deployment access.

1. Install this GitHub Action in your workflow.
2. Get temporary pilot Proof Access from https://ai-admissibility.com/#get-proof-access.
3. The form posts to https://ai-admissibility.com/proof-access and returns a `proof_access_id`.
4. Add `AI_ADMISSIBILITY_PROOF_ACCESS_ID` and `AI_ADMISSIBILITY_AUTHORITY_PUBKEY` as repository secrets.
5. Run the workflow and inspect the authority result. A valid pilot context can proceed to the hosted authority decision path; invalid or missing context must fail closed as DENY.

Pilot non-claims: Proof Access is synthetic evaluation only. It is not production access, not paid tier access, not private deployment, and not a customer no-bypass guarantee.

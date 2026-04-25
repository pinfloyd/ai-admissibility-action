# ai-admissibility-action

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
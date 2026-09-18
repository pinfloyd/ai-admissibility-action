# AI Admissibility Technical Brief

## External pre-execution admission before high-impact execution

AI Admissibility is an external ALLOW/DENY boundary model for AI-driven workflows, agents, CI/CD jobs, cloud identity flows, and other authority-bearing automation.

The core rule is:

**No Admission = No Execution.**

## The problem

AI and automation can modify code, trigger deployments, call APIs, change infrastructure, move money, or affect customer state. Scanners, logs, reviews, and incident reports can be useful, but they often operate after or around execution.

AI Admissibility addresses a different question:

**Should this actor, with this intent, in this current context, receive authority to act before the protected effect occurs?**

## Canonical public demonstration

The canonical installed boundary used for the current public demonstration is:

`AI_BOUNDARY_RELEASE_V1`

The official live demonstration is:

https://ai-admissibility.com/canonical-pilot/

The public browser uses a fixed demonstration path. It does not receive unrestricted authority credentials and cannot directly invoke the isolated protected effect mechanism.

The public identity endpoint is intentionally protected, and anonymous admission is intentionally rejected. Those properties are part of the current public contract, not signs that the boundary is unavailable.

## GitHub Action role

This repository is a bounded evaluation surface.

The Action:

- validates required evaluation context;
- rejects placeholder configuration;
- supports an explicit synthetic smoke mode;
- fails closed outside that synthetic mode because runtime authority integration is not wired in this public repository.

The Action does **not** call the canonical installed boundary for general customer execution and does not create a production boundary merely by being installed.

## Synthetic evaluation

A synthetic smoke run proves only that the Action loads, validates its inputs, and maintains fail-closed discipline around its bounded evaluation path.

Historical synthetic smoke evidence may still exist in GitHub Actions history. That evidence is not a current credential-issuance or production-access path.

## Real integration requirement

A real high-impact workflow needs a stronger property than a successful Action run:

1. the exact protected action is defined;
2. a separate authority decides before that action;
3. the client verifies the authority result;
4. DENY, missing, invalid, expired, stale, or unverifiable admission blocks execution;
5. no alternate bypass path reaches the same protected effect.

That customer-specific no-bypass property is not claimed by the public Marketplace evaluation Action.

## Public role and non-claims

The website and GitHub repositories are public showcase, documentation, proof, and demonstration surfaces.

They do not provide:

- public checkout;
- payment processing;
- automatic credential issuance;
- a generally open production authority endpoint;
- customer production execution;
- a universal safety, security, legal, or compliance guarantee.

## Collaboration

For research, integration, collaboration, or deployment discussions:

**governance@ai-admissibility.com**

## Public references

- Official site: https://ai-admissibility.com/
- Canonical demo: https://ai-admissibility.com/canonical-pilot/
- Reference Guide: https://ai-admissibility.com/reference-guide/
- Surrogate Boundary Test: https://ai-admissibility.com/surrogate-boundary-test/
- Boundary repository: https://github.com/pinfloyd/ai-admissibility-boundary

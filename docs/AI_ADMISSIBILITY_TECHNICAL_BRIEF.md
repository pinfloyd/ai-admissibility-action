# AI Admissibility Technical Brief

## External fail-closed gate for AI-driven execution

AI Admissibility is an external ALLOW/DENY boundary for AI-driven workflows, GitHub Actions, agents, and automation systems. Its purpose is simple: execution should not proceed unless a valid authority decision exists before the action runs.

## The problem

AI and automation can now modify code, trigger deployments, approve workflow steps, call APIs, and affect infrastructure. In many systems, the first real control happens after execution: logs, scans, alerts, reviews, or incident reports. That is too late for high-impact automation.

## Why post-event audit is not enough

A scanner can tell you what happened. A log can help explain what failed. A dashboard can show risk after the fact. None of those stop execution before it happens. AI Admissibility is built around a stricter rule: no valid authority decision means no execution.

## What AI Admissibility does

AI Admissibility adds an external pre-execution gate. A workflow or agent must obtain an authority-backed decision before continuing. If the decision is missing, invalid, stale, unverifiable, or denied, the client fails closed.

Core behavior:

- validate required authority context;
- reject placeholder configuration;
- request or receive an authority decision;
- verify the decision before proceeding;
- fail closed by default;
- separate pilot proof from production access.

## GitHub Action pilot path

The public GitHub Action is the developer-facing pilot surface. It allows a user to request temporary Proof Access, pass a proof_access_id into GitHub Actions, and run a synthetic smoke workflow.

Verified pilot E2E PASS run: https://github.com/pinfloyd/ai-admissibility-action/actions/runs/24959798826

Pilot path:

1. Open https://ai-admissibility.com/#get-proof-access
2. Request Proof Access.
3. Copy the returned proof_access_id.
4. Run the Pilot Proof Access Smoke workflow.
5. Confirm the log contains PILOT_PROOF_ACCESS_SMOKE=PASS.

## Production path

The production path is not the same as the synthetic pilot. In production, a client should not manually provide a trust verdict in YAML. The action should send a deterministic request payload to the hosted authority, receive a signed ALLOW/DENY decision, verify it locally, and continue only if the signed decision is valid.

Production flow:

1. Customer receives access context after approval or payment.
2. Workflow builds a deterministic request payload.
3. Hosted authority evaluates the request.
4. Authority returns a signed ALLOW/DENY decision.
5. GitHub Action verifies signature, policy, request hash, and verdict.
6. Workflow continues only on valid ALLOW.
7. Everything else fails closed.

## Pilot non-claims

The current public pilot is synthetic evaluation only. It is not production access, not paid tier access, not private deployment, and not a customer no-bypass guarantee. It proves the onboarding path, action loading, proof_access_id propagation, and fail-closed discipline.

## Who this is for

AI Admissibility is for teams that allow AI or automation to touch code, deployments, approvals, infrastructure, or high-impact workflows.

Relevant users:

- GitHub Actions and CI/CD teams;
- AI agent builders;
- DevOps and platform teams;
- security teams evaluating AI execution risk;
- founders building automation-heavy systems;
- teams that need pre-execution control rather than post-event audit.

## What you get

Pilot:

- temporary proof_access_id;
- GitHub Actions smoke workflow;
- public PASS/DENY proof path;
- synthetic evaluation only.

Private / production path:

- hosted authority endpoint;
- access context and policy binding;
- signed ALLOW/DENY decision path;
- local verification;
- fail-closed integration guidance.

## Call to action

Start with Proof Access: https://ai-admissibility.com/#get-proof-access

For production or private deployment, request commercial access from the site.

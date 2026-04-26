# GitHub Marketplace Listing Copy v2 — Clean

## Product name

AI Admissibility Action

## One-line tagline

Stop AI-driven workflows unless an external authority allows execution.

## Short description

A fail-closed GitHub Action for AI and automation workflows. It validates authority context, blocks placeholder setup, supports a Proof Access pilot, and keeps execution stopped unless the required admission path is valid.

## Marketplace description

AI Admissibility Action is a developer-facing gate for AI-driven execution. It is designed for GitHub Actions, CI/CD workflows, agents, and automation systems where execution should not continue unless an external authority decision exists before the action runs.

Most security tools explain what happened after execution. AI Admissibility is built around a stricter rule: no valid authority decision means no execution.

The public pilot path lets a developer request temporary Proof Access, pass a proof_access_id into GitHub Actions, and verify the synthetic smoke path through a public PASS run. Production access is separate and is intended to use a hosted authority decision, signed ALLOW/DENY response, local verification, and fail-closed behavior.

## What it does

- Validates required authority inputs.
- Rejects placeholder configuration.
- Provides a Proof Access pilot workflow.
- Demonstrates fail-closed behavior when authority integration is not wired.
- Links the action, technical brief, and verified pilot PASS run into one public proof path.

## Who it is for

- GitHub Actions and CI/CD teams.
- AI agent builders.
- DevOps and platform teams.
- Security teams evaluating AI execution risk.
- Teams that need pre-execution control instead of post-event audit.

## Public proof

- Site technical brief is published.
- GitHub docs technical brief is published.
- Verified pilot E2E PASS run is public.
- Proof Access entry is available from the site.

## Non-claims

The current public pilot is synthetic evaluation only. It is not production access, not paid tier access, not private deployment, and not a customer no-bypass guarantee.

## Suggested categories

Security, DevOps, CI/CD, GitHub Actions, AI Safety, Automation Governance, Policy Enforcement, Supply Chain Security

## Search keywords

ai security, github actions security, fail closed, admission control, policy gate, ai agent security, ci cd gate, pre execution control, automation risk, external authority, allow deny, proof access

## Links / Next steps

Get Proof Access: https://ai-admissibility.com/#get-proof-access

Read the Technical Brief: https://ai-admissibility.com/technical-brief/

View verified pilot PASS run: https://github.com/pinfloyd/ai-admissibility-action/actions/runs/24959798826

# GitHub Marketplace Listing Copy — current public semantics

## Product name

AI Admissibility Action

## One-line tagline

Fail closed unless the required admission context is valid before execution.

## Short description

A bounded GitHub Action evaluation surface for external-admission concepts. It validates authority context, rejects placeholder setup, supports an explicit synthetic smoke mode, and fails closed because live runtime authority integration is not wired in the public Action.

## Marketplace description

AI Admissibility Action is a developer-facing evaluation surface for AI-driven and automated execution.

It demonstrates one core discipline:

**No Admission = No Execution.**

The public Action validates its required inputs and can run an explicit synthetic smoke path. Outside that synthetic path, it intentionally fails closed because the public Action is not wired to the canonical installed authority.

The canonical live demonstration is separate:

https://ai-admissibility.com/canonical-pilot/

Installing the Marketplace Action alone does not create a customer production boundary and does not prove a no-bypass integration.

## What it does

- Validates required evaluation inputs.
- Rejects missing and placeholder configuration.
- Provides an explicit synthetic smoke path.
- Demonstrates fail-closed behavior when live authority integration is absent.
- Keeps the public Action distinct from the canonical installed boundary.

## What it does not do

- No public checkout or payment processing.
- No automatic credential issuance.
- No generally open production authority endpoint.
- No customer-specific no-bypass guarantee.
- No monitoring, scanning, rollback, or universal security claim.

## Historical compatibility

Older published tags may still contain Proof Access or Hosted Authority language from earlier product stages. Published tags are historical artifacts and are not rewritten.

Use the current default branch and official site for current public semantics.

## Who it is for

- GitHub Actions and CI/CD teams;
- AI agent builders;
- DevOps and platform teams;
- security teams evaluating AI execution risk;
- teams studying pre-execution authority separation.

## Suggested categories

Security, DevOps, CI/CD, GitHub Actions, AI Safety, Automation Governance, Policy Enforcement, Supply Chain Security

## Search keywords

ai security, github actions security, fail closed, admission control, policy gate, ai agent security, ci cd gate, pre execution control, automation risk, external authority, allow deny

## Links / next steps

Canonical live demo: https://ai-admissibility.com/canonical-pilot/

Technical Brief: https://ai-admissibility.com/technical-brief/

Reference Guide: https://ai-admissibility.com/reference-guide/

Collaboration: governance@ai-admissibility.com

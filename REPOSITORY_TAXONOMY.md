# File: .github/REPOSITORY_TAXONOMY.md

# Symfony-X Repository Taxonomy

This document defines the repository structure, classification tiers, and governance policies for Symfony-X.

> Symfony-X is a constraint-driven Symfony 8 platform built around a single skeleton, modular Feature Modules, and recipe-driven automation.

---

# Tier A — Foundation (Platform Layer)

These repositories define how Symfony-X works.

They are:
- highly stable
- tightly controlled
- architecturally critical

## Repositories

- symfony-x/skeleton
- symfony-x/ui
- symfony-x/maker
- symfony-x/dev-tools
- symfony-x/recipes

## Role

- define Symfony-X baseline (Symfony 8 + LAST stack)
- enforce architectural constraints
- provide deterministic scaffolding
- define UI contract (Twig + Tailwind + Stimulus)
- standardize development tooling
- automate configuration via recipes

## Policy

- collaborator-only PRs
- 2 approvals minimum
- CODEOWNERS required
- architect signoff required
- strict CI required

---

# Tier B — Feature Modules (Product Layer)

These repositories provide installable, complete feature systems.

They are what Developers actually install.

## Repositories (Initial)

- symfony-x/user
- symfony-x/user-oauth
- symfony-x/admin

## Future Candidates

- symfony-x/ai
- symfony-x/billing
- symfony-x/messenger
- symfony-x/mercure

## Role

Each Feature Module MUST:

- be installable independently
- provide a complete working feature
- include:
  - backend logic
  - configuration
  - routes
  - templates/components
  - Tailwind styling
  - default UX
  - recipe automation

## Policy

- trusted contributors allowed
- 1–2 approvals required
- maintainer review required
- API changes require architect review

---

# Tier C — Recipes (Automation Layer)

Recipes automate installation and configuration.

## Repositories

- symfony-x/recipes

## Role

Recipes are responsible for:

- copying configuration
- wiring routes
- installing templates
- defining environment variables
- applying opinionated defaults

## Rules

- every Feature Module MUST have a recipe
- recipes MUST be deterministic
- no interactive/manual steps required

## Policy

- trusted contributors allowed
- 1–2 approvals required
- strict review for breaking changes

---

# Tier D — Documentation & Examples

Public-facing repositories that support Developer adoption.

## Repositories

- symfony-x/docs
- symfony-x/examples

## Role

- document architecture and usage
- provide example applications
- demonstrate Feature Module integration

## Policy

- public PRs allowed
- triage-first review queue
- maintainer merge required

---

# Tier E — Experimental Labs

Unstable, exploratory repositories.

## Repositories

- symfony-x/labs-*

Examples:
- symfony-x/labs-ai-agent
- symfony-x/labs-realtime-runtime
- symfony-x/labs-event-systems

## Role

- explore new ideas
- test architecture extensions
- prototype future Feature Modules

## Policy

- invite-only contributors
- unstable branch model allowed
- no API stability guarantees

---

# Tier F — Internal Infrastructure

Internal operational repositories.

## Repositories

- symfony-x/release-engineering
- symfony-x/security-advisories
- symfony-x/deployment-infra

## Policy

- maintainers only
- restricted branch pushes
- no external contributions

---

# Starter Stacks (Future Layer)

Starter Stacks are NOT first-order repositories yet.

When introduced, they will be:

- Composer metapackages
- no code
- dependency-only

Examples (future):

- symfony-x/starter-user
- symfony-x/starter-saas
- symfony-x/starter-admin

## Role

- install curated sets of Feature Modules
- provide rapid application bootstrapping

---

# Default PR Access by Tier

| Tier | Outside Public PRs |
|------|--------------------|
| A (Foundation) | No |
| B (Feature Modules) | Limited |
| C (Recipes) | Limited |
| D (Docs/Examples) | Yes |
| E (Labs) | No |
| F (Internal) | No |

---

# Branch Protection Standards

## Tier A — Foundation

- 2 approvals required
- latest push approval required
- stale approvals dismissed
- CODEOWNERS required
- strict CI required

---

## Tier B — Feature Modules

- 1–2 approvals required
- CI required
- CODEOWNERS required

---

## Tier C — Recipes

- 1–2 approvals required
- CI required
- careful review for install behavior

---

## Tier D — Docs / Examples

- 1 approval required
- basic CI required
- maintainer merge only

---

## Tier E — Labs

- maintainer discretion
- unstable policies allowed

---

## Tier F — Internal

- maintainers only
- restricted pushes

---

# Naming & Structural Rules

## Foundation Repositories

- MUST remain minimal
- MUST NOT contain business features

## Feature Modules

- MUST represent complete features
- MUST include UI + backend + config
- MUST NOT be partial capability packages

## Recipes

- MUST be deterministic
- MUST not require manual setup

## Terminology Alignment

- Developer = person building the app
- Application User = end user of the app
- User Entity = internal model

---

# Initial Repository Set

## Foundation

- .github
- symfony-x/skeleton
- symfony-x/ui
- symfony-x/maker
- symfony-x/dev-tools
- symfony-x/recipes

## Feature Modules

- symfony-x/user
- symfony-x/user-oauth
- symfony-x/admin

## Documentation

- symfony-x/docs
- symfony-x/examples

## Labs

- symfony-x/labs-*

---

# Guiding Principle

> Symfony-X repositories must reduce ambiguity, enforce structure, and enable deterministic development.

---

End of Specification

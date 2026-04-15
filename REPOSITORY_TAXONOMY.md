# File: .github/REPOSITORY_TAXONOMY.md

# Symfony-X Repository Taxonomy

## Purpose

This document defines the repository classes, ownership model, and governance rules for the Symfony-X organization.

Symfony-X is organized around:

1. a constrained Composer package ecosystem
2. one minimal universal skeleton
3. one separate control-plane product (`Buffer`)

The repository structure must preserve architectural clarity, prevent structural drift, and keep application-local concerns separate from ecosystem governance.

---

## Repository Classes

### Tier A — Canonical Core Repositories

These repositories define the foundation, automation, deterministic generation model, and quality standards of the Symfony-X ecosystem.

Examples:

- `symfony-x/skeleton`
- `symfony-x/recipes`
- `symfony-x/maker`
- `symfony-x/dev-tools`

Characteristics:

- define ecosystem-wide contracts or defaults
- affect many downstream repositories
- highest architectural sensitivity
- changes require strong review discipline

Policy:

- collaborator-only pull requests
- no anonymous or drive-by PR acceptance by default
- 2 approvals minimum
- CODEOWNERS required on protected paths
- required status checks must pass
- direct pushes to default branch prohibited
- squash merge only
- architect signoff required for structural changes

---

### Tier B — Identity Repositories

These repositories define the application's nature. They are not feature packages.

Examples:

- `symfony-x/ui`
- `symfony-x/api`
- `symfony-x/mcp`

Characteristics:

- establish application mode or operating model
- may be composed explicitly by developers
- must remain sharply bounded
- must not silently become feature dumps

Policy:

- trusted contributor PRs only
- 1 to 2 approvals required depending on change scope
- CODEOWNERS required for core contracts
- required static analysis and test checks
- squash merge only
- architectural review required for public contract changes

#### SXUC Note

`symfony-x/ui` is the SXUC identity repository.

It owns:

- UI-first async identity
- LAST stack integration for UI-first apps
- Mercure-backed deferred propagation semantics for UI
- preset resolution and preset contract boundaries
- async-aware UI Makers

It does not own:

- domain features
- application-specific business workflows
- arbitrary frontend experimentation outside governed contracts

---

### Tier C — Feature Repositories

These repositories add business capability or user-facing systems on top of the foundation and identity layers.

Examples:

- `symfony-x/user`
- `symfony-x/user-oauth`
- `symfony-x/oauth-server`
- `symfony-x/dashboard`
- `symfony-x/admin`

Characteristics:

- composable application modules
- must declare dependencies explicitly
- must not redefine application nature implicitly
- may provide package-local maker commands, profiler collectors, and recipes

Policy:

- trusted contributor PRs allowed
- 1 approval minimum
- required tests and static analysis
- squash merge only
- maintainer review required for new extension points or public API changes

---

### Tier D — Cross-Cutting Integration Repositories

These repositories exist only when a reusable cross-cutting contract clearly justifies its own package.

Examples:

- `symfony-x/mercure`
- `symfony-x/messenger`
- `symfony-x/telemetry`
- `symfony-x/testing`
- `symfony-x/doctrine-tools`

Characteristics:

- reusable infrastructure-facing integration packages
- should not be created prematurely
- should exist only when reuse pressure is proven across multiple packages or apps

Policy:

- trusted contributor PRs allowed
- 1 approval minimum
- required tests and static analysis
- squash merge only
- architectural review required before introducing new Tier D repos

#### SXUC Boundary Rule

A Tier D repository must not silently absorb SXUC identity responsibilities.

For example:

- a generic Mercure integration package may exist
- SXUC still owns UI-facing async transport semantics for UI-first apps

---

### Tier P — Product Repositories

These repositories are standalone deployable products, not normal Composer packages.

Examples:

- `symfony-x/buffer`

Characteristics:

- independent deployment lifecycle
- independent operational concerns
- may serve as control plane, orchestration layer, or governance product
- may expose UI, API, and MCP surfaces
- not governed like a normal library package

Policy:

- collaborator-only pull requests
- 2 approvals minimum
- CODEOWNERS required
- required status checks must pass
- protected environments where applicable
- release discipline required
- security review required for authentication, agent, execution, or governance surfaces
- squash merge only

---

## Architectural Rules by Repository Class

### Rule 1 — Skeleton Must Stay Barebones

`symfony-x/skeleton` is the universal entry point.

It must include only:

- Symfony 8 baseline
- base Docker/dev environment defaults
- standard project bootstrap concerns

It must not include by default:

- LAST stack
- Doctrine
- Mercure
- application-specific features
- opinionated domain scaffolding

---

### Rule 2 — Identity Repositories Define Nature

Identity repositories define what kind of application is being built.

Examples:

- `ui` defines UI-first application capabilities through SXUC
- `api` defines headless/API-first application capabilities
- `mcp` defines AI-first server integration capabilities

Feature packages must not silently assume or install identity concerns unless done through an explicit installation profile or declared dependency path.

---

### Rule 3 — Feature Repositories Add Capability, Not Nature

Feature repositories must:

- add composable capability
- declare required dependencies explicitly
- remain bounded to their feature domain

Feature repositories must not:

- redefine the entire app structure
- become dumping grounds for unrelated helpers
- force hidden architectural choices across the ecosystem
- redefine SXUC-owned async runtime semantics

---

### Rule 4 — Recipes Wire, Packages Own Runtime

`symfony-x/recipes` may:

- wire configuration
- register routes
- enable services
- inject environment defaults
- automate install-time setup

Recipes must not:

- own runtime business logic
- become the source of truth for package behavior

Runtime ownership belongs to the package itself.

---

### Rule 5 — Deterministic Generation Only

If a repository owns structural concepts, it must expose deterministic generation for them.

Manual structural drift is not an acceptable operating model for Symfony-X.

For `symfony-x/ui`, this includes async-aware UI structure.

---

## Guiding Principle

Repositories exist to clarify responsibility, not blur it.

If a repository weakens package boundaries or hides ownership, it works against Symfony-X governance.

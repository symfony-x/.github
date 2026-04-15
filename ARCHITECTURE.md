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
- `ui` defines UI-first application capabilities
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

All generated code in Symfony-X should be produced through deterministic maker commands.

Generation policy:
- shared generation framework lives in `symfony-x/maker`
- package-specific maker commands live with the package that owns the contract
- generated output must follow package contract rules
- generated output should include corresponding test scaffolding where applicable

---

### Rule 6 — Buffer Is a Separate Control-Plane Product

`Buffer` is not an application-local admin panel.

It is a separate control-plane product responsible for concerns such as:
- compatibility validation
- product intent tracking
- generation governance
- architectural linting
- AI agent gateway/MCP coordination
- ecosystem policy enforcement

It must remain separate from normal feature-package concerns.

---

## Dependency Direction Rules

Allowed direction:

1. `skeleton`
2. `recipes`, `maker`, `dev-tools`
3. identity packages (`ui`, `api`, `mcp`)
4. feature packages (`user`, `dashboard`, `admin`, etc.)
5. separate product (`buffer`) integrates with ecosystem but is not a normal downstream feature package

General rule:
- lower layers must not depend on higher layers
- identity packages must not depend on feature packages
- core repositories must not depend on app-specific modules
- feature packages may depend on identity packages only when explicitly required
- Buffer may integrate with many repos, but should not collapse their contracts into itself

---

## Approval Expectations

### Structural Changes
Examples:
- adding or removing repositories
- changing repository class
- changing package boundaries
- changing dependency direction rules
- redefining installation responsibilities

Requirements:
- architect review required
- minimum 2 approvals for Tier A and Tier P
- taxonomy and architecture docs must be updated in the same PR where applicable

### Routine Changes
Examples:
- bug fixes
- test additions
- documentation updates
- localized implementation improvements

Requirements:
- normal approval policy for the affected tier
- all required checks passing

---

## Repository Creation Policy

A new repository should be created only when at least one of the following is true:
- it represents a stable public contract
- it has a clearly bounded responsibility
- it has an independent release cadence
- it needs materially different governance or permissions
- it is reused across multiple packages or applications

A new repository should not be created merely because:
- the code is getting longer
- the idea sounds important
- a future use is imaginable but not yet real

Default bias:
- prefer fewer, clearer repositories
- split only when the boundary is real

---

## Current First-Wave Repository Set

Core:
- `symfony-x/skeleton`
- `symfony-x/recipes`
- `symfony-x/maker`
- `symfony-x/dev-tools`

Identity:
- `symfony-x/ui`
- `symfony-x/api`

Feature:
- `symfony-x/user`

Product:
- `symfony-x/buffer`

These repositories define the initial proof of the Symfony-X architecture.

---

## Second-Wave Candidate Repositories

Identity:
- `symfony-x/mcp`

Feature:
- `symfony-x/dashboard`
- `symfony-x/admin`
- `symfony-x/user-oauth`
- `symfony-x/oauth-server`

Cross-cutting:
- `symfony-x/mercure`
- `symfony-x/messenger`
- `symfony-x/testing`
- `symfony-x/telemetry`

These should be created only after first-wave contracts are proven.

---

## Governance Principle

Symfony-X is not a loose collection of starter kits.

It is a constrained architecture ecosystem built from:
- one minimal skeleton
- explicit identity selection
- composable feature packages
- deterministic code generation
- centralized standards
- a separate governance/control-plane product

The repository taxonomy must always reinforce that model.

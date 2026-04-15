# Symfony-X Package Guidelines

## Purpose

This document defines how to design, structure, and maintain packages within the Symfony-X ecosystem.

All packages must conform to these rules to ensure:

- architectural consistency
- deterministic behavior
- composability
- AI compatibility
- long-term maintainability

---

## Package Philosophy

A Symfony-X package is:

- a **bounded contract**
- a **composable unit of capability**
- a **deterministic contributor to application structure**

It is **not**:

- a dumping ground for utilities
- a hidden architecture layer
- a monolithic subsystem
- a source of implicit behavior

---

## Package Types

### Identity Packages

Examples:

- `symfony-x/ui`
- `symfony-x/api`
- `symfony-x/mcp`

Purpose:

- define application nature

Rules:

- must be explicitly installed
- must not depend on feature packages
- must remain narrowly scoped
- must not contain business logic

#### SXUC-Specific Identity Guidance

`symfony-x/ui` defines the UI-first identity through **SXUC**.

SXUC owns:

- LAST stack integration
- Mercure-backed deferred UI propagation
- async UX transport semantics
- preset resolution
- async-aware Makers for UI structure

SXUC does not own:

- business-domain features
- feature-specific workflow logic
- domain persistence concerns

---

### Feature Packages

Examples:

- `symfony-x/user`
- `symfony-x/dashboard`
- `symfony-x/admin`

Purpose:

- add business capability

Rules:

- must declare dependencies explicitly
- must not redefine application structure
- must not implicitly install identity
- must remain domain-focused

---

### Cross-Cutting Packages

Examples:

- `symfony-x/mercure`
- `symfony-x/messenger`

Purpose:

- provide reusable infrastructure integration

Rules:

- must only exist when reuse is proven
- must remain contract-focused
- must not absorb unrelated concerns

#### SXUC Boundary Note

If a cross-cutting package interacts with UI-first applications, it must not take ownership of SXUC’s async UI semantics.

For example:

- a generic Mercure package may provide reusable infrastructure integration
- SXUC still owns UI-facing topic conventions, UI update contracts, and immediate/deferred UI flow semantics

---

## Required Package Structure

A standard Symfony-X package should follow:

- `src/`
  - `DependencyInjection/`
  - `Controller/` (if applicable)
  - `Entity/` (if applicable)
  - `Security/` (if applicable)
  - `Service/`
  - `Maker/` (if applicable)
  - `Profiler/` (if applicable)
  - `<PackageName>Bundle.php`

- `config/`
  - `services.yaml`
  - `packages/` (optional)
  - `routes/` (optional)

- `templates/` (if UI-related)

- `tests/`

- `composer.json`
- `README.md`

---

## Dependency Rules

### Explicit Dependencies Only

All dependencies must be declared in `composer.json`.

No implicit assumptions.

---

### Direction Constraints

Allowed:

- Feature → Identity
- Feature → Cross-cutting
- Identity → Core tools

Forbidden:

- Identity → Feature
- Core → Feature
- Feature → unrelated feature (without clear contract)

---

### Optional Dependencies

If a feature supports multiple identities:

- use conditional integration
- document clearly
- do not auto-install dependencies

---

## Installation Behavior

### Recipes

If the package includes a recipe, it may:

- register services
- configure bundles
- add routes
- set environment defaults

Recipes must:

- be idempotent
- not override user configuration blindly
- not contain business logic

---

## Maker Integration

### Requirement

If a package introduces a new structural concept, it must provide a Maker command.

Examples:

- `make:x-user`
- `make:x-dashboard-widget`
- `make:x-oauth-client`
- `make:sxuc:component`
- `make:sxuc:live-component`

---

### Rules

- makers must generate deterministic output
- file locations must be fixed and predictable
- naming conventions must be enforced
- generated code must align with package contracts
- test scaffolding should be generated where applicable

### SXUC Maker Requirement

SXUC Makers must generate **async-aware defaults**.

That includes, where applicable:

- predictable template and component placement
- Turbo-friendly template structure
- Stimulus-ready hooks
- deferred update readiness
- preset-aware but contract-safe output

---

## Configuration Design

- use namespaced configuration (e.g. `symfony_x_user`)
- provide sane defaults
- allow overrides
- avoid deep nesting unless necessary

### SXUC Configuration Rule

For `symfony-x/ui`, configuration must keep architectural decisions explicit.

Examples of explicit concerns:

- preset selection
- component paths
- template paths
- feature toggles that do not violate identity invariants

Configuration must not hide core identity behavior.

---

## Service Design

- use dependency injection exclusively
- avoid static access patterns
- keep services small and focused
- expose clear interfaces where extension is expected

### SXUC Service Guidance

SXUC should expose clear service boundaries for:

- preset resolution
- UI update publication
- topic or stream helper generation
- async rendering helpers where needed

---

## Entity Design

- entities must belong to the package domain
- do not leak entities across unrelated packages
- keep persistence concerns contained
- avoid tight coupling to UI or API layers

---

## Security Design

- use Symfony Security component
- define voters where appropriate
- avoid hardcoding roles
- allow extensibility for custom policies

---

## UI Integration (if applicable)

If the package depends on `symfony-x/ui`:

- follow LAST stack principles
- use Stimulus, Turbo, and Live Components correctly
- keep UI components reusable
- respect SXUC async semantics

Packages depending on SXUC must not:

- treat Turbo as optional in SXUC-owned flows
- invent their own competing UI event transport without clear contract extension
- silently shift UI ownership to client-only application state

---

## Profiler Integration

Packages should provide a `DataCollector` when meaningful.

Examples:

- security decisions (`user`)
- UI state (`ui`)
- AI traffic (`mcp`)

Rules:

- only include useful, actionable data
- avoid noise
- ensure performance impact is minimal

---

## Testing Requirements

Every package must include:

- unit tests for core logic
- integration tests where applicable
- functional tests where runtime behavior is significant

### SXUC Testing Guidance

SXUC and any preset package should test:

- rendering output structure
- preset resolution behavior
- async-ready scaffolding correctness
- integration points for Turbo/Mercure-oriented flows where applicable

---

## Guiding Principle

A Symfony-X package should make the system clearer, not blurrier.

If a package hides architecture, expands without bounds, or weakens deterministic generation, it is not a good Symfony-X package.

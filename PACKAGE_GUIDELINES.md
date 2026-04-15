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

---

### Rules

- makers must generate deterministic output  
- file locations must be fixed and predictable  
- naming conventions must be enforced  
- generated code must align with package contracts  
- test scaffolding should be generated where applicable  

---

## Configuration Design

- use namespaced configuration (e.g. `symfony_x_user`)  
- provide sane defaults  
- allow overrides  
- avoid deep nesting unless necessary  

---

## Service Design

- use dependency injection exclusively  
- avoid static access patterns  
- keep services small and focused  
- expose clear interfaces where extension is expected  

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
- avoid tightly coupling logic to templates  
- keep UI components reusable  

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

Recommended:

- test generated code paths  
- test configuration behavior  
- test service wiring  

---

## Documentation Requirements

Each package must include:

- clear `README.md`  
- installation instructions  
- configuration options  
- usage examples  
- description of provided makers  

---

## Versioning

- use semantic versioning (SemVer)  
- document breaking changes clearly  
- maintain compatibility within Symfony 8 ecosystem  

---

## Anti-Patterns (Forbidden)

- implicit dependency installation  
- cross-package entity leakage  
- monolithic packages  
- runtime behavior hidden in recipes  
- non-deterministic generators  
- global state or static access  
- mixing identity and feature concerns  

---

## Design Checklist

Before releasing a package, verify:

- does it have a clear, bounded responsibility?  
- are dependencies explicit?  
- does it avoid redefining application structure?  
- does it integrate cleanly with identity packages?  
- does it provide deterministic makers if needed?  
- does it follow Symfony best practices?  
- is it testable and documented?  

---

## Guiding Principle

> A Symfony-X package must be predictable, composable, and bounded.

If a package introduces ambiguity, implicit behavior, or structural drift, it is not aligned with Symfony-X.

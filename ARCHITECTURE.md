
More precisely:

1. `skeleton`
2. `recipes`, `maker`, `dev-tools`
3. identity packages (`ui`, `api`, `mcp`)
4. feature packages (`user`, `dashboard`, etc.)

### Constraints

- lower layers must not depend on higher layers
- identity must not depend on feature modules
- core tools must not depend on application features
- feature modules may depend on identity only when required
- Buffer integrates externally and is not part of the dependency chain

---

## Deterministic Generation Model

Symfony-X replaces ad-hoc scaffolding with **deterministic generation**.

### Process

1. intent is identified (human or AI)
2. intent is mapped to a maker command
3. generator produces structure based on package contract
4. developer or agent refines within constraints

### Properties

- predictable output
- enforced naming and placement
- package-aligned structure
- test scaffolding generated alongside code

### Rule

All structural code creation must occur through maker commands.

---

## Recipes Model

Recipes automate installation and configuration.

### Responsibilities

- register services
- configure bundles
- add routes
- set environment defaults

### Constraints

- recipes must not contain business logic
- recipes must not override package ownership
- recipes must remain idempotent and predictable

---

## Identity Enforcement

Identity must be **explicit and visible**.

### Rule

No feature package may silently define application nature.

### Exception

Feature packages may provide **installation profiles** that:

- require identity packages explicitly
- clearly communicate what is being installed

Example:
- `symfony-x/user` may offer a “web-app” profile that installs `symfony-x/ui`

---

## Admin vs Control Plane

### `symfony-x/admin`

- application-local
- privileged user interface
- operates on application state
- part of the deployed app

### `Buffer`

- external control-plane system
- operates across applications and environments
- enforces architecture and policy
- coordinates AI and generation workflows

### Rule

These must remain separate concerns.

---

## Observability

Packages should provide visibility into their behavior.

### Mechanism

- Symfony Profiler `DataCollector`s

### Examples

- UI state inspector (`ui`)
- security decisions (`user`)
- AI traffic logs (`mcp`)
- system activity (`admin`)

### Rule

Observability should reflect meaningful runtime behavior, not noise.

---

## AI Interaction Model

Symfony-X is designed for AI-assisted development.

### Principle

AI does not write arbitrary code.

### Workflow

1. determine intent
2. map to command
3. generate deterministic structure
4. refine within constraints

### Enforcement

- maker commands define structure
- dev-tools enforce correctness
- Buffer validates system-wide integrity

---

## Architectural Constraints Summary

- minimal foundation
- explicit identity selection
- composable features only
- deterministic generation required
- recipes handle wiring only
- no hidden dependencies
- no implicit structure changes
- governance is enforced, not optional
- control plane is external

---

## Guiding Principle

> Symfony-X is a constrained system designed to produce predictable, scalable, and composable applications.

The system limits structure so that applications remain flexible, maintainable, and safe to evolve.

# Symfony-X Architecture Enforcement

## Purpose

This document defines how Symfony-X architectural rules are **actively enforced**, not merely documented.

It connects:

- Constraints
- Package Guidelines
- Maker Contract
- Command Map
- Generation Pipeline
- Buffer

Into a **cohesive enforcement system**.

---

## Core Principle

Architecture is enforced automatically.

If a rule depends on human discipline alone, it is insufficient.

---

## Enforcement Layers

Symfony-X uses three enforcement layers:

1. Local Enforcement (Dev Tools)
2. Structural Enforcement (Makers & Pipeline)
3. Global Enforcement (Buffer)

Each layer provides increasing levels of control.

---

## 1. Local Enforcement (Dev Tools)

### Components

- PHPStan
- PHP-CS-Fixer
- architecture lint rules
- custom Symfony-X validators

### Responsibilities

- enforce coding standards
- detect structural violations
- validate dependency direction
- enforce naming and namespace rules

---

### Enforced Rules

Dev Tools must enforce:

- no invalid namespace usage
- no forbidden dependencies
- no cross-package leakage
- configuration correctness
- code quality standards

### SXUC-Relevant Enforcement

Where supported by tooling, Dev Tools should validate:

- illegal preset/runtime coupling
- forbidden UI architecture drift in SXUC-owned structure
- package-local violations of documented SXUC boundaries
- missing required generated structure for SXUC patterns where deterministic rules exist

---

### Failure Model

If Dev Tools fail:

- commit should be blocked
- CI must fail
- merge must be prevented

---

## 2. Structural Enforcement (Makers & Pipeline)

### Components

- Maker commands
- Generation Pipeline
- Command Map

---

### Responsibilities

- enforce deterministic structure
- control file placement
- enforce package ownership
- prevent freeform structural generation

---

### Enforced Rules

- structural code must be generated via Makers
- file locations must be predictable
- naming conventions must be enforced
- package boundaries must be respected

### SXUC Structural Enforcement

For SXUC-owned structure, Makers and pipeline should enforce:

- async-aware scaffolding
- contract-safe preset handling
- governed template/component placement
- valid UI identity ownership

---

### Hard Constraint

If structure is created outside Makers, it is considered invalid.

---

### Pipeline Enforcement

The pipeline ensures:

- intent must be mapped before execution
- package ownership must be resolved
- validation must occur before and after generation

For SXUC, pipeline enforcement should also ensure:

- UI-first identity is explicit
- preset selection is explicit where applicable
- generated structure does not violate Turbo/Mercure invariants

---

## 3. Global Enforcement (Buffer)

### Components

- Validation Engine
- Command Orchestrator
- Intent Store
- Audit Log

---

### Responsibilities

- enforce cross-package rules
- validate full system composition
- track intent vs implementation
- coordinate AI agents
- provide audit and traceability

---

### Enforced Rules

Buffer must enforce:

- dependency direction correctness
- identity/feature alignment
- compatibility across packages
- adherence to constraints
- proper use of Makers and pipeline

### SXUC-Relevant Buffer Enforcement

Where Buffer understands SXUC semantics, it should validate:

- explicit UI identity installation
- explicit preset resolution
- forbidden transport redefinition by feature packages
- drift away from the documented immediate/deferred async UX split

---

### Authority Level

Buffer operates as the **highest authority** in the system.

It may:

- block invalid operations
- reject command execution
- flag architectural violations
- require corrective actions

---

## Enforcement Flow

The full enforcement model:

1. intent declared
2. intent mapped to command
3. local validation (Dev Tools)
4. global validation (Buffer, if available)
5. command execution (Maker)
6. post-validation (Dev Tools + Buffer)
7. audit recorded

---

## CI/CD Enforcement

### Required Checks

All repositories must enforce:

- static analysis (PHPStan)
- coding standards (CS Fixer)
- test execution
- architecture validation

---

### Merge Rules

Pull requests must not be merged if:

- any enforcement check fails
- dependency violations exist
- structural inconsistencies are detected
- required Makers are missing

---

## Repository-Level Enforcement

### Tier A (Core)

- strictest enforcement
- multiple approvals required
- architecture review mandatory

---

### Tier B (Identity)

- strong enforcement
- contract stability required
- async-runtime contract changes require architectural review for `symfony-x/ui`

---

### Tier C (Features)

- moderate enforcement
- must respect boundaries
- must not redefine identity-owned runtime behavior

---

### Tier P (Buffer)

- highest enforcement
- security and governance critical

---

## AI Enforcement

AI agents must operate within constraints.

### Required Behavior

AI must:

- use Command Map
- follow Generation Pipeline
- use Makers for structure
- respect package boundaries

---

### Forbidden Behavior

AI must not:

- generate structural code directly
- bypass validation
- introduce hidden dependencies
- mutate system outside pipeline
- invent alternate SXUC architecture for UI-first apps

---

## Violation Handling

When a violation occurs:

1. detection (Dev Tools or Buffer)
2. rejection of operation
3. clear error reporting
4. required correction before retry

---

## Observability

Enforcement must be visible.

### Required Signals

- validation failures
- command execution logs
- dependency violations
- policy violations
- architecture drift alerts

### SXUC Signals

Where supported, enforcement and observability should surface:

- identity installation state
- preset selection state
- SXUC contract violations
- generator compliance for async-aware UI structure

---

## Guiding Principle

An architecture rule that cannot be validated is weaker than it appears.

Symfony-X enforcement exists to make architecture concrete, testable, and difficult to drift from silently.

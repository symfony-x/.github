# Symfony-X Maker Contract

## Purpose

This document defines the rules, expectations, and guarantees for all Maker commands within the Symfony-X ecosystem.

Makers are the only approved mechanism for generating application structure.

They exist to:

- eliminate structural ambiguity
- enforce architectural constraints
- ensure deterministic output
- provide a stable interface for both developers and AI agents

---

## Core Principle

Makers define structure. Humans and AI refine behavior.

No code that affects application structure should be created manually if a Maker exists or should exist.

---

## Maker Responsibilities

A Maker command must:

- generate code deterministically
- enforce correct file placement
- enforce naming conventions
- align with package boundaries
- produce valid, runnable code
- integrate with Symfony configuration automatically where applicable

---

## Determinism Requirement

### Rule

Given the same inputs, a Maker must always produce the same output.

### Constraints

- no randomness
- no environment-dependent structure
- no implicit variation
- no hidden side effects

### Allowed Inputs

- explicit CLI arguments
- interactive prompts (deterministic choices only)
- configuration values

---

## Structural Ownership

Each package owns its own Makers.

Examples:

- symfony-x/user → `make:x-user`, `make:x-user-voter`
- symfony-x/dashboard → `make:x-dashboard-widget`
- symfony-x/ui` → `make:sxuc:component`, `make:sxuc:live-component`

### Rule

A Maker must not generate code outside its package's defined domain.

---

## Naming Conventions

Makers must follow a consistent naming pattern.

General pattern:

- `make:x-<package>-<concept>` for Symfony-X package Makers
- package-specific explicit naming is allowed when the package contract defines it clearly

Examples:

- `make:x-user`
- `make:x-user-voter`
- `make:x-dashboard-widget`
- `make:sxuc:component`
- `make:sxuc:layout`

### Rules

- avoid ambiguity
- include package context
- be descriptive and explicit

---

## File Placement Rules

Generated files must:

- be placed in predictable directories
- match Symfony best practices
- match package-specific structure

Example:

- entities → `src/Entity/`
- services → `src/Service/`
- voters → `src/Security/Voter/`

### Rule

No Maker may write to arbitrary or dynamic paths.

---

## Code Quality Guarantees

Generated code must:

- pass PHPStan (configured level)
- conform to PHP-CS-Fixer rules
- follow Symfony best practices
- include correct namespaces
- include type hints and return types

---

## Test Scaffolding

### Requirement

Makers should generate corresponding tests when applicable.

Examples:

- service → unit test
- controller → functional test skeleton
- entity → basic test scaffold

### Rule

Generated tests must be runnable and valid.

---

## Configuration Integration

Makers may:

- register services
- update configuration
- integrate with existing Symfony config

### Constraints

- must not overwrite user modifications blindly
- must be idempotent where possible
- must preserve user-defined configuration

---

## Recipe Interaction

If a package provides recipes:

- Makers should assume the recipe has already configured the environment
- Makers must not duplicate recipe behavior

---

## Idempotency

### Rule

Running the same Maker twice must not:

- corrupt files
- duplicate definitions
- break application state

### Expected Behavior

- detect existing structures
- prompt user for overwrite or skip
- safely merge when applicable

---

## Error Handling

Makers must:

- fail clearly and early
- provide actionable error messages
- never leave the system in a broken state

---

## AI Interaction Model

Makers are the primary interface for AI agents.

### Workflow

1. AI determines intent
2. AI maps intent to a Maker command
3. Maker generates structure
4. AI refines implementation

### Rule

AI must not bypass Makers for structural code generation.

---

## SXUC Maker Requirements

If a Maker belongs to `symfony-x/ui`, it must generate **async-aware structure**.

### SXUC Principle

SXUC Makers must encode the governed async UX contract in structure, not leave it to ad hoc manual convention.

### Generated SXUC output should include, where applicable

- predictable component/template placement
- Turbo-oriented template boundaries
- clear DOM target conventions
- pending/completed/error placeholders where relevant
- Stimulus attachment points where relevant
- Mercure/deferred update readiness where relevant
- explicit preset-aware output when preset selection affects presentation

### SXUC Makers must not

- hide async architecture behind undocumented magic
- silently invent alternate transport models
- generate output that conflicts with Turbo/Mercure invariants
- bind output to one preset unless explicitly requested

---

## Extensibility

Makers should:

- expose extension points where appropriate
- allow additional options via arguments
- remain backward compatible

---

## Versioning

Changes to Maker behavior must follow:

- semantic versioning
- clear documentation of breaking changes
- migration guidance when necessary

---

## Anti-Patterns (Forbidden)

- generating incomplete or non-runnable code
- writing files outside defined structure
- embedding business logic in generators
- modifying unrelated parts of the application
- relying on hidden assumptions
- non-deterministic output
- silent overwrites of user code
- generating SXUC UI structure that ignores async identity constraints

---

## Design Checklist

Before implementing or modifying a Maker:

- is the output deterministic?
- is file placement predictable?
- does it align with package boundaries?
- does it enforce naming conventions?
- does it generate valid, runnable code?
- does it integrate cleanly with Symfony?
- does it support AI-driven workflows?
- if it belongs to SXUC, does it generate async-aware defaults?

---

## Guiding Principle

Makers are the contract between intent and structure.

If a Maker introduces ambiguity, inconsistency, or unpredictability, it violates the Symfony-X architecture.

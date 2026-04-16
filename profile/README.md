# Symfony-X

Symfony-X is a constraint-driven architecture for building Symfony applications through explicit composition.

It replaces scaffolding and implicit structure with deterministic, install-driven system design.

---

## Why Symfony-X Exists

Modern Symfony applications tend to degrade over time.

Even well-structured projects eventually accumulate:

- inconsistent architecture
- blurred boundaries between concerns
- duplicated patterns across teams and repositories
- increasing difficulty introducing new features safely
- drift caused by ad-hoc changes and AI-generated code

Symfony-X exists to solve this problem at the architectural level.

Instead of relying on convention or discipline alone, Symfony-X enforces:

- explicit system composition
- strict separation of concerns
- deterministic structure
- predictable evolution over time

---

## The Core Idea

> Applications are not generated — they are composed.

A Symfony-X application is built by installing packages that each have a clearly defined role.

There is no hidden scaffolding, no implicit setup, and no ambiguity about how the system is constructed.

---

## The Model

Symfony-X applications are built from three distinct concerns:

### Identity (What the app *is*)

Defines how the system behaves and communicates.

Examples:
- `symfony-x/ui` (SXUC)
- `symfony-x/api`
- `symfony-x/mcp`

Identity determines:
- interaction model
- runtime behavior
- system expectations

---

### Capabilities (What the app *can do*)

Reusable, bounded functionality.

Examples:
- `symfony-x/user`
- `symfony-x/user-oauth`
- billing, integrations, domain modules

Capabilities:
- do not define application structure
- do not assume identity
- remain portable across applications

---

### Application Structure (How the app is experienced)

Some packages provide higher-level application structure built on identity.

Examples:
- `symfony-x/dashboard`

These packages:

- depend on identity
- assemble capabilities into a cohesive system
- provide a usable application surface out of the box

They define how the system is experienced, not what the system fundamentally is.

---

## Example

```bash
composer require symfony-x/ui
composer require symfony-x/dashboard
composer require symfony-x/user
```

This produces:

- an SXUC-driven UI application
- a working operational dashboard
- a user system ready for integration

The application emerges from composition — not from generated code.

---

## System Architecture

Symfony-X is built on a layered model:

- Foundation → minimal Symfony baseline  
- Identity → defines application type  
- Capabilities → provide reusable functionality  
- Application Structure → defines system surface  
- Governance → enforces architectural correctness  

---

## Governance

Symfony-X enforces architecture through:

- deterministic code generation (Makers)
- architectural validation (Buffer)
- constraint enforcement (CI and tooling)

This ensures that invalid structures cannot be introduced.

---

## What This Enables

Symfony-X makes it possible to:

- build applications with deterministic architecture
- evolve systems safely over time
- integrate AI-assisted development without structural drift
- reuse capabilities across multiple application types
- maintain clear separation between system concerns

---

## What Symfony-X Is Not

Symfony-X is not:

- a starter template
- a bundle collection
- a UI framework
- a scaffolding tool

It does not generate applications.

Instead, it defines how applications are **constructed and maintained**.

---

## Design Principles

Symfony-X is built on a small set of strict principles:

- Identity must always be explicit
- Capabilities must remain portable
- Application Structure must remain additive
- System behavior must be deterministic
- Architecture must be enforceable

---

## Philosophy

Symfony-X treats architecture as a first-class concern.

Instead of relying on discipline to maintain structure, it encodes structure into the system itself.

The result is:

> a system that remains understandable, predictable, and stable — even as it evolves

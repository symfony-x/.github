# Symfony-X

Symfony-X is a constraint-driven architecture for building Symfony applications through explicit composition.

It replaces scaffolding and implicit structure with deterministic, install-driven system design.

---

## The Problem

Modern Symfony applications drift because:

- structure is generated once, then diverges
- features blur into architecture
- UI, API, and domain concerns mix over time
- AI-generated code introduces inconsistency

Symfony-X solves this by making architecture enforceable.

---

## The Model

Applications are built from three layers:

### 1. Identity (What the app *is*)
Defines the interaction model.

Examples:
- symfony-x/ui (SXUC)
- symfony-x/api
- symfony-x/mcp

---

### 2. Capabilities (What the app *can do*)
Reusable, bounded functionality.

Examples:
- user systems
- billing
- integrations

Capabilities:
- do not define structure
- do not assume identity
- remain portable

---

### 3. Application Structure
Some packages provide higher-level application structure built on identity.

These packages:
- depend on identity
- assemble capabilities
- provide a usable system out of the box

Example:
- symfony-x/dashboard

---

## Example

```bash
composer require symfony-x/ui
composer require symfony-x/dashboard
composer require symfony-x/user
```

This produces:

- an SXUC-driven UI application
- a working dashboard surface
- a user system

---

## Core Principle

> Applications are not generated — they are composed.

---

## SXUC (Symfony-X UI Component)

SXUC provides an async-first UI model:

- Turbo handles immediate interaction
- Mercure propagates state asynchronously
- UI reflects system state as it evolves

---

## Why This Matters

Symfony-X enables:

- deterministic architecture
- AI-safe code generation
- composable system evolution
- strict separation of concerns

---

## What Symfony-X Is Not

- not a starter template
- not a bundle collection
- not a UI kit

It is:

> a system for enforcing architectural correctness over time

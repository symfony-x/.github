# Symfony-X Maker Contract

This document defines the contract for Makers within Symfony-X.

Makers are responsible for generating deterministic structure while preserving architectural integrity.

---

## Purpose

Makers exist to:

- generate consistent code
- enforce conventions
- reduce manual implementation errors

They operate within the system — not above it.

---

## Scope

Makers generate structure inside an already-defined system.

They do not:

- define application identity
- define application structure
- determine system architecture

Architecture is established through composition, not generation.

---

## Allowed Responsibilities

Makers MAY:

- generate entities, controllers, and components
- scaffold capability-level structures
- enforce naming and structural conventions
- integrate with existing system configuration

---

## Forbidden Responsibilities

Makers MUST NOT:

- define or install Identity packages
- define or install Application Structure packages
- introduce implicit dependencies
- bypass architectural constraints

---

## Determinism Requirement

Makers MUST produce:

- predictable output
- repeatable structure
- consistent conventions

The same input must always produce the same result.

---

## Constraint Alignment

All generated code must:

- comply with architectural constraints
- respect dependency rules
- preserve system boundaries

Makers must never generate code that violates the system model.

---

## Integration with the System

Makers operate alongside:

- Command Map (intent resolution)
- Constraints (rule enforcement)
- Buffer (validation layer)

They must align with all three.

---

## Core Principle

> Makers generate valid structure, not system architecture.

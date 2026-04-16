# Symfony-X Generation Pipeline

This document defines the flow for generating structure within a Symfony-X application.

The pipeline ensures that all generated code is consistent, deterministic, and aligned with system architecture.

---

## Core Principle

> Generation creates structure within the system; it does not define the system.

Architecture is established through composition before generation occurs.

---

## Pipeline Overview

The generation pipeline follows a strict sequence:

1. Intent Resolution
2. Architecture Validation
3. Structure Generation
4. Validation and Integration

---

## 1. Intent Resolution

User intent is interpreted using the Command Map.

The system determines:

- whether to install an Identity package
- whether to install a Capability package
- whether to install an Application Structure package
- whether to invoke a Maker

No generation occurs at this stage.

---

## 2. Architecture Validation

Before generation:

- system architecture must be valid
- package classification must be correct
- dependency rules must be satisfied

Invalid states must be rejected before proceeding.

---

## 3. Structure Generation

Makers generate deterministic structure within the system.

This includes:

- entities
- controllers
- components
- configuration scaffolding

Generation is constrained by:

- Maker Contract
- architectural constraints
- system boundaries

---

## 4. Validation and Integration

After generation:

- Buffer validates structural correctness
- constraints are re-evaluated
- integration with existing system is verified

Invalid generation must be rejected.

---

## Separation of Concerns

The pipeline enforces a strict separation:

- Composition → defines the system
- Generation → builds within the system

These must never be conflated.

---

## Determinism

The pipeline must produce:

- predictable results
- consistent structure
- repeatable outcomes

The same intent must produce the same system state.

---

## Core Rule

> If generation would produce an invalid structure, it must not proceed.

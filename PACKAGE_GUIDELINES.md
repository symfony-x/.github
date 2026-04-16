# Symfony-X Package Guidelines

This document defines how packages should be designed within Symfony-X.

The goal is to ensure consistency, composability, and architectural correctness.

---

## Package Types

Symfony-X defines three primary types of packages:

### Identity Packages

Define what the application *is*.

Examples:
- symfony-x/ui
- symfony-x/api
- symfony-x/mcp

Identity packages:

- define interaction model
- define runtime behavior
- must remain explicit

---

### Capability Packages

Provide reusable functionality.

Examples:
- user system
- billing
- integrations

Capability packages:

- must be independent of identity
- must be portable across applications
- must focus on a single responsibility

Capability packages MUST NOT:

- define application structure
- assume a specific identity
- depend on Application Structure packages

---

### Application Structure Packages

Provide higher-level application structure built on identity.

Examples:
- symfony-x/dashboard

Application Structure packages:

- depend on identity
- may assemble multiple capabilities
- provide a usable application surface

Application Structure packages MUST:

- remain additive
- not redefine application identity

Application Structure packages MUST NOT:

- be treated as reusable capabilities
- introduce implicit system behavior

---

## Design Principles

All packages must follow these principles:

- explicit dependencies
- single responsibility
- deterministic behavior
- composability

---

## Dependency Rules

Allowed:

- Application Structure → Identity
- Application Structure → Capability
- Capability → Foundation
- Identity → Foundation

Forbidden:

- Capability → Application Structure
- Identity → Application Structure

---

## Classification Guide

When creating a package, ask:

### Does it define how the system behaves?
→ Identity

### Does it add reusable functionality?
→ Capability

### Does it assemble a usable application surface?
→ Application Structure

---

## Anti-Patterns

The following are invalid:

- Capability packages that define UI structure
- Capability packages that assume a specific identity
- Application Structure packages treated as reusable modules
- Packages that mix multiple responsibilities
- Packages that introduce implicit dependencies

---

## Core Rule

> A package must have a single, clear role within the system.

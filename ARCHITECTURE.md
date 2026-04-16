# Symfony-X Architecture

Symfony-X is a constraint-driven modular architecture built on explicit layering and deterministic composition.

---

## Layer Model

### 1. Foundation
Minimal Symfony skeleton.

Contains:
- Kernel
- Config baseline
- No UI
- No DB
- No identity

---

### 2. Identity Layer
Defines the nature of the application.

Examples:
- UI (SXUC)
- API
- MCP

Responsibilities:
- Interaction model
- Runtime communication pattern

---

### 3. Capability Layer
Provides isolated, reusable functionality.

Examples:
- User system
- OAuth integration
- Billing

Characteristics:
- Independent of identity
- Portable across applications
- Bounded responsibility

---

### 4. Composition Layer
Builds application surfaces by assembling identity and capabilities.

Examples:
- Dashboard

Responsibilities:
- Provide default application structure
- Deliver ready-to-use UI or API surface
- Assemble capabilities into cohesive experience

Constraints:
- Must depend on identity explicitly
- Must not redefine identity implicitly
- Must remain additive

---

### 5. Governance Layer
Controls correctness and consistency.

Components:
- Recipes
- MakerBundle
- Buffer
- Dev tools

---

## Dependency Rules

Allowed:
- Composition → Identity
- Composition → Capability
- Capability → Foundation
- Identity → Foundation

Forbidden:
- Capability → Composition
- Identity → Composition
- Foundation → Anything

---

## Installation Model

Applications are built through composition:

composer require symfony-x/ui  
composer require symfony-x/dashboard  
composer require symfony-x/user  

---

## Core Principle

Symfony-X is not scaffold-driven.

It is:

A layered composition system where application behavior emerges from explicit package installation.

# Symfony-X Architecture

Symfony-X is a constraint-driven modular architecture built on explicit layering and deterministic composition.

It is designed to prevent architectural drift by enforcing clear boundaries between system layers and eliminating implicit behavior.

---

## Philosophy

Traditional Symfony applications tend to degrade over time due to:

- implicit structure introduced by scaffolding
- unclear separation between application concerns
- features gradually redefining system behavior
- increasing difficulty maintaining consistency

Symfony-X addresses this by:

- enforcing explicit system composition
- separating identity, capability, and structure concerns
- making architecture deterministic and inspectable

---

## Layer Model

### 1. Foundation
The minimal baseline of a Symfony application.

Contains:
- Kernel
- Configuration baseline

Does NOT contain:
- UI
- Persistence
- Identity
- Business logic

This layer exists purely to support higher-level composition.

---

### 2. Identity Layer
Defines what the application *is*.

Examples:
- UI (SXUC)
- API
- MCP

Responsibilities:
- interaction model
- runtime communication pattern
- system behavior expectations

Identity determines how the system communicates and evolves.

---

### 3. Capability Layer
Provides isolated, reusable functionality.

Examples:
- user systems
- OAuth integration
- billing

Characteristics:
- independent of identity
- portable across applications
- bounded responsibility

Capabilities MUST:
- not define application structure
- not assume identity implicitly
- not alter system behavior outside their scope

---

### 4. Application Structure Layer
Provides higher-level application structure built on identity.

Examples:
- dashboard

These packages:

- depend on an Identity Package
- may assemble multiple capabilities
- provide a usable application surface

They define how the system is experienced, not what the system fundamentally is.

---

## Application Surface

An application surface is a user-facing system assembled by an Application Structure package.

Examples:
- dashboard UI
- operational interfaces
- administrative environments

Application surfaces:
- emerge from composition
- do not define identity
- do not replace capabilities

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
- Foundation → Any higher layer

These rules ensure that:

- structure does not leak downward
- capabilities remain reusable
- identity remains explicit

---

## Behavioral Model

Under UI identity (SXUC):

- Turbo handles immediate interaction
- Mercure propagates state asynchronously

This establishes an async-first system model:

- immediate user feedback
- deferred state resolution
- eventual consistency

This model ensures that the user interface reflects system state as it evolves, rather than blocking on synchronous operations.

---

## Installation Model

Applications are composed explicitly through package installation:

```bash
composer require symfony-x/ui
composer require symfony-x/dashboard
composer require symfony-x/user
```

Result:

- Identity defines application type
- Application Structure defines application surface
- Capabilities define functionality

The final system is the result of composition, not generation.

---

## Constraints

- Identity must always be explicit
- Capabilities must remain portable
- Application Structure must remain additive
- No package may implicitly redefine application type

Violating these constraints introduces architectural ambiguity and must be avoided.

---

## Core Principle

> System behavior emerges from explicit composition, not generated structure.

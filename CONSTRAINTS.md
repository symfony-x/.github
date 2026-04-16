# Symfony-X Constraints

This document defines the rules that enforce architectural correctness within Symfony-X.

Constraints are mandatory and must not be violated.

---

## Identity Constraints

- Identity MUST be explicitly installed
- Identity MUST define the application interaction model
- Identity MUST NOT depend on Application Structure
- Identity MUST NOT be implicitly inferred

---

## Capability Constraints

- Capabilities MUST be independent of identity
- Capabilities MUST be portable across applications
- Capabilities MUST NOT define application structure
- Capabilities MUST NOT assume a specific identity
- Capabilities MUST NOT depend on Application Structure

---

## Application Structure Constraints

- Application Structure MUST depend on an Identity
- Application Structure MAY depend on Capabilities
- Application Structure MUST remain additive
- Application Structure MUST NOT redefine application identity
- Application Structure MUST NOT introduce implicit system behavior

---

## Dependency Constraints

Allowed:

- Application Structure → Identity
- Application Structure → Capability
- Capability → Foundation
- Identity → Foundation

Forbidden:

- Capability → Application Structure
- Identity → Application Structure
- Foundation → Any higher layer

---

## Composition Constraints

- Applications MUST be constructed through explicit composition
- Composition MUST NOT introduce hidden dependencies
- Composition MUST remain inspectable and deterministic

---

## Recipe Constraints

- Recipes MUST only configure applications
- Recipes MUST NOT define system behavior
- Recipes MUST NOT introduce architectural ambiguity

---

## Maker Constraints

- Makers MUST generate deterministic structure
- Makers MUST enforce architectural conventions
- Makers MUST NOT introduce implicit behavior

---

## Buffer Constraints

- Buffer MUST validate architectural correctness
- Buffer MUST detect constraint violations
- Buffer MUST NOT modify system behavior

---

## System Integrity Constraints

- System structure MUST remain explicit
- System behavior MUST remain predictable
- Architectural boundaries MUST NOT be violated
- No component may introduce ambiguity into the system

---

## Anti-Drift Principle

Any change that:

- obscures system structure
- weakens constraints
- introduces implicit behavior

MUST be rejected.

---

## Core Rule

> If a system cannot be reasoned about deterministically, it is invalid.

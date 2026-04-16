# Symfony-X Architecture Enforcement

This document defines how architectural constraints are enforced within Symfony-X.

Enforcement ensures that invalid system structures cannot be introduced.

---

## Enforcement Principle

> Architecture must be enforceable, not optional.

Any change that violates system constraints must be detected and rejected.

---

## Enforcement Layers

Symfony-X enforces architecture through multiple layers:

### 1. Static Validation

Automated checks validate:

- package classification (Identity, Capability, Application Structure)
- dependency direction
- structural consistency

---

### 2. CI Enforcement

Continuous Integration must:

- reject invalid dependencies
- reject misclassified packages
- detect architectural violations before merge

---

### 3. Maker Enforcement

Makers must:

- generate valid structure only
- enforce architectural conventions
- prevent invalid code generation

Makers MUST NOT:

- create application structure implicitly
- define identity
- bypass architectural constraints

---

### 4. Buffer Validation

The Buffer acts as an architectural validation layer.

It must:

- detect constraint violations
- validate system composition
- prevent structural drift

The Buffer MUST validate:

- Capability does not define application structure
- Application Structure does not redefine identity
- dependency rules are respected

---

## Enforced Constraints

The following must be enforced across all repositories:

### Identity

- must be explicit
- must not depend on Application Structure

---

### Capability

- must remain independent
- must not define application structure
- must not depend on Application Structure

---

### Application Structure

- must depend on Identity
- may depend on Capability
- must remain additive
- must not redefine identity

---

### Dependency Rules

Allowed:

- Application Structure → Identity
- Application Structure → Capability
- Capability → Foundation
- Identity → Foundation

Forbidden:

- Capability → Application Structure
- Identity → Application Structure

---

## Violation Handling

When a violation is detected:

- the change MUST be rejected
- the violation MUST be reported clearly
- corrective action MUST be required

Violations must never be silently accepted.

---

## Drift Detection

The system must continuously detect:

- misclassified packages
- invalid dependencies
- implicit structural changes

Drift must be treated as a failure condition.

---

## Core Rule

> If a change cannot be validated against the architecture, it must not be accepted.

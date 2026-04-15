# Symfony-X Constraints

## Purpose

This document defines the **non-negotiable constraints** of the Symfony-X ecosystem.

These rules exist to:

- prevent architectural drift  
- enforce determinism  
- maintain composability  
- ensure AI-safe operation  
- preserve long-term system integrity  

If a design, package, or change violates these constraints, it is not Symfony-X compliant.

---

## Core Principle

Constraints are enforced, not suggested.

Symfony-X is a constrained system by design.

---

## 1. Foundation Constraints

### Rule 1.1 — Skeleton Must Remain Minimal

`symfony-x/skeleton` must not include:

- UI frameworks  
- database layers  
- authentication systems  
- feature modules  
- application-specific logic  

### Rule 1.2 — No Implicit Behavior

The foundation must not:

- auto-enable features  
- assume application type  
- include hidden dependencies  

---

## 2. Identity Constraints

### Rule 2.1 — Identity Must Be Explicit

Application identity must be installed explicitly.

Forbidden:

- implicit identity installation  
- feature packages silently defining identity  

---

### Rule 2.2 — Identity Is Not a Feature

Identity packages must not:

- contain business logic  
- behave like feature modules  
- absorb domain-specific functionality  

---

### Rule 2.3 — Identity Must Remain Bounded

Identity packages must:

- define integration patterns  
- not expand into unrelated domains  

---

## 3. Feature Constraints

### Rule 3.1 — Features Must Be Bounded

Feature packages must:

- have a clearly defined domain  
- avoid cross-domain responsibilities  

---

### Rule 3.2 — No Structural Redefinition

Feature packages must not:

- redefine application architecture  
- override identity behavior  
- mutate global structure  

---

### Rule 3.3 — Explicit Dependencies Only

All dependencies must be declared.

Forbidden:

- hidden dependencies  
- implicit installs  
- runtime assumptions  

---

## 4. Dependency Constraints

### Rule 4.1 — Dependency Direction Is Fixed

Allowed:

Foundation → Governance → Identity → Features

Forbidden:

- Identity → Feature  
- Core → Feature  
- cyclic dependencies  

---

### Rule 4.2 — No Cross-Boundary Leakage

Packages must not:

- expose internal entities across boundaries  
- tightly couple to unrelated packages  

---

## 5. Generation Constraints

### Rule 5.1 — Structural Code Must Be Generated

All structural code must be created via Makers.

Forbidden:

- manual creation of structural components when a Maker exists or should exist  
- bypassing package generation rules  

---

### Rule 5.2 — Determinism Is Required

Generators must:

- produce identical output for identical input  
- avoid randomness  
- avoid environment-specific variation  

---

### Rule 5.3 — No Freeform Generation

AI and developers must not:

- invent structure  
- create files outside defined patterns  
- bypass Maker contracts  

---

## 6. Recipe Constraints

### Rule 6.1 — Recipes Wire Only

Recipes may:

- configure services  
- register routes  
- set defaults  

Recipes must not:

- contain business logic  
- override package ownership  
- introduce hidden behavior  

---

### Rule 6.2 — Recipes Must Be Safe

Recipes must:

- be idempotent  
- not overwrite user configuration blindly  
- produce predictable results  

---

## 7. Buffer Constraints

### Rule 7.1 — Buffer Is External

Buffer must:

- remain a separate system  
- not be required at runtime  
- not be embedded into applications  

---

### Rule 7.2 — No Runtime Coupling

Applications must not:

- depend on Buffer for execution  
- fail if Buffer is unavailable  

---

### Rule 7.3 — Buffer Governs, Not Executes

Buffer must not:

- replace application logic  
- act as a feature module  

---

## 8. AI Constraints

### Rule 8.1 — Intent Must Be Mapped First

AI must:

- identify intent  
- resolve ownership  
- map to commands  

Before generating code.

---

### Rule 8.2 — No Architecture Invention

AI must not:

- invent missing structure  
- bypass Makers  
- create implicit dependencies  

---

### Rule 8.3 — Structure Before Behavior

AI may:

- refine logic  

Only after:

- structure has been generated deterministically  

---

## 9. Configuration Constraints

### Rule 9.1 — Configuration Must Be Namespaced

All package configuration must:

- be scoped to the package  
- avoid global pollution  

---

### Rule 9.2 — No Hidden Defaults

Configuration must:

- be explicit  
- be documented  
- avoid silent behavior changes  

---

## 10. Observability Constraints

### Rule 10.1 — Signal Over Noise

Profiler and observability tools must:

- provide meaningful insight  
- avoid excessive or irrelevant data  

---

### Rule 10.2 — No Hidden State

Runtime behavior must be observable and traceable.

---

## 11. Repository Constraints

### Rule 11.1 — One Responsibility Per Repo

Repositories must:

- represent a single bounded concept  
- not combine unrelated functionality  

---

### Rule 11.2 — No Premature Splitting

Do not create new repositories unless:

- the boundary is real  
- reuse is proven  
- governance requires separation  

---

## 12. Anti-Patterns (Strictly Forbidden)

- implicit dependency installation  
- hidden architecture changes  
- non-deterministic generators  
- cross-package domain leakage  
- monolithic “do everything” packages  
- embedding control-plane logic in application code  
- bypassing validation  
- manual structural generation where Makers should exist  
- vague or undefined package boundaries  

---

## 13. Enforcement Model

Constraints are enforced through:

- Maker commands (structure control)  
- dev-tools (static analysis and linting)  
- recipes (controlled installation)  
- Buffer (control-plane validation)  

Violations must be:

- rejected during review  
- flagged by tooling  
- blocked by governance systems  

---

## 14. Design Validation Checklist

Before introducing a change, verify:

- does it violate dependency direction?  
- does it introduce implicit behavior?  
- does it bypass Makers?  
- does it break determinism?  
- does it blur identity vs feature boundaries?  
- does it introduce hidden coupling?  
- does it depend on Buffer at runtime?  

If any answer is yes, the change must be rejected or redesigned.

---

## Guiding Principle

Symfony-X is constrained so that systems remain predictable.

If flexibility introduces ambiguity, it is rejected.

Constraints are the foundation of composability.

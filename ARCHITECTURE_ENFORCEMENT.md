# Symfony-X Architecture Enforcement

## Purpose

This document defines how Symfony-X architectural rules are **actively enforced**, not merely documented.

It connects:

- Constraints  
- Package Guidelines  
- Maker Contract  
- Command Map  
- Generation Pipeline  
- Buffer  

Into a **cohesive enforcement system**.

---

## Core Principle

Architecture is enforced automatically.

If a rule depends on human discipline alone, it is insufficient.

---

## Enforcement Layers

Symfony-X uses three enforcement layers:

1. Local Enforcement (Dev Tools)  
2. Structural Enforcement (Makers & Pipeline)  
3. Global Enforcement (Buffer)  

Each layer provides increasing levels of control.

---

## 1. Local Enforcement (Dev Tools)

### Components

- PHPStan  
- PHP-CS-Fixer  
- architecture lint rules  
- custom Symfony-X validators  

### Responsibilities

- enforce coding standards  
- detect structural violations  
- validate dependency direction  
- enforce naming and namespace rules  

---

### Enforced Rules

Dev Tools must enforce:

- no invalid namespace usage  
- no forbidden dependencies  
- no cross-package leakage  
- configuration correctness  
- code quality standards  

---

### Failure Model

If Dev Tools fail:

- commit should be blocked  
- CI must fail  
- merge must be prevented  

---

## 2. Structural Enforcement (Makers & Pipeline)

### Components

- Maker commands  
- Generation Pipeline  
- Command Map  

---

### Responsibilities

- enforce deterministic structure  
- control file placement  
- enforce package ownership  
- prevent freeform structural generation  

---

### Enforced Rules

- structural code must be generated via Makers  
- file locations must be predictable  
- naming conventions must be enforced  
- package boundaries must be respected  

---

### Hard Constraint

If structure is created outside Makers, it is considered invalid.

---

### Pipeline Enforcement

The pipeline ensures:

- intent must be mapped before execution  
- package ownership must be resolved  
- validation must occur before and after generation  

---

## 3. Global Enforcement (Buffer)

### Components

- Validation Engine  
- Command Orchestrator  
- Intent Store  
- Audit Log  

---

### Responsibilities

- enforce cross-package rules  
- validate full system composition  
- track intent vs implementation  
- coordinate AI agents  
- provide audit and traceability  

---

### Enforced Rules

Buffer must enforce:

- dependency direction correctness  
- identity/feature alignment  
- compatibility across packages  
- adherence to constraints  
- proper use of Makers and pipeline  

---

### Authority Level

Buffer operates as the **highest authority** in the system.

It may:

- block invalid operations  
- reject command execution  
- flag architectural violations  
- require corrective actions  

---

## Enforcement Flow

The full enforcement model:

1. intent declared  
2. intent mapped to command  
3. local validation (Dev Tools)  
4. global validation (Buffer, if available)  
5. command execution (Maker)  
6. post-validation (Dev Tools + Buffer)  
7. audit recorded  

---

## CI/CD Enforcement

### Required Checks

All repositories must enforce:

- static analysis (PHPStan)  
- coding standards (CS Fixer)  
- test execution  
- architecture validation  

---

### Merge Rules

Pull requests must not be merged if:

- any enforcement check fails  
- dependency violations exist  
- structural inconsistencies are detected  
- required Makers are missing  

---

## Repository-Level Enforcement

### Tier A (Core)

- strictest enforcement  
- multiple approvals required  
- architecture review mandatory  

---

### Tier B (Identity)

- strong enforcement  
- contract stability required  

---

### Tier C (Features)

- moderate enforcement  
- must respect boundaries  

---

### Tier P (Buffer)

- highest enforcement  
- security and governance critical  

---

## AI Enforcement

AI agents must operate within constraints.

### Required Behavior

AI must:

- use Command Map  
- follow Generation Pipeline  
- use Makers for structure  
- respect package boundaries  

---

### Forbidden Behavior

AI must not:

- generate structural code directly  
- bypass validation  
- introduce hidden dependencies  
- mutate system outside pipeline  

---

## Violation Handling

When a violation occurs:

1. detection (Dev Tools or Buffer)  
2. rejection of operation  
3. clear error reporting  
4. required correction before retry  

---

## Observability

Enforcement must be visible.

### Required Signals

- validation failures  
- command execution logs  
- dependency violations  
- audit history  

---

## Progressive Enforcement Model

Symfony-X may operate in stages:

### Stage 1 — Local Only

- Dev Tools enforcement  
- manual discipline  

---

### Stage 2 — Structured

- Makers + pipeline enforced  
- limited drift possible  

---

### Stage 3 — Fully Governed

- Buffer integrated  
- full validation  
- audit and traceability  
- AI-safe environment  

---

## Extensibility

Enforcement system must support:

- new validation rules  
- new package types  
- evolving architecture constraints  
- advanced policy engines  

---

## Anti-Patterns

Strictly forbidden:

- bypassing Dev Tools  
- bypassing Makers  
- skipping pipeline stages  
- ignoring validation failures  
- manual structural changes  
- embedding governance logic in runtime code  

---

## Design Checklist

Before approving a change:

- does it violate constraints?  
- does it bypass Makers?  
- does it introduce hidden dependencies?  
- does it break dependency direction?  
- does it avoid validation?  
- does it reduce determinism?  

If yes, reject the change.

---

## Guiding Principle

Symfony-X is enforced by system design, not convention.

If enforcement can be bypassed, the architecture is incomplete.

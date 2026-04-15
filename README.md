# Symfony-X Governance & Architecture

This repository defines the **governing documents, architectural rules, and enforcement model** for the Symfony-X ecosystem.

It is the **source of truth** for how Symfony-X systems are designed, built, and validated.

---

## Purpose

The `.github` repository exists to:

- define architecture and system design  
- enforce consistency across all repositories  
- standardize terminology and constraints  
- govern package development and composition  
- enable deterministic and AI-compatible workflows  

All Symfony-X repositories must align with these documents.

---

## Document Index

### Core Architecture

#### `ARCHITECTURE.md`
Defines the full system architecture:

- layer model (Foundation, Identity, Features, Governance)  
- dependency direction rules  
- separation of concerns  
- application vs control-plane boundaries  

---

#### `TERMINOLOGY.md`
Defines the canonical language of the system:

- foundation, identity, feature  
- Maker, command, intent  
- Buffer, control plane, MCP  
- application vs governance concepts  

All documentation and code must use these terms consistently.

---

#### `CONSTRAINTS.md`
Defines **non-negotiable system rules**:

- what is allowed and forbidden  
- dependency restrictions  
- generation requirements  
- identity and feature boundaries  

This is the primary guard against architectural drift.

---

### Package & Development Standards

#### `PACKAGE_GUIDELINES.md`
Defines how Symfony-X packages must be built:

- package structure  
- dependency rules  
- configuration design  
- testing requirements  
- integration patterns  

---

#### `MAKER_CONTRACT.md`
Defines how all Maker commands must behave:

- deterministic generation rules  
- naming conventions  
- file placement rules  
- idempotency requirements  
- AI interaction constraints  

---

### Execution Model

#### `COMMAND_MAP.md`
Defines how **intent becomes commands**:

- intent classification  
- package ownership resolution  
- command selection rules  
- installation vs generation logic  

This is the translation layer between requests and actions.

---

#### `GENERATION_PIPELINE.md`
Defines the **execution pipeline**:

- intent → classification → package → command  
- validation before and after generation  
- deterministic structure creation  
- audit and traceability  

All structural changes must pass through this pipeline.

---

### Control Plane

#### `BUFFER_ARCHITECTURE.md`
Defines the Buffer system:

- control-plane responsibilities  
- validation engine  
- command orchestration  
- AI agent coordination (MCP)  
- audit and intent tracking  

Buffer governs the ecosystem externally.

---

### Enforcement

#### `ARCHITECTURE_ENFORCEMENT.md`
Defines how rules are enforced:

- Dev Tools (local enforcement)  
- Makers & pipeline (structural enforcement)  
- Buffer (global enforcement)  
- CI/CD integration  
- violation handling  

This ensures architecture is enforced automatically.

---

### Repository Governance

#### `REPOSITORY_TAXONOMY.md`
Defines repository structure and policy:

- repository tiers (Core, Identity, Feature, Product)  
- ownership and review rules  
- approval requirements  
- creation guidelines  

---

## System Model Summary

Symfony-X operates as a constrained system:

- **Foundation** → minimal baseline  
- **Identity** → defines application nature  
- **Features** → add capability  
- **Governance** → enforces correctness  

Structural changes must follow:

Intent → Command → Pipeline → Validation → Audit

---

## Enforcement Model

Rules are enforced through:

- Maker commands (structure control)  
- Dev Tools (static validation)  
- Recipes (controlled installation)  
- Buffer (global governance)  

Manual structural changes are not considered valid.

---

## Usage

All Symfony-X repositories must:

- adhere to these documents  
- follow defined dependency rules  
- use Makers for structural generation  
- pass validation requirements  
- maintain alignment with architecture  

---

## Contribution Guidelines

Changes to this repository affect the entire ecosystem.

Requirements:

- clear justification  
- alignment with existing architecture  
- consideration of downstream impact  
- approval from maintainers  

Architectural changes must not introduce:

- ambiguity  
- implicit behavior  
- non-determinism  

---

## Guiding Principle

This repository defines the system that defines all other systems.

If a rule is not enforced here, it is not enforced anywhere.

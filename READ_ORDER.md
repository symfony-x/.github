# Symfony-X Read Order

## Purpose

This document defines the **canonical reading order** for understanding the Symfony-X system.

Symfony-X is a **constrained, multi-layer architecture**.  
Reading documents out of order will lead to misunderstanding.

This sequence ensures:

- correct mental model  
- proper understanding of constraints  
- safe participation in the ecosystem  
- compatibility with AI-driven workflows  

---

## Core Principle

Symfony-X must be understood **from constraints to execution**, not the other way around.

Do not start with code.  
Start with rules.

---

## Recommended Read Order

### 1. TERMINOLOGY.md

Defines the language of the system.

You must understand:

- foundation, identity, feature  
- Maker, command, intent  
- control plane vs application plane  
- deterministic generation  

### Rule

If terms are unclear, stop and resolve them before continuing.

---

### 2. CONSTRAINTS.md

Defines what is **allowed and forbidden**.

You must understand:

- dependency rules  
- generation requirements  
- identity boundaries  
- forbidden patterns  

### Rule

Constraints are not guidelines. They are enforced.

---

### 3. ARCHITECTURE.md

Defines the system structure.

You must understand:

- the four-layer model  
- separation of concerns  
- dependency direction  
- application vs control plane  

---

### 4. REPOSITORY_TAXONOMY.md

Defines how the system is organized at the repository level.

You must understand:

- repository tiers  
- package roles  
- governance boundaries  

---

### 5. PACKAGE_GUIDELINES.md

Defines how packages must be built.

You must understand:

- package structure  
- dependency declaration  
- integration patterns  
- testing and documentation requirements  

---

### 6. MAKER_CONTRACT.md

Defines how structure is generated.

You must understand:

- deterministic generation  
- naming conventions  
- file placement rules  
- idempotency  

---

### 7. COMMAND_MAP.md

Defines how intent becomes commands.

You must understand:

- intent classification  
- package ownership resolution  
- command selection rules  

---

### 8. GENERATION_PIPELINE.md

Defines how commands are executed.

You must understand:

- pipeline stages  
- validation points  
- execution flow  
- audit model  

---

### 9. BUFFER_ARCHITECTURE.md

Defines the control plane.

You must understand:

- Buffer responsibilities  
- validation and orchestration  
- AI coordination  
- separation from application runtime  

---

### 10. ARCHITECTURE_ENFORCEMENT.md

Defines how rules are enforced.

You must understand:

- Dev Tools enforcement  
- Maker enforcement  
- pipeline enforcement  
- Buffer enforcement  

---

### 11. TEAM_PERMISSION_MATRIX.md

Defines who can do what.

You must understand:

- repository tier permissions  
- approval requirements  
- AI contribution limits  

---

### 12. ORG_CHARTER.md

Defines the governing philosophy.

You must understand:

- mission and principles  
- decision-making model  
- evolution strategy  
- authority structure  

---

## Execution Order (For Developers & AI)

After reading, all work must follow this flow:

1. identify intent  
2. classify intent  
3. resolve package ownership  
4. map to command  
5. run through generation pipeline  
6. validate  
7. refine behavior  

---

## Anti-Patterns

Do not:

- start with implementation  
- skip constraints  
- guess architecture  
- create structure manually  
- bypass Makers  
- ignore validation  

---

## For AI Agents

AI must:

- follow this read order before acting  
- operate through COMMAND_MAP  
- generate structure via Makers  
- respect all constraints  

### Rule

If an AI system has not processed these documents in order, it is not safe to operate.

---

## For Contributors

Before submitting changes:

- confirm alignment with all documents  
- verify constraints are not violated  
- ensure deterministic behavior  
- validate against pipeline  

---

## Guiding Principle

Understanding precedes action.

Symfony-X is designed to be learned in order and executed deterministically.

If you skip steps, you will break the system.

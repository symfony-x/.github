# Symfony-X Read Order

## Purpose

This document defines how to learn and operate within the Symfony-X system.

Symfony-X is a **constrained architecture system**.  
Understanding it requires reading documents in the correct order.

---

## Core Principle

Symfony-X must be understood from:

    Constraints → Structure → Generation → Execution → Governance

Do not start with code.  
Start with rules.

---

## Two Learning Paths

Symfony-X supports two paths:

### 1. Quick Start Path (Developers)

For experienced developers who want to start building quickly.

### 2. Full System Path (Architects, Maintainers, AI)

For complete understanding of the system.

---

# Quick Start Path

Follow this path to become productive quickly.

### Step 1 — TERMINOLOGY.md

Learn the core language:

- foundation, identity, feature  
- Maker, command, intent  
- control plane vs application plane  

---

### Step 2 — SYSTEM_DIAGRAM.md

Understand the system visually:

- layer structure  
- dependency direction  
- pipeline flow  

---

### Step 3 — CONSTRAINTS.md

Learn what you are not allowed to do.

Focus on:

- dependency rules  
- generation rules  
- forbidden patterns  

---

### Step 4 — COMMAND_MAP.md

Understand how to translate intent into commands.

---

### Step 5 — GENERATION_PIPELINE.md

Understand how commands execute.

---

### Step 6 — Start Building

Follow this workflow:

1. identify intent  
2. map to command  
3. run Maker  
4. refine behavior  

---

## Quick Start Rule

If something feels unclear, jump to the Full System Path.

---

# Full System Path

Required for:

- maintainers  
- contributors  
- architects  
- AI systems  

---

### 1. TERMINOLOGY.md

Defines the system language.

---

### 2. CONSTRAINTS.md

Defines all non-negotiable rules.

---

### 3. SYSTEM_DIAGRAM.md

Defines the visual system model.

---

### 4. ARCHITECTURE.md

Defines the formal system structure.

---

### 5. REPOSITORY_TAXONOMY.md

Defines repository organization and governance tiers.

---

### 6. PACKAGE_GUIDELINES.md

Defines how packages must be built.

---

### 7. MAKER_CONTRACT.md

Defines deterministic generation rules.

---

### 8. COMMAND_MAP.md

Defines intent → command mapping.

---

### 9. GENERATION_PIPELINE.md

Defines execution flow.

---

### 10. BUFFER_ARCHITECTURE.md

Defines the control plane.

---

### 11. ARCHITECTURE_ENFORCEMENT.md

Defines how rules are enforced.

---

### 12. TEAM_PERMISSION_MATRIX.md

Defines access and approval control.

---

### 13. ORG_CHARTER.md

Defines system philosophy and governance model.

---

## Execution Model (All Paths)

All work must follow:

1. identify intent  
2. classify intent  
3. resolve package ownership  
4. map to command  
5. execute through pipeline  
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

## AI-Specific Rules

AI must:

- follow Full System Path before acting  
- operate through COMMAND_MAP  
- generate structure via Makers  
- respect all constraints  

Rule:

AI that does not follow this order is unsafe.

---

## Contributor Requirements

Before submitting changes:

- confirm alignment with all documents  
- verify constraints are not violated  
- ensure deterministic behavior  
- validate through pipeline  

---

## Guiding Principle

Symfony-X is designed to be:

- learned in order  
- executed deterministically  
- enforced automatically  

Understanding precedes action.

Skipping steps breaks the system.

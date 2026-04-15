# Symfony-X Generation Pipeline

## Purpose

This document defines the **end-to-end execution model** for how intent becomes code in the Symfony-X ecosystem.

It connects:

- Command Map (intent → command)  
- Maker Contract (deterministic generation)  
- Dev Tools (quality enforcement)  
- Buffer (control-plane governance)  

This pipeline ensures:

- deterministic structure  
- enforced architecture  
- safe AI interaction  
- auditable system evolution  

---

## Core Principle

All structural change must flow through the pipeline.

Intent must become a command before it becomes code.

---

## Pipeline Overview

The Symfony-X generation pipeline consists of eight stages:

1. Intent Identification  
2. Intent Classification  
3. Package Resolution  
4. Installation Verification  
5. Command Resolution  
6. Pre-Validation  
7. Deterministic Generation  
8. Post-Validation & Audit  

Each stage is required for compliant operation.

---

## Stage 1 — Intent Identification

The desired outcome is declared.

Examples:

- add user authentication  
- create a dashboard widget  
- enable OAuth login  
- convert application to API  

Source:

- human input  
- AI agent request  

---

## Stage 2 — Intent Classification

Intent is categorized into one of:

- foundation  
- identity  
- feature  
- structural  
- governance  

This determines the execution path.

---

## Stage 3 — Package Resolution

The system determines which package owns the intent.

Examples:

- authentication → `symfony-x/user`  
- widget → `symfony-x/dashboard`  
- OAuth login → `symfony-x/user-oauth`  
- API mode → `symfony-x/api`  

### Rule

No command may be selected before ownership is resolved.

---

## Stage 4 — Installation Verification

The system checks whether the required package is installed.

If not installed:

- install package  
- execute recipe  
- optionally run setup command  

### Rule

Generation must not occur before dependencies are satisfied.

---

## Stage 5 — Command Resolution

The system selects the appropriate command.

Priority order:

1. package-specific Maker command  
2. package setup/install command  
3. governance/validation command  

Fallback:

- manual implementation only if the concept is non-structural  

### Rule

Structural intent must resolve to a Maker command.

---

## Stage 6 — Pre-Validation

Before executing structural changes, the system validates:

- dependency direction  
- package compatibility  
- identity alignment  
- constraint compliance  

### Responsibility

- Dev Tools (local validation)  
- Buffer (global validation, if available)  

### Rule

Invalid states must be rejected before execution.

---

## Stage 7 — Deterministic Generation

The selected command is executed.

### Requirements

- output must be deterministic  
- file placement must be predictable  
- code must be valid and runnable  
- structure must align with package contracts  

### Source of Enforcement

- Maker Contract  

---

## Stage 8 — Post-Validation & Audit

After execution, the system performs:

### Validation

- static analysis (PHPStan)  
- formatting checks (CS Fixer)  
- architecture validation  

### Audit

- record command execution  
- track structural changes  
- update system state  

### Responsibility

- Dev Tools (local)  
- Buffer (global audit, if available)  

---

## Pipeline Flow Summary

Intent → Classification → Package → Install → Command → Validate → Generate → Validate → Audit

---

## Execution Modes

### Local Mode (No Buffer)

Pipeline operates with:

- Command Map  
- Maker commands  
- Dev Tools  

Limitations:

- reduced global validation  
- no centralized audit  
- no multi-project awareness  

---

### Buffer-Integrated Mode

Pipeline operates with:

- Buffer orchestration  
- full validation  
- intent tracking  
- audit logging  
- MCP-based AI coordination  

This is the **fully governed mode**.

---

## AI Interaction Model

AI agents must follow the pipeline strictly.

### Required Behavior

AI must:

1. identify intent  
2. classify intent  
3. resolve package ownership  
4. select command  
5. execute generation  
6. refine only inside generated structure  

---

### Forbidden Behavior

AI must not:

- generate structural code directly  
- bypass Maker commands  
- skip validation  
- invent package boundaries  
- introduce implicit dependencies  

---

## Error Handling

At any stage, failure must:

- stop the pipeline  
- provide actionable feedback  
- avoid partial or broken state  

### Recovery

- user or agent resolves issue  
- pipeline restarts from appropriate stage  

---

## Idempotency

The pipeline must support safe re-execution.

### Guarantees

- repeated commands do not corrupt structure  
- existing code is preserved unless explicitly overridden  
- generation is predictable  

---

## Validation Points

Validation should occur at:

- before identity installation  
- before feature installation  
- before structural generation  
- after generation  
- before deployment  

---

## Observability

The pipeline must be observable.

### Required Signals

- executed commands  
- validation results  
- generation outputs  
- system state changes  

### Tools

- Symfony profiler (local insights)  
- Buffer audit log (global insights)  

---

## Extensibility

The pipeline must support:

- new packages  
- new Maker commands  
- new validation rules  
- evolving AI capabilities  

Without breaking:

- determinism  
- dependency rules  
- structural integrity  

---

## Anti-Patterns

Strictly forbidden:

- skipping pipeline stages  
- executing commands without validation  
- generating structure outside Makers  
- mutating files directly without command mapping  
- silent dependency installation  
- bypassing audit mechanisms  

---

## Design Checklist

Before executing or modifying the pipeline:

- is intent clearly defined?  
- is ownership resolved?  
- are dependencies installed?  
- is there a deterministic command?  
- has validation been performed?  
- will output be predictable?  
- will the system remain consistent?  

---

## Guiding Principle

The pipeline is the enforcement layer of Symfony-X.

If structure is created outside the pipeline, the system is no longer governed.

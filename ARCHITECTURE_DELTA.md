# ARCHITECTURE_DELTA.md

# Symfony-X Architecture Delta: Strict → Policy-Driven Modes

## Status
Proposed

## Author
David G. Becker

---

# 1. Overview

This document defines the architectural evolution of Symfony-X from a **strict, deterministic execution model** to a **policy-driven, mode-based system**.

The goal is to introduce flexibility and agent-assisted workflows **without compromising structural guarantees**.

---

# 2. Previous Model (Strict Path)

Symfony-X originally enforced a **single execution path**:

- Makers generate all structure
- Agents execute commands only (no freeform edits)
- Buffer blocks all non-compliant writes
- Pre-write validation guarantees correctness
- Manual code paths are discouraged or disallowed

## Properties

- Deterministic
- Reproducible
- Zero structural drift
- Low flexibility
- Minimal agent autonomy

---

# 3. New Model (Policy-Driven Execution)

Symfony-X now introduces **Operating Modes** that define how the system behaves.

> Structure remains deterministic. Execution becomes policy-driven.

---

# 4. Architectural Shift

| Axis | Before | After |
|------|--------|-------|
| Execution Model | Single strict path | Multiple selectable modes |
| Control Strategy | Prevention (hard blocking) | Prevention + Detection + Audit |
| Agent Role | Command executor | Bounded autonomous actor |
| Validation | Pre-write only | Pre-write + Post-write |
| Flexibility | Minimal | Configurable |

---

# 5. Invariant Layer (Unchanged)

The following remain **universally enforced across all modes**:

- Namespace and directory structure
- Package boundaries
- Contract/interface integrity
- Service wiring correctness
- Composer/bundle integrity
- Forbidden architectural patterns

## Enforcement

- Buffer (hard constraints)
- Linter (authoritative validation)

---

# 6. New System Layers

## 6.1 Policy Layer

Introduces **mode-based behavior control**:

- Locked
- Guided
- Exploratory

Each mode defines:
- enforcement strictness
- agent permissions
- validation behavior

---

## 6.2 Dual Buffer System

### Before
Buffer = Gatekeeper (blocking)

### After
Buffer = Gatekeeper (hard) + Advisor (soft)

#### Responsibilities

| Role | Function |
|------|----------|
| Gatekeeper | Blocks invariant violations |
| Advisor | Detects drift, suggests improvements |

---

## 6.3 Agent Capability Expansion

### Before
- MCP tools only
- No direct code edits

### After
- MCP tools (all modes)
- Bounded autonomous edits (Guided+)
- Grounded freeform edits (Exploratory)

#### Constraint Model

- Structure: always protected
- Logic: conditionally editable
- Scope: mode-dependent

---

## 6.4 Dual Validation Pipeline

### Before
Pre-write validation → Write

### After
Pre-write validation → Write → Post-write audit

#### Components

| Stage | Tool | Purpose |
|------|------|---------|
| Pre-write | Buffer | Prevent invalid writes |
| Post-write | Linter | Enforce correctness |
| Runtime | Profiler | Observe behavior |

---

## 6.5 Linter Elevation

The linter is now:

> The single source of truth for system correctness

### Responsibilities

- Enforce invariants
- Detect drift
- Score code quality
- Gate CI/CD (mode-dependent)

---

# 7. Mode-Specific Behavior

## 7.1 Locked Mode

### Goal
Maximum determinism

### Rules

- Makers required
- No manual structure edits
- No agent-generated files
- Buffer blocks all violations
- Linter blocks all failures

---

## 7.2 Guided Mode

### Goal
Controlled flexibility

### Rules

- Makers preferred
- Manual code allowed
- Agent edits allowed in safe zones
- Buffer enforces invariants only
- Linter blocks structural violations

---

## 7.3 Exploratory Mode

### Goal
Rapid iteration and experimentation

### Rules

- Manual + agent workflows allowed
- Buffer acts primarily as advisor
- Continuous audit replaces strict blocking
- Linter reports drift severity

---

# 8. Safe Zone Model

Introduces **bounded autonomy regions** for agents.

## Allowed

- Method bodies
- Annotated regions
- Non-structural logic

## Forbidden

- Directory structure
- Namespaces
- Contracts/interfaces
- Service configuration

---

# 9. Installation Model Change

### Before
- Maker-only installation

### After
- Maker OR manual installation
- Linter validates both

---

# 10. Control System Interpretation

Symfony-X now functions as a **closed-loop control system**:

| Component | Role |
|----------|------|
| Makers | Initial state generator |
| Agent | Actuator |
| Buffer | Controller (pre-write) |
| Linter | Sensor (post-write validation) |
| Profiler | Telemetry |

---

# 11. Risks Introduced

| Risk | Description | Mitigation |
|------|------------|-----------|
| Structural drift | Manual or agent edits bypass patterns | Enforce invariants in buffer + linter |
| Loss of determinism | Multiple workflows | Mode declaration + CI enforcement |
| Agent misuse | Unbounded edits | Safe zones + MCP grounding |
| Audit noise | Excess logging | Structured scoring + thresholds |

---

# 12. Benefits Gained

- Developer choice of workflow
- Support for real-world coding patterns
- Integration of AI-assisted development
- Continuous system introspection
- Path toward self-optimizing architecture

---

# 13. Migration Strategy

1. Introduce `mode` configuration
2. Refactor Buffer into dual-role system
3. Expand Linter capabilities
4. Define safe zone annotations
5. Update Makers to respect mode
6. Integrate profiler feedback loop

---

# 14. Configuration Example

symfony_x:
  mode: guided

---

# 15. Strategic Outcome

This evolution transforms Symfony-X into:

> A deterministic architecture with adaptive execution policies

It preserves:
- structural integrity
- reproducibility guarantees

While enabling:
- flexibility
- agent collaboration
- iterative development workflows

---

# 16. Final Principle

> Enforce what must be correct.  
> Observe and guide what can evolve.

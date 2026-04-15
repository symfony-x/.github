# OPERATING_MODES.md

# Symfony-X Operating Modes

Symfony-X is designed as a **constraint-driven architecture with selectable execution policies**.

Rather than enforcing a single workflow, Symfony-X provides **explicit operating modes** that allow developers to choose the level of determinism, flexibility, and agent autonomy appropriate for their use case.

---

# Core Principle

> **Structure is always deterministic. Workflow is policy-driven.**

All modes preserve **architectural invariants**, while allowing variation in:

- developer workflow
- agent behavior
- enforcement strictness
- validation timing

---

# Universal Invariants (ALL MODES)

These rules are **non-negotiable** and enforced regardless of mode:

- Namespace and directory structure integrity
- Package boundaries and modular isolation
- Contract/interface compliance
- Service registration correctness
- Forbidden pattern prevention (as defined by Symfony-X rules)
- Composer and bundle consistency
- Explicit identity ownership
- SXUC async invariants when `symfony-x/ui` is installed

These are enforced by:

- Buffer (hard constraints)
- Linter (authoritative validation)

---

# Operating Modes Overview

| Mode | Purpose | Enforcement Level | Agent Autonomy |
|-----|--------|------------------|----------------|
| Locked | Maximum determinism and safety | Strict (blocking) | None (commands only) |
| Guided | Balanced workflow with controlled flexibility | Moderate (mixed) | Bounded |
| Exploratory | Rapid iteration and experimentation | Light (audit-driven) | High (grounded) |

---

# 1. Locked Mode

## Description

Locked Mode enforces **full deterministic architecture**.

All changes must pass through Symfony-X generators and commands.

## Characteristics

- Makers are required for scaffolding
- MCP tools are the only allowed agent interface
- Buffer acts as a strict execution gatekeeper
- Pre-write validation is blocking
- Linter failures block CI/CD

## Behavior

- No manual structural changes allowed
- No direct agent-generated files
- All code originates from deterministic scaffolding

## Use Cases

- Production systems
- Core architecture packages
- Shared libraries
- Security-critical applications

---

# 2. Guided Mode

## Description

Guided Mode allows **controlled flexibility** while preserving architectural guarantees.

## Characteristics

- Makers are preferred but not required for every local workflow step
- Manual code is allowed within constraints
- Agents may edit **bounded regions**
- Buffer enforces invariants but allows workflow flexibility
- Validation is both pre-write (selective) and post-write (audit)

## Behavior

- Developers may write code directly
- Agents may:
  - modify method bodies
  - operate within defined safe zones
- Structural violations are still blocked

## Use Cases

- Application development
- Feature iteration
- Teams balancing speed and safety

---

# 3. Exploratory Mode

## Description

Exploratory Mode enables **maximum flexibility and experimentation**, with strong observational tooling.

## Characteristics

- Makers optional for experimentation
- Manual and agent-driven workflows allowed within audited bounds
- Buffer acts primarily as an advisor
- Continuous audit replaces strict pre-write blocking
- Profiler and logs provide real-time feedback

## Behavior

- Agent autonomy is allowed but must be:
  - grounded in MCP resources
  - observable
  - auditable
- Linter reports drift severity instead of always blocking

## Use Cases

- Prototyping
- R&D
- AI-assisted development workflows
- Experimental features

---

# Component Behavior by Mode

| Component | Locked | Guided | Exploratory |
|----------|--------|--------|-------------|
| Buffer | Hard gatekeeper (blocks violations) | Enforces invariants + advisory feedback | Advisory-first, minimal blocking |
| Agent Interface | MCP tools only | MCP tools + bounded edits | Grounded autonomous edits |
| Quality Control | Pre-write blocking validation | Mixed pre-write + post-write | Continuous audit + profiler telemetry |
| Installation | Maker-only | Maker or manual | Fully flexible (validated post-write) |

---

# Enforcement Model

Symfony-X uses a **dual-layer enforcement system**:

## 1. Pre-Write Enforcement (Buffer)

- Prevents invalid writes before they occur
- Strongest in Locked mode
- Selective in Guided mode
- Minimal in Exploratory mode

## 2. Post-Write Validation (Linter + Profiler)

- Always active in all modes
- Final authority on compliance
- Produces:
  - errors (blocking)
  - warnings (drift)
  - metrics (quality scoring)

---

# Agent Autonomy Model

Agent capabilities are **tiered by mode**:

| Capability | Locked | Guided | Exploratory |
|-----------|--------|--------|-------------|
| Execute commands | ✅ | ✅ | ✅ |
| Modify generated code | ❌ | Limited | ✅ |
| Create new files | ❌ | Restricted | ✅ |
| Structural changes | ❌ | ❌ | ⚠️ (audited) |

---

# Safe Zones (Guided & Exploratory)

Agents may operate freely within:

- Method bodies
- Explicitly annotated regions
- Non-structural code areas

Agents may NOT modify:

- Directory structure
- Namespaces
- Service wiring
- Contracts/interfaces

For SXUC-owned structure, they also may not redefine:

- immediate/deferred async split
- preset/runtime boundaries
- Turbo/Mercure invariants

---

# Linter as Source of Truth

> **Makers generate structure. Linter enforces truth.**

Regardless of mode:

- The linter is the **final authority**
- All code must pass linter rules for compliance
- CI/CD pipelines should enforce linter output based on mode

---

# Mode Selection

Mode can be defined via:

- Project configuration (`symfony_x.yaml`)
- Environment (`APP_MODE`)
- CLI flags

---

# Important Boundary Rule

Operating mode changes **workflow policy**, not **architecture identity**.

Therefore, switching between Locked, Guided, and Exploratory must not:

- redefine package ownership
- weaken identity boundaries
- change SXUC runtime semantics if `symfony-x/ui` is installed

In particular:

- Turbo remains the immediate interaction mechanism in SXUC
- Mercure remains the deferred propagation mechanism in SXUC
- presets remain presentation concerns only

---

# Guiding Principle

Operating modes let teams choose how tightly workflow is governed.

They do not let teams redefine what the system fundamentally is.

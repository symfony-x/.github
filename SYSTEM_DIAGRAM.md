# Symfony-X System Diagram

## Purpose

This document provides a visual model of the Symfony-X architecture.

It complements:

- ARCHITECTURE.md (structure)
- GENERATION_PIPELINE.md (execution)
- BUFFER_ARCHITECTURE.md (control plane)

---

## High-Level Model

Symfony-X consists of two interacting systems:

1. Application Plane (your Symfony app)
2. Control Plane (Buffer)

---

## Layered Architecture

    Control Plane
    ┌───────────────────────────────┐
    │            Buffer             │
    │                               │
    │  - Validation Engine          │
    │  - Command Orchestrator       │
    │  - Intent Store               │
    │  - MCP Gateway                │
    │  - Audit Log                  │
    └───────────────▲───────────────┘
                    │
                    │ governs / validates / audits
                    │

    Application Plane
    ┌────────────────────────────────────────────────────────────┐
    │                                                            │
    │  Feature Layer                                             │
    │  --------------------------------------------------------  │
    │  user  dashboard  admin  oauth  integrations               │
    │                           ▲                                │
    │                           │ depends on                     │
    │  Identity Layer                                            │
    │  --------------------------------------------------------  │
    │  ui (SXUC)   api   mcp                                      │
    │                           ▲                                │
    │                           │ depends on                     │
    │  Governance Layer                                          │
    │  --------------------------------------------------------  │
    │  maker    dev-tools    recipes                             │
    │                           ▲                                │
    │                           │ depends on                     │
    │  Foundation Layer                                          │
    │  --------------------------------------------------------  │
    │  skeleton                                                   │
    │                                                            │
    └────────────────────────────────────────────────────────────┘

---

## Dependency Direction

    Foundation → Governance → Identity → Features

Rules:

- dependencies flow upward only
- no downward or cyclic dependencies
- identity must not depend on features
- foundation must remain neutral

---

## SXUC Runtime Model

For UI-first applications, `symfony-x/ui` introduces the governed async UX substrate:

    User Action
        │
        ▼
    Turbo / Live Component Request
        │
        ▼
    Immediate Symfony Response
        │
        ├── Turbo Frame / Stream DOM Update
        │
        └── Pending State Shown

    Background Work (optional)
        │
        ▼
    Domain Event / Completion
        │
        ▼
    Mercure Publication
        │
        ▼
    Browser Receives Update
        │
        ▼
    Turbo Stream or Stimulus Bridge
        │
        ▼
    Deferred UI Reconciliation

Canonical principle:

> Turbo governs the immediate request-response interaction cycle, while Mercure governs deferred real-time state propagation back into the UI.

---

## Generation Pipeline Flow

    Intent
      ↓
    Intent Classification
      ↓
    Package Resolution
      ↓
    Installation Check
      ↓
    Command Selection
      ↓
    Pre-Validation
      ↓
    Maker Execution
      ↓
    Post-Validation
      ↓
    Audit Log

---

## Command Model

    Intent
      ↓
    Command Map
      ↓
    Maker Command
      ↓
    Generated Structure
      ↓
    Behavior Implementation

---

## AI Interaction Model

    AI Agent
        ↓
    Intent Resolution
        ↓
    Command Mapping
        ↓
    Buffer Validation
        ↓
    Maker Execution
        ↓
    Code Refinement

Rules:

- AI never writes structure directly
- AI must use Makers
- AI operates through the pipeline

---

## Buffer Integration

    Buffer
        │
        ├── Validation
        ├── Orchestration
        └── Audit Logging
              │
              ▼
    Symfony-X Application

---

## Enforcement Model

    Dev Tools (local enforcement)
        ↓
    Makers (structural enforcement)
        ↓
    Buffer (global enforcement)

---

## Complete System Flow

    Intent
      ↓
    Command Map
      ↓
    Generation Pipeline
      ↓
    Maker Execution
      ↓
    Dev Tools Validation
      ↓
    Buffer Validation (optional)
      ↓
    Audit & Traceability
      ↓
    Application Runtime

---

## Key Properties

### Determinism

- same input → same structure
- no randomness
- no hidden behavior

---

### Explicitness

- all dependencies declared
- all structure generated
- no implicit assumptions

---

### Separation of Concerns

- identity defines nature
- features define capability
- governance enforces correctness

---

### External Governance

- Buffer is not part of runtime
- control plane is separate
- system remains operational without Buffer

---

## SXUC-Specific Properties

### Immediate / Deferred Split

- Turbo handles immediate interaction flow
- Mercure handles deferred propagation
- Stimulus bridges behavior safely inside the Turbo lifecycle

### Preset Boundary

- presets affect presentation
- presets do not redefine transport semantics
- presets do not replace server-driven UI ownership

---

## Anti-Patterns (Visual Summary)

    ✗ Manual structural code
    ✗ Implicit dependencies
    ✗ Feature redefining identity
    ✗ Identity depending on features
    ✗ Skipping pipeline
    ✗ AI generating code directly
    ✗ Buffer embedded in runtime
    ✗ UI preset redefining SXUC async runtime
    ✗ Ad hoc frontend architecture replacing SXUC

---

## Guiding Principle

Structure flows through the system, not around it.

If a change bypasses this model, it violates the architecture.

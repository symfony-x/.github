# Symfony-X Architecture

## Purpose

This document defines the **architectural model, constraints, and governing principles** of the Symfony-X ecosystem.

Symfony-X is a **constrained composition system** for building Symfony 8 applications with:

- deterministic structure
- explicit application identity
- composable feature modules
- enforced architectural boundaries
- AI-compatible development workflows

---

## Core Model

Symfony-X separates application construction into four layers:

1. Foundation
2. Identity
3. Features
4. Governance

Each layer has strict responsibilities and dependency rules.

---

## Layer 1 — Foundation

### Repository

- `symfony-x/skeleton`

### Responsibility

Provides the **minimal application baseline**.

Includes:

- Symfony 8 framework baseline
- base configuration
- Docker / local development setup

Excludes:

- UI stack
- database
- authentication
- business logic
- application features

### Rules

- must remain minimal and neutral
- must not assume application type
- must not include optional subsystems by default
- must be safe for all application types

---

## Layer 2 — Identity

### Repositories

- `symfony-x/ui`
- `symfony-x/api`
- `symfony-x/mcp`

### Responsibility

Defines the **nature of the application**.

Identity answers:

> “What kind of system is this?”

Examples:

- `ui` → UI-first applications through **SXUC**, the governed async UX identity built on Live Components, AssetMapper, Stimulus, Turbo, and Mercure
- `api` → headless / API-first systems
- `mcp` → AI-native / MCP-enabled systems

### SXUC Identity Principle

SXUC is not merely a component bundle.

It is the **async interaction substrate** for Symfony-X UI-first applications.

Its canonical principle is:

> **In SXUC, Turbo governs the immediate request-response interaction cycle, while Mercure governs deferred real-time state propagation back into the UI.**

### Rules

- identity must be explicitly installed
- identity must not be implicitly assumed by feature packages
- identity packages must remain narrowly scoped
- identity packages define integration patterns, not business logic
- `symfony-x/ui` owns async transport semantics for UI-first applications
- SXUC presets may change presentation, but must not redefine the async runtime model

---

## Layer 3 — Feature Modules

### Examples

- `symfony-x/user`
- `symfony-x/dashboard`
- `symfony-x/admin`
- `symfony-x/user-oauth`
- `symfony-x/oauth-server`

### Responsibility

Provides **bounded, composable functionality**.

Feature modules:

- implement business capability
- extend the application
- integrate with identity packages where required

### Rules

- must declare dependencies explicitly
- must not redefine application structure
- must not implicitly install identity
- must remain within a clearly defined domain boundary
- must not redefine SXUC async semantics when integrating with `symfony-x/ui`

---

## Layer 4 — Governance & Control Plane

### Repositories

- `symfony-x/dev-tools`
- `symfony-x/maker`
- `symfony-x/recipes`
- `symfony-x/buffer` (separate product)

### Responsibility

Ensures **consistency, correctness, and evolution control**.

#### dev-tools

- static analysis (PHPStan)
- formatting (PHP-CS-Fixer)
- architectural linting
- baseline quality enforcement

#### maker

- deterministic code generation framework
- shared abstractions for generators
- eliminates structural ambiguity

#### recipes

- install-time automation
- configuration wiring
- environment setup

#### buffer (Control Plane)

A **separate system** responsible for:

- compatibility validation
- architectural policy enforcement
- product intent tracking
- AI agent coordination (MCP)
- generation approval workflows

### Rules

- governance tools must not introduce runtime coupling
- Buffer must remain separate from application runtime
- generation must be deterministic and reproducible
- no freeform scaffolding is allowed

---

## Dependency Model

### Allowed Direction

Foundation → Governance → Identity → Features

### Constraints

- lower layers must not depend on higher layers
- identity must not depend on feature modules
- core tools must not depend on application features
- feature modules may depend on identity only when required
- Buffer integrates externally and is not part of the dependency chain

---

## Deterministic Generation Model

Symfony-X replaces ad-hoc scaffolding with **deterministic generation**.

### Process

1. intent is identified (human or AI)
2. intent is mapped to a maker command
3. generator produces structure based on package contract
4. developer or agent refines within constraints

### Properties

- predictable output
- enforced naming and placement
- package-aligned structure
- test scaffolding generated alongside code

### Rule

All structural code creation must occur through maker commands.

### SXUC Rule

If structure belongs to SXUC, Makers must generate **async-aware structure** by default, including:

- predictable DOM targets where applicable
- Turbo-oriented template structure
- Stimulus-compatible behavior hooks
- Mercure-ready deferred update placeholders or integration points

---

## Recipes Model

Recipes automate installation and configuration.

### Responsibilities

- register services
- configure bundles
- add routes
- set environment defaults

### Constraints

- recipes must not contain business logic
- recipes must not override package ownership
- recipes must remain idempotent and predictable

### SXUC Note

Recipes for `symfony-x/ui` and any UI preset packages may wire configuration and assets, but runtime ownership remains in the package itself.

---

## Identity Enforcement

Identity must be **explicit and visible**.

### Rule

No feature package may silently define application nature.

### Exception

Feature packages may provide installation profiles that:

- require identity packages explicitly
- clearly communicate what is being installed

Example:

- `symfony-x/user` may offer a “web-app” profile that installs `symfony-x/ui`

---

## SXUC Preset Model

SXUC supports an explicit preset selection model.

Examples:

- `preset: none`
- `preset: shadcn`
- `preset: flowbite`

### Rules

- presets are presentation strategies, not alternate architecture modes
- presets must not disable Turbo or Mercure semantics
- presets must not replace server-driven UI with client-owned application state
- preset-specific packages may provide templates, styles, adapters, and Makers
- preset selection must be explicit and developer-controlled

---

## Admin vs Control Plane

### symfony-x/admin

- application-local
- privileged user interface
- operates on application state
- part of the deployed app

### Buffer

- external control-plane system
- operates across applications and environments
- enforces architecture and policy
- coordinates AI and generation workflows

### Rule

These must remain separate concerns.

---

## Observability

Packages should provide visibility into their behavior.

### Mechanism

- Symfony Profiler DataCollectors

### Examples

- UI state inspector (`ui`)
- security decisions (`user`)
- AI traffic logs (`mcp`)
- system activity (`admin`)

### Rule

Observability should reflect meaningful runtime behavior, not noise.

For SXUC, observability should make async UX behavior visible, including:

- immediate vs deferred update paths
- topic usage where appropriate
- stream publication events
- state transition signals

---

## AI Interaction Model

Symfony-X is designed for AI-assisted development.

### Principle

AI does not write arbitrary code.

### Workflow

1. determine intent
2. map to command
3. generate deterministic structure
4. refine within constraints

### Enforcement

- maker commands define structure
- dev-tools enforce correctness
- Buffer validates system-wide integrity

### SXUC-Specific Rule

AI must not invent ad hoc frontend architecture for UI-first apps.

For SXUC-owned structure, AI must work through:

- SXUC Makers
- declared preset configuration
- governed Turbo/Mercure patterns

---

## Architectural Constraints Summary

- minimal foundation
- explicit identity selection
- composable features only
- deterministic generation required
- recipes handle wiring only
- no hidden dependencies
- no implicit structure changes
- governance is enforced, not optional
- control plane is external
- SXUC defines async UI identity for UI-first applications
- Turbo and Mercure are architectural invariants of SXUC

---

## Guiding Principle

> Symfony-X is a constrained system designed to produce predictable, scalable, and composable applications.

The system limits structure so that applications remain flexible, maintainable, and safe to evolve.

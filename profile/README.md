# Symfony-X

> A constrained, composable system for building Symfony 8 applications.

Symfony-X is not a starter kit.

It is a **governed development system** for Symfony 8 that combines:

- a minimal universal foundation
- explicit application identity
- composable feature modules
- deterministic code generation
- architecture enforcement
- AI-compatible workflows
- a separate control plane (**Buffer**)

---

## What Symfony-X Is

Symfony-X is built around a simple idea:

**applications should be composed explicitly, generated deterministically, and governed continuously.**

Instead of starting from a preconfigured app template full of assumptions, Symfony-X starts from a true baseline and adds only what is intentionally selected.

---

## The Symfony-X Model

Symfony-X separates application construction into four layers:

### 1. Foundation

Start from the minimal baseline:

- `symfony-x/skeleton`

The foundation includes:

- Symfony 8 baseline
- standard project bootstrap
- base local/dev environment

The foundation excludes:

- UI stack
- database
- authentication
- business features
- hidden assumptions

---

### 2. Identity

Define what kind of application you are building:

- `symfony-x/ui` → UI-first applications
- `symfony-x/api` → API-first / headless systems
- `symfony-x/mcp` → AI-first / MCP-enabled systems

Identity is explicit.  
It is never implied by feature packages.

---

### 3. Features

Add bounded capability through composable modules:

- `symfony-x/user`
- `symfony-x/dashboard`
- `symfony-x/admin`
- `symfony-x/user-oauth`
- `symfony-x/oauth-server`

Feature modules:

- declare dependencies explicitly
- remain domain-bounded
- do not redefine application structure
- integrate through contracts, recipes, and Makers

---

### 4. Governance

Enforce correctness through tooling and control systems:

- `symfony-x/maker`
- `symfony-x/dev-tools`
- `symfony-x/recipes`
- `symfony-x/buffer`

Governance exists to prevent structural drift and keep both human and AI-driven development aligned with the architecture.

---

## Why Symfony-X Exists

Traditional project templates often collapse too many concerns into one starting point.

Symfony-X exists to prevent that.

### No Hidden Assumptions

Nothing important is silently preinstalled.

You choose your application’s nature and capabilities explicitly.

### No Structural Drift

Structure is enforced through:

- package boundaries
- deterministic Maker commands
- controlled recipes
- validation tooling
- Buffer governance

### AI-Compatible by Design

AI does not invent architecture.

The intended workflow is:

1. identify intent
2. resolve package ownership
3. map intent to commands
4. generate structure deterministically
5. refine behavior within constraints

### Composable, Not Monolithic

Applications are built by composing:

- foundation
- identity
- features
- integrations

Not by modifying a single oversized starter.

---

## The Execution Model

Symfony-X follows this model:

**Intent → Command → Structure → Validation → Behavior**

That means:

- intent is translated into explicit commands
- structure is generated through Makers
- validation happens before and after generation
- implementation happens inside governed boundaries

This is the core of Symfony-X’s deterministic development model.

---

## Buffer: The Control Plane

`Buffer` is not an application feature.

It is a **separate control-plane system** responsible for:

- package compatibility validation
- architecture governance
- intent tracking
- AI agent coordination
- generation orchestration
- audit and traceability

Applications should continue to run without Buffer.  
Buffer governs system evolution externally.

---

## Getting Started

Start with the foundation:

    git clone https://github.com/symfony-x/skeleton my-app
    cd my-app

Choose your identity:

    composer require symfony-x/ui
    # or
    composer require symfony-x/api

Add bounded features:

    composer require symfony-x/user

From there, structure should be created through Symfony-X Maker commands rather than freeform scaffolding.

---

## Repository Structure

Symfony-X repositories are organized into distinct classes:

### Core
- `skeleton`
- `recipes`
- `maker`
- `dev-tools`

### Identity
- `ui`
- `api`
- `mcp`

### Features
- `user`
- `dashboard`
- `admin`
- `user-oauth`
- `oauth-server`

### Product
- `buffer`

This structure is intentional.  
Different repository classes have different responsibilities and governance requirements.

---

## Governance Documents

The `.github` repository is the source of truth for the system.

Key documents include:

- `ARCHITECTURE.md`
- `CONSTRAINTS.md`
- `TERMINOLOGY.md`
- `PACKAGE_GUIDELINES.md`
- `MAKER_CONTRACT.md`
- `COMMAND_MAP.md`
- `GENERATION_PIPELINE.md`
- `BUFFER_ARCHITECTURE.md`
- `ARCHITECTURE_ENFORCEMENT.md`
- `REPOSITORY_TAXONOMY.md`
- `READ_ORDER.md`

These documents define how Symfony-X is designed, generated, validated, and governed.

---

## Contribution Model

Symfony-X prioritizes:

- correctness over speed
- explicitness over convention
- determinism over ambiguity
- systems over improvisation

Contributions are expected to align with the architecture and constraints of the ecosystem.

Structural changes should not bypass:

- package ownership rules
- Makers
- validation
- repository governance

---

## Guiding Principle

> Symfony-X constrains structure so applications can remain flexible.

You choose what gets installed.  
Symfony-X governs how it fits together.

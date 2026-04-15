# Symfony-X

> A constrained, composable system for building modern Symfony applications.

Symfony-X is not a starter kit.

It is a **governed development system** for modern Symfony that combines:

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

- Symfony baseline
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

- `symfony-x/ui` → UI-first applications through **SXUC**, the governed async UX identity
- `symfony-x/api` → API-first / headless systems
- `symfony-x/mcp` → AI-first / MCP-enabled systems

Identity is explicit.  
It is never implied by feature packages.

---

## SXUC (Symfony-X UI Component)

SXUC is the UI identity implemented by `symfony-x/ui`.

It is **not a UI library**.

It is the **governed async UX substrate** for Symfony-X UI-first applications.

SXUC is built on:

- Live Components
- AssetMapper
- Stimulus
- Turbo
- Mercure

---

## SXUC Core Principle

> **In SXUC, Turbo governs the immediate request-response interaction cycle, while Mercure governs deferred real-time state propagation back into the UI.**

This creates a strict architectural split:

### Immediate UX Path

- user performs an action
- Turbo request or Live Component action is triggered
- Symfony responds immediately
- UI updates via Turbo (Frame/Stream)
- optional pending or optimistic state is shown

### Deferred Completion Path

- work is dispatched to background processing
- domain event occurs on completion
- SXUC publishes a Mercure update
- browser receives the event
- Turbo Stream or Stimulus bridge updates the DOM

---

## SXUC Preset Model

SXUC supports explicit UI presets.

Examples:

- `preset: none`
- `preset: shadcn`
- `preset: flowbite`

### Preset Rules

Presets may define:

- markup
- styling
- component structure
- UI library adapters

Presets must NOT define:

- async transport semantics
- UI lifecycle behavior
- Turbo/Mercure interaction model

---

## 3. Features

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
- must respect identity-level behavior (including SXUC async semantics)

---

## 4. Governance

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

---

## The Execution Model

Symfony-X follows this model:

**Intent → Command → Structure → Validation → Behavior**

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

---

## Getting Started

Start with the foundation:

```bash
git clone https://github.com/symfony-x/skeleton my-app
cd my-app
```

Choose your identity:

```bash
composer require symfony-x/ui
# or
composer require symfony-x/api
```

Add bounded features:

```bash
composer require symfony-x/user
```

---

## Guiding Principle

Symfony-X is a constrained system.

If something is implicit, it is a bug.

# Symfony-X

> A constrained, composable architecture for building Symfony 8 applications.

Symfony-X is not a starter kit.

It is a **governed ecosystem** designed to eliminate architectural drift and enable deterministic, scalable application development — for both humans and AI systems.

---

## What is Symfony-X?

Symfony-X provides a **foundation-first approach** to building applications:

- Start from a **true minimal Symfony baseline**
- Explicitly define your application's **nature**
- Add **composable feature modules**
- Generate code through **deterministic commands**
- Enforce structure through **tooling and governance**
- Optionally integrate with a **control-plane system (Buffer)**

---

## Core Principles

### 1. Foundation First

Start with:

- https://github.com/symfony-x/skeleton

This is a **barebones Symfony 8 application**.

It includes:
- minimal framework setup  
- Docker/dev environment  

It excludes:
- UI stack  
- database  
- authentication  
- business logic  

Nothing is assumed.

---

### 2. Explicit Application Identity

Define what your application *is*:

- https://github.com/symfony-x/ui → UI-first (LAST stack)  
- https://github.com/symfony-x/api → API-first / headless  
- https://github.com/symfony-x/mcp → AI-first / MCP-enabled  

Identity is **not implicit**. It is explicitly installed.

---

### 3. Composable Feature Modules

Add functionality through bounded packages:

- https://github.com/symfony-x/user  
- https://github.com/symfony-x/dashboard  
- https://github.com/symfony-x/admin  
- https://github.com/symfony-x/user-oauth  
- https://github.com/symfony-x/oauth-server  

Each module:
- declares dependencies explicitly  
- does not redefine application structure  
- integrates through recipes and contracts  

---

### 4. Deterministic Code Generation

- https://github.com/symfony-x/maker  
- https://github.com/symfony-x/dev-tools  
- https://github.com/symfony-x/recipes  

Symfony-X replaces freeform scaffolding with:

- **deterministic maker commands**
- **package-owned generators**
- **quality-locked output (PHPStan, CS rules)**

AI agents and developers use the same system.

---

### 5. Control Plane (Buffer)

- https://github.com/symfony-x/buffer  

Buffer is a **separate system**, not part of your app.

It acts as a **control plane** for:

- compatibility validation  
- product intent tracking  
- architectural governance  
- AI agent coordination (MCP)  
- generation approval workflows  

---

## Architecture Model

Symfony-X enforces separation between:

- **Foundation** → how an app starts  
- **Nature** → what kind of app it is  
- **Features** → what the app does  
- **Governance** → how the system evolves  

This separation is the key to:
- long-term maintainability  
- AI-assisted development  
- reproducible architectures  

---

## Why Symfony-X?

### No Hidden Assumptions
You choose everything. Nothing is preloaded.

---

### No Structural Drift
Architecture is enforced through:
- package boundaries  
- recipes  
- maker commands  
- dev tooling  
- Buffer validation  

---

### AI-Native Development

Instead of generating arbitrary code, agents:

1. determine intent  
2. map to commands  
3. generate deterministic structure  
4. refine within constraints  

---

### Composable System Design

Applications are built by composing:

- identity  
- features  
- integrations  

Not by modifying a monolithic starter.

---

## Getting Started

Clone the skeleton:

    git clone https://github.com/symfony-x/skeleton my-app
    cd my-app

Choose your identity:

    composer require symfony-x/ui
    # or
    composer require symfony-x/api

Add features:

    composer require symfony-x/user

---

## Repository Structure

Symfony-X is organized into strict repository tiers:

### Core (Foundation & Tooling)
- `skeleton`
- `recipes`
- `maker`
- `dev-tools`

### Identity (Application Nature)
- `ui`
- `api`
- `mcp`

### Features (Composable Modules)
- `user`
- `dashboard`
- `admin`
- `user-oauth`
- `oauth-server`

### Product (Control Plane)
- `buffer`

---

## Governance

Symfony-X enforces strict policies:

- core repositories are **collaborator-controlled**
- architecture changes require **review and alignment**
- packages must declare **explicit dependencies**
- deterministic generation replaces freeform scaffolding

See:
- `.github/REPOSITORY_TAXONOMY.md`
- `.github/ARCHITECTURE.md`

---

## Contribution Model

We prioritize:

- architectural integrity over speed  
- clarity over flexibility  
- deterministic systems over convention drift  

Most repositories:
- do not accept anonymous PRs  
- require structured review  
- must align with taxonomy and architecture  

Start with discussions before proposing changes.

---

## Roadmap

- stabilize core contracts (`skeleton`, `recipes`, `maker`, `dev-tools`)
- finalize identity layer (`ui`, `api`, `mcp`)
- expand feature modules
- develop Buffer as control-plane
- enable AI-native development workflows

---

## Guiding Principle

> Symfony-X is a **constrained system for building unconstrained applications**.

You control what gets installed.  
Symfony-X controls how it fits together.

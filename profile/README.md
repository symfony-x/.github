# Symfony-X

**Symfony-X is an opinionated development platform for building modern web applications with Symfony 8, the LAST stack, and AI-assisted workflows.**

> Stay close to Symfony. Constrain where it matters. Eliminate slop.

---

## 🚀 Vision

Symfony-X aims to make Symfony the best platform for **AI-driven application development** by:

* reducing architectural ambiguity
* enforcing consistent patterns
* providing generator-driven workflows
* enabling modular, composable feature installation
* keeping everything aligned with Symfony best practices

Symfony-X is not a new framework.

It is:

> **Symfony, constrained and structured for speed, consistency, and AI reliability.**

---

## 🧠 Core Principles

* **Symfony first** — follow official best practices by default
* **LAST stack** — HTML-first, server-driven UI
* **Explicit over magical** — no hidden lifecycle ownership
* **Generators over guesswork** — CLI-driven development
* **Composable features** — install capabilities via packages
* **AI-friendly structure** — predictable, machine-legible architecture

---

## 🧱 Platform Architecture

Symfony-X is built from three layers:

### 1. Skeleton (Base Application)

👉 `symfony-x/skeleton`

The canonical starting point.

Includes:

* Symfony 8 baseline
* AssetMapper, Stimulus, Turbo, Tailwind
* minimal Docker setup
* Symfony-X constitution and policies
* zero optional product features

---

### 2. Packages (Features)

Install capabilities as needed:

* `symfony-x/ui` → UI components, form theme, Stimulus wrappers
* `symfony-x/maker` → generators and scaffolding
* `symfony-x/doctrine-pack` → database support
* `symfony-x/async-pack` → Messenger-based async workflows
* `symfony-x/mercure-pack` → realtime updates
* `symfony-x/auth-pack` → authentication and users
* `symfony-x/dashboard-pack` → authenticated user dashboard
* `symfony-x/oauth-pack` → optional OAuth/social login
* `symfony-x/user-system-pack` → combined auth + dashboard (+ optional OAuth)
* `symfony-x/admin-pack` → internal/admin tooling (optional)
* `symfony-x/ai-pack` → AI integrations (optional)

> Features are installed intentionally — not baked into the base.

---

### 3. Recipes (Automation)

👉 `symfony-x/recipes`

Symfony Flex recipes automate installation:

* config wiring
* environment variables
* template setup
* asset registration
* Docker Compose service additions

> Recipes install infrastructure. Generators create application code.

---

## 🧩 UI Strategy

👉 `symfony-x/ui`

Symfony-X defines a **stable UI grammar**:

* Twig Components as the public API
* Stimulus for browser behavior
* Turbo-compatible lifecycle
* Symfony Forms with a consistent theme

Flowbite is used internally **as an implementation detail**, not as the public API.

> Apps depend on Symfony-X UI — not on Flowbite directly.

---

## ⚙️ Generators

👉 `symfony-x/maker`

Symfony-X provides CLI-driven scaffolding:

```bash
php bin/console app:make:component
php bin/console app:make:crud
php bin/console app:make:async-flow
php bin/console app:make:widget-wrapper
```

Generators ensure:

* consistent structure
* predictable output
* reduced AI ambiguity

---

## 🐳 Local Development

Symfony-X uses Docker Compose by default.

Feature packages may extend `compose.yaml` via recipes:

* database
* Mercure
* queues
* mail services
* optional AI infrastructure

All changes are:

* additive
* predictable
* scoped to the feature

---

## 📦 Installation Model

Start with the base:

```bash
composer create-project symfony-x/skeleton my_app
cd my_app
```

Then add features:

```bash
composer require symfony-x/ui
composer require symfony-x/doctrine-pack
composer require symfony-x/async-pack
composer require symfony-x/user-system-pack
```

Symfony Flex recipes handle setup automatically.

---

## 🧭 Project Philosophy

Symfony-X replaces:

❌ multiple starter templates
❌ forked “tiers” of apps
❌ copy-paste architecture decisions

with:

✅ one canonical base
✅ composable feature modules
✅ consistent installation via recipes
✅ predictable generation via CLI

---

## 📚 Existing Repositories

The following repositories represent earlier exploration stages:

* `symfony-x`
* `symfony-x2`
* `symfony-xxx`

These are being **phased out** in favor of:

> **one skeleton + modular packages**

They remain available for reference but should not be used for new projects.

---

## 🏭 Symfony-XL

👉 `symfony-x/symfony-XL`

A separate project focused on:

* automation
* orchestration
* AI-driven software generation

This is **not part of the core runtime platform**, but builds on top of Symfony-X.

---

## 🧠 Why This Approach Works

By constraining the stack and enforcing structure:

* AI produces more consistent code
* architecture becomes predictable
* onboarding becomes faster
* maintenance becomes simpler

Symfony-X turns Symfony into:

> **a constrained development language, not just a framework**

---

## 🏁 Status

🚧 Active development
⚠️ APIs and structure may evolve
🧪 Experimental but grounded in Symfony best practices

---

## 🧭 Motto

**Stay close to Symfony. Constrain where it matters. Eliminate slop.**

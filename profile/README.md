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
* delivering complete features with default UX
* keeping everything aligned with Symfony best practices

Symfony-X is not a new framework.

It is:

> **Symfony, constrained and structured for speed, consistency, and AI reliability.**

---

## 🧠 Core Principles

* **Symfony first** — follow official best practices by default
* **LAST stack** — HTML-first, server-driven UI
* **Tailwind baseline** — consistent UI system across all features
* **Explicit over magical** — no hidden lifecycle ownership
* **Generators over guesswork** — CLI-driven development
* **Composable features** — install complete feature systems
* **AI-friendly structure** — predictable, machine-legible architecture

---

## 🧱 Platform Architecture

Symfony-X is built from two primary layers:

### 1. Foundation (Platform Layer)

👉 `symfony-x/skeleton`

Defines how Symfony-X works. Mostly invisible to Application Users.

Includes:

* Symfony 8 baseline
* AssetMapper, Stimulus, Turbo, Tailwind
* minimal Docker setup
* Symfony-X policies and conventions
* zero product features

Other foundation repositories:

* `symfony-x/ui` → UI contract (Twig components, Tailwind, Stimulus patterns)
* `symfony-x/maker` → generators and deterministic scaffolding
* `symfony-x/dev-tools` → standardized development tooling
* `symfony-x/recipes` → Symfony Flex automation

---

### 2. Feature Modules (Installable Features)

Install complete, working feature systems with default UX.

Examples:

* `symfony-x/user` → internal user system (auth, persistence, account UI)
* `symfony-x/user-oauth` → OAuth/social login integration
* `symfony-x/admin` → internal/admin tooling

Future modules may include:

* AI integrations
* billing systems
* async/realtime capabilities

> Features are installed intentionally — not baked into the base.

---

## 🧩 Feature Module Philosophy

Each Feature Module provides:

* backend wiring
* configuration
* routes
* templates / components
* Tailwind-based UI
* default UX flows
* recipe automation

> No half-features. No scaffolding-only packages.

---

## 🔁 Recipes (Automation)

👉 `symfony-x/recipes`

Symfony Flex recipes automate installation:

* config wiring
* environment variables
* template setup
* asset registration
* Docker Compose extensions

> Recipes configure packages. Generators create application code.

---

## 🧩 UI Strategy

👉 `symfony-x/ui`

Symfony-X defines a **stable UI grammar**:

* Twig Components as the public API
* Stimulus for browser behavior
* Turbo-compatible lifecycle
* Symfony Forms with a consistent theme
* Tailwind as the design system

> Apps depend on Symfony-X UI — not on specific UI libraries.

---

## ⚙️ Generators

👉 `symfony-x/maker`

Symfony-X provides CLI-driven scaffolding:

php bin/console make:x-feature
php bin/console make:x-entity
php bin/console make:x-component

Generators ensure:

* consistent structure
* predictable output
* reduced AI ambiguity

---

## 🐳 Local Development

Symfony-X uses Docker Compose by default.

Feature Modules may extend `compose.yaml` via recipes:

* database
* queues
* realtime services
* mail services
* optional AI infrastructure

All changes are:

* additive
* predictable
* scoped to the feature

---

## 📦 Installation Model

Start with the base:

composer create-project symfony-x/skeleton my_app
cd my_app

Then add features:

composer require symfony-x/user
composer require symfony-x/user-oauth
composer require symfony-x/admin

Symfony Flex recipes handle setup automatically.

---

## 🧭 Project Philosophy

Symfony-X replaces:

❌ multiple starter templates  
❌ fragmented architecture decisions  
❌ copy-paste feature implementation  

with:

✅ one canonical base  
✅ installable feature modules  
✅ consistent installation via recipes  
✅ predictable generation via CLI  

---

## 📚 Existing Repositories

The following repositories represent earlier exploration stages:

* `symfony-x`
* `symfony-x2`
* `symfony-xxx`

These are being **phased out** in favor of:

> **one skeleton + feature modules**

They remain available for reference but should not be used for new projects.

---

## 🏁 Status

🚧 Active development  
⚠️ APIs and structure may evolve  
🧪 Experimental but grounded in Symfony best practices  

---

## 🧭 Motto

**Stay close to Symfony. Constrain where it matters. Eliminate AI slop.**

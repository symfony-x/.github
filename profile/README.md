# Symfony-X

**Symfony-X is an opinionated development platform for building modern web applications with Symfony 8, the LAST stack, and AI-assisted workflows.**

> Stay close to Symfony. Constrain where it matters. Eliminate slop.

---

## 🚀 Vision

Symfony-X aims to make Symfony the best platform for **AI-driven application development** by:

- reducing architectural ambiguity
- enforcing consistent patterns
- providing generator-driven workflows
- enabling modular, composable feature installation
- delivering complete features with default UX
- keeping everything aligned with Symfony best practices

Symfony-X is not a new framework.

It is:

> **Symfony, constrained and structured for speed, consistency, and AI reliability.**

---

## 🧠 Core Principles

- **Symfony first** — follow official best practices by default
- **LAST stack** — HTML-first, server-driven UI (Live, AssetMapper, Stimulus, Turbo)
- **Tailwind baseline** — consistent UI foundation across all features
- **Explicit over magical** — no hidden lifecycle ownership
- **Generators over guesswork** — CLI-driven development
- **Feature modules over fragments** — install complete systems, not partial capabilities
- **AI-friendly structure** — predictable, machine-legible architecture

---

## 🧱 Platform Architecture

Symfony-X is built from two primary layers:

### 1. Foundation (Platform Layer)

Defines how Symfony-X works. Mostly invisible to Application Users.

- symfony-x/skeleton
- symfony-x/ui
- symfony-x/maker
- symfony-x/dev-tools
- symfony-x/recipes

---

### 2. Feature Modules (Installable Features)

Install complete, working feature systems with default UX.

- symfony-x/user
- symfony-x/user-oauth
- symfony-x/admin

Future modules may include AI, billing, async, and realtime capabilities.

---

## 🧩 Feature Module Philosophy

Each Feature Module MUST:

- be installable independently
- provide a complete working feature
- include backend, config, routes, UI, and default UX
- include recipe automation

No half-features.

---

## 🧱 Skeleton

symfony-x/skeleton is the canonical starting point.

Includes:
- Symfony 8
- LAST stack
- Tailwind
- dev tooling

Excludes:
- Doctrine
- user system
- business features

---

## 🔁 Recipes

symfony-x/recipes automates installation:

- config
- routes
- templates
- env vars

Recipes configure packages. Generators create code.

---

## 📦 Installation

composer create-project symfony-x/skeleton my_app
cd my_app

composer require symfony-x/user
composer require symfony-x/user-oauth
composer require symfony-x/admin

---

## 🧠 Terminology

- Developer → builds the app
- Application User → uses the app
- User Entity → represents users in code

---

## 🏁 Status

Active development.

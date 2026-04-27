# Symfony-X

> **A disciplined, package-first architecture project for modern Symfony applications.**

Symfony-X is an independent community project focused on composing modern Symfony applications through **Composer packages, Symfony bundles, Flex recipes, LAST-stack defaults, and focused AI/Mate developer tooling**.

Symfony-X is currently in its **foundation-building phase**.

The goal is not to replace Symfony, fork Symfony, or present Symfony-X as an official Symfony distribution. The goal is to build a disciplined, inspectable, Symfony-native composition layer for developers who want stronger defaults, clearer package boundaries, and better tooling for modern application development.

---

## Symfony and Symfony-X

Symfony-X is built **for Symfony**.

It is not Symfony itself.

Symfony-X is not affiliated with, endorsed by, sponsored by, or maintained by Symfony SAS or the Symfony project. Symfony is a trademark of Symfony SAS.

Symfony-X exists as an independent ecosystem project that uses Symfony’s public extension points:

- Composer packages
- Symfony bundles
- Flex recipes
- Maker-style generators
- Symfony UX conventions
- AssetMapper
- Turbo
- Stimulus
- Live Components
- Mercure
- Messenger
- Symfony-native developer tooling

Symfony-X should be understood as:

> **An opinionated, unofficial package composition project for building modern Symfony applications.**

It should not be understood as:

- an official Symfony distribution
- a Symfony replacement
- a fork of Symfony
- a certification authority
- a framework competing with Symfony
- an autonomous AI app generator

Symfony-X depends on Symfony being strong, stable, and extensible. The project’s purpose is to build on that foundation carefully.

---

## Purpose

Symfony-X exists to explore a better way to compose modern Symfony applications.

The project is centered on a simple constraint:

> **Start by installing the capability that owns the concern.**

Reusable behavior should enter an application through a package whenever possible. If runtime Symfony integration is needed, that package should usually be a Symfony bundle. If setup or wiring is needed, it should be automated through a Flex recipe. If files must be generated into the host application, that generation should be explicit, deterministic, minimal, and reviewable.

Symfony-X is not a pile of starter templates.

It is not a collection of disconnected experiments.

It is not abstraction for its own sake.

The aim is to create a focused ecosystem around:

- a canonical Symfony-X application shell
- package-driven application composition
- Symfony bundles with clear ownership boundaries
- Flex recipes for predictable installation
- LAST-stack defaults for modern web applications
- Turbo-driven UX patterns
- deterministic scaffolding where needed
- focused AI/Mate tooling for developer assistance
- long-term maintainability

Symfony-X is designed to reduce drift, reduce ambiguity, and make the path from **idea → architecture → installation → implementation** more deliberate and more consistent.

---

## Current Status

Symfony-X is in **active foundation-building mode**.

The vision currently extends beyond the implementation surface. That is intentional.

This stage is about defining the architecture, terminology, package boundaries, repository roles, and developer workflow before expanding into a broader ecosystem.

The current priority is to build something durable, coherent, and worth building on.

---

## Current Repositories

The active Symfony-X organization is being shaped around these repositories and package roles:

- [`.github`](https://github.com/symfony-x/.github) — organization doctrine, architecture, governance, terminology, and planning
- [`skeleton`](https://github.com/symfony-x/skeleton) — canonical Symfony-X project shell
- [`workbench`](https://github.com/symfony-x/workbench) — maintainer-only development host and proving ground
- [`recipes`](https://github.com/symfony-x/recipes) — Symfony Flex recipes and installation automation
- `ui-bundle` — Symfony-X UI bundle and SXUC foundation
- `ai-mate-extension` — vendor-neutral Symfony-X Mate/MCP development tooling
- `dashboard-bundle` — future operational UI surface built on the Symfony-X UI layer
- `standards` — reusable standards, analysis, and validation support

Archived or experimental repositories may be retained for historical reference during the reset.

---

## Core Direction

Symfony-X is being shaped around several core principles.

### Package-First Composition

Application capabilities should be added through explicit packages rather than ad hoc project-local code.

A Symfony-X package may provide reusable code, a Symfony bundle, Flex recipe automation, Maker generators, frontend assets, documentation, or Mate/MCP developer tooling.

The package owns the concern. The application composes the capability.

### Symfony-Native Boundaries

Symfony-X uses Symfony terminology deliberately.

- **Package** means a Composer-distributed unit.
- **Bundle** means a reusable Symfony package with runtime framework integration.
- **UX bundle** means a Symfony bundle that ships frontend assets, controllers, or UI behavior in the Symfony UX style.
- **Recipe** means Flex automation for installation and wiring.
- **Component** means an actual UI, Twig, Live, or Stimulus component primitive inside a UI bundle.

Symfony-X should not invent new terminology when Symfony already has the right word.

### Install-Driven Application Growth

Capabilities should be installed intentionally, wired predictably, and documented clearly.

Recipes should help automate setup, but they should not hide architecture.

A good Symfony-X install path should be inspectable, repeatable, and reversible.

### LAST-Stack Defaults

Symfony-X is especially focused on the modern Symfony LAST stack:

- **Live Components**
- **AssetMapper**
- **Stimulus**
- **Turbo**

The default web application direction is server-driven, progressively enhanced, Turbo-friendly, and compatible with Symfony-native frontend tooling.

### Turbo-Driven UX

Symfony-X favors Turbo-driven web applications where possible.

The basic interaction model is:

> **Turbo handles immediate request/response UX. Mercure handles deferred real-time state propagation.**

That means applications can feel responsive without defaulting to unnecessary frontend complexity.

### AI-Aware, Not AI-Led

Symfony-X assumes developers will increasingly work with AI assistants.

The project’s response is not to let AI freely mutate applications.

Instead:

> **AI reasons. Symfony-X commands mutate.**

Symfony-X AI/Mate tooling should help assistants understand the project, inspect the application, explain architecture, suggest safe commands, and validate package shape.

Freeform code generation should not become the default architecture strategy.

### Doctrine Propagation

Symfony-X Mate tooling is not only about maintainer productivity.

It is also about giving AI assistants a bounded, vendor-neutral doctrine surface:

- terminology
- package taxonomy
- bundle vs recipe guidance
- architecture checks
- redirection tables
- install-state inspection
- safe command suggestions
- package-shape validation

This helps AI tools work inside Symfony-X constraints instead of inventing their own architecture.

---

## Planned Build Order

The current development order is:

1. `workbench`
2. `ai-mate-extension` baseline
3. `ui-bundle` / SXUC baseline
4. `dashboard-bundle` first usable version
5. Hermes Agent sandbox experiment
6. recipe ownership metadata
7. richer Mate tools
8. optional `mate-observer` later

This order is intentional.

The workbench comes first because Symfony-X needs a real maintainer host application where packages, recipes, Mate tools, UI layers, and dashboard surfaces can be developed and tested together.

---

## Workbench

`workbench` is the maintainer-only Symfony application used to develop and validate Symfony-X packages.

It is not the user-facing skeleton.

It is not the product template.

It is the proving ground.

The workbench should be used to:

- install Symfony-X packages locally
- validate bundle behavior
- test Flex recipe assumptions
- inspect services, routes, events, assets, and configuration
- develop Mate/MCP tooling
- test dashboard and UI package behavior
- prove package boundaries before recommending them publicly

The skeleton is what users start with.

The workbench is where maintainers prove the system.

---

## AI/Mate Tooling

Symfony-X AI/Mate tooling is intended to be vendor-neutral.

Core documentation should not assume one AI assistant, one model, or one client. Developers may use ChatGPT, Claude, Gemini, Codex, local models, IDE tools, MCP clients, or other systems.

The planned `ai-mate-extension` package should provide Symfony-X-specific guidance and tools without making any single AI vendor part of the architecture.

Vendor-specific adapters may exist separately, but they should not define Symfony-X itself.

---

## UI Direction

The Symfony-X UI direction is centered on `ui-bundle` and SXUC.

SXUC is the Symfony-X UI concept/layer. The package should be named like a Symfony package, not like a vague frontend component library.

The preferred package/repository term is:

> `symfony-x/ui-bundle`

The UI layer should support modern Symfony UX conventions, including:

- AssetMapper
- Stimulus controllers
- Turbo defaults
- Live Components
- Tailwind-friendly styling
- optional UI presets or adapters
- Mercure-ready async UX patterns

The UI layer should remain Symfony-native and package-driven.

---

## Skeleton Direction

The Symfony-X skeleton should stay intentionally small.

It should provide a clean application shell and a memorable first-run experience, not a large prebuilt application.

The default homepage should act as a Symfony-X orientation surface:

> **Welcome to the shell. Now compose the application.**

The core model is:

> **Shell → Capability → Wiring → Ownership → Product**

The skeleton should guide developers toward installing the capability that owns the concern, rather than encouraging copy-paste application growth.

---

## Research and Model Development

Symfony-X may also include dataset and model work aimed at improving AI-assisted Symfony development.

This research track is experimental and should support the broader doctrine of the project, not replace it.

Useful outputs may include:

- Symfony-focused datasets
- doctrine snapshots
- architecture examples
- package-shape examples
- AI assistant evaluation data
- LoRA or model experiments
- repeatable snapshot formats

Fine-tuned or open-weight models may become useful downstream, but they are not an early dependency of the project.

The first priority is human-readable doctrine, package boundaries, recipes, Mate tools, and repeatable architecture.

Related research space:

- Hugging Face [`symfony-x`](https://huggingface.co/symfony-x) — Symfony-focused datasets and model experiments

---

## What Comes Next

Symfony-X is expected to grow carefully into a broader package ecosystem around:

- canonical skeleton setup
- package and bundle conventions
- Flex recipe automation
- recipe ownership metadata
- UI bundle and SXUC primitives
- dashboard surfaces
- standards and validation tooling
- Symfony-X Mate/MCP tools
- deterministic generators
- architecture inspection tools
- optional sandboxed agent experiments

The goal is not to expand quickly for appearances.

The goal is to expand from a foundation that is structurally sound.

---

## Project Posture

Symfony-X is early.

Use it with that understanding.

The current work is about establishing the foundation, proving the package model, and documenting the architectural doctrine before encouraging broad adoption.

Symfony-X should earn trust by being:

- clear
- practical
- inspectable
- Symfony-native
- package-driven
- honest about status
- careful with automation
- respectful of the Symfony ecosystem

---

## Start Here

To understand the direction of Symfony-X, begin with the documentation in [`.github`](https://github.com/symfony-x/.github).

That repository defines the architecture, terminology, constraints, governance, and planning principles guiding the next phase of the organization.

Suggested reading order:

1. organization profile
2. architecture overview
3. terminology
4. package guidelines
5. repository taxonomy
6. command and generation model
7. AI/Mate strategy
8. governance and contribution guidance

---

## Follow the Project

Symfony-X is still early, but this is the stage where the direction is being established.

If the vision resonates with you:

- **Star the repositories**
- **Follow the organization**
- **Check back soon**

The foundation is being built now.

The ecosystem comes next.

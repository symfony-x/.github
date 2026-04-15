# Symfony-X Terminology

## Purpose

This document defines the canonical terminology used throughout the Symfony-X ecosystem.

All documentation, packages, and tools must use these terms consistently to:

- avoid ambiguity
- enforce architectural clarity
- support AI-driven workflows
- maintain shared understanding across the ecosystem

---

## Core Concepts

### Foundation

The minimal starting point for any Symfony-X application.

Defined by:

- `symfony-x/skeleton`

Characteristics:

- contains only baseline Symfony setup
- includes no application assumptions
- excludes UI, database, authentication, and features

---

### Identity

Defines the **nature of an application**.

Examples:

- UI-first application
- API-first application
- AI/MCP-enabled application

Implemented by:

- `symfony-x/ui`
- `symfony-x/api`
- `symfony-x/mcp`

Key rule:

- identity must be explicitly installed

---

### SXUC

**Symfony-X UI Component**.

The canonical async UX identity implemented by `symfony-x/ui`.

SXUC is the governed UI-first identity layer for Symfony-X applications. It is built on:

- Live Components
- AssetMapper
- Stimulus
- Turbo
- Mercure

SXUC defines:

- the async interaction model for UI-first apps
- the rendering and interaction contract for server-driven UI
- preset-based presentation strategies

---

### Async UX

A UI model where interactions are handled without full page reloads and long-running work is reflected back into the interface asynchronously.

In Symfony-X, Async UX is governed by SXUC through:

- Turbo for immediate interaction handling
- Mercure for deferred state propagation

---

### Immediate UX Path

The request-response interaction cycle handled immediately after user input.

In SXUC, this is typically:

1. user action
2. Turbo request or Live action
3. Symfony response
4. DOM update or pending state

---

### Deferred Completion Path

The background completion cycle that occurs after the initial response.

In SXUC, this is typically:

1. work dispatched to background execution
2. domain event emitted on completion
3. Mercure update published
4. browser receives update
5. Turbo Stream or Stimulus bridge updates the DOM

---

### Preset

An explicit SXUC rendering strategy selected by the developer.

Examples:

- `none`
- `shadcn`
- `flowbite`

A preset may define:

- templates
- styles
- component markup conventions
- bridge adapters

A preset does **not** define the core async runtime model.

---

### Feature Module

A bounded package that provides application capability.

Examples:

- user system
- dashboard
- admin interface
- OAuth integration

Characteristics:

- composable
- dependency-aware
- domain-scoped

---

### Governance

The system that enforces architectural correctness and consistency.

Includes:

- `dev-tools` (static analysis, linting)
- `maker` (deterministic generation)
- `recipes` (install-time wiring)
- `Buffer` (control plane)

---

### Control Plane

A system that governs application structure and evolution externally.

In Symfony-X:

- implemented by Buffer

Responsibilities:

- validation
- orchestration
- intent tracking
- AI coordination

---

## Structural Terms

### Package

A Composer-distributed unit of functionality within Symfony-X.

Types:

- identity package
- feature package
- cross-cutting package

---

### Repository

A GitHub repository containing one primary package or product.

Types:

- package repository
- product repository

---

### Product

A standalone system with its own runtime and lifecycle.

Example:

- Buffer

---

### Layer

A level in the Symfony-X architecture model.

Layers:

1. Foundation
2. Identity
3. Features
4. Governance

---

### Dependency Direction

The allowed flow of dependencies between layers.

Valid direction:

Foundation → Governance → Identity → Features

Invalid:

- Feature → Foundation inversion
- Identity → Feature
- Core → Feature

---

## Generation Terms

### Maker

A deterministic command that generates application structure.

Examples:

- `make:x-user`
- `make:x-dashboard-widget`
- `make:sxuc:component`

Key properties:

- predictable output
- package-owned
- structure-enforcing

---

### Deterministic Generation

The process of creating code where identical inputs produce identical outputs.

Key requirement:

- no randomness or hidden variation

---

### Structural Code

Code that defines application shape.

Examples:

- entities
- services
- controllers
- configuration structure
- component classes
- template structures owned by package contract

Must be generated via Makers when a package-owned Maker exists or should exist.

---

### Behavioral Code

Code that defines logic within an existing structure.

Examples:

- business rules
- conditionals
- validation logic
- component-specific interaction logic inside generated structure

May be written or refined manually or by AI within constraints.

---

### Async-Aware Scaffolding

Generated structure that is already prepared for SXUC’s async model.

Examples:

- predictable DOM targets
- Turbo-ready template boundaries
- pending/completed placeholders
- Mercure-ready update integration points

---

### Command

An executable action that produces or modifies structure.

Types:

- Maker command
- install/setup command
- validation command

---

### Command Map

The mapping between **intent and commands**.

Defines how requests become executable operations.

---

## Intent & AI Terms

### Intent

A declared desired outcome.

Examples:

- “add user login”
- “create dashboard widget”
- “enable OAuth”
- “make this a UI-first app”
- “add an async UI component”

---

### Intent Resolution

The process of translating intent into:

- package ownership
- command selection

---

### Intent Category

Classification of intent.

Types:

- foundation
- identity
- feature
- structural
- governance

---

### Identity Intent

Intent related to choosing or changing application nature.

Examples:

- “make this a UI-first app”
- “make this API-first”
- “add MCP capabilities”

---

### SXUC Intent

Intent related specifically to the governed UI-first async UX system.

Examples:

- “add an async data table”
- “create a live widget”
- “add a Turbo/Mercure UI flow”
- “install UI identity with shadcn preset”

---

### AI Agent

An automated system that interacts with Symfony-X through commands.

Rules:

- must map intent before acting
- must use Makers for structure
- must not invent architecture

---

### MCP (Model Context Protocol)

A structured interface for AI-agent interaction.

In Symfony-X:

- used by Buffer
- used by `symfony-x/mcp`

---

## Buffer-Specific Terms

### Buffer

The Symfony-X control-plane system.

Responsibilities:

- validation
- orchestration
- intent tracking
- AI coordination

---

## SXUC Runtime Terms

### Turbo-First

A design rule where Turbo is the default mechanism for navigation and partial update behavior in SXUC.

This includes:

- Turbo Drive
- Turbo Frames
- Turbo Streams

---

### Mercure-Backed Propagation

A design rule where deferred state updates are propagated back into the UI through Mercure topics and SXUC-owned update conventions.

---

### Topic Convention

A deterministic naming rule for Mercure topics in SXUC.

Examples:

- `/sxuc/component/{componentId}`
- `/sxuc/user/{userId}`
- `/sxuc/job/{jobId}`
- `/sxuc/resource/{type}/{id}`

---

### Stimulus Bridge

A scoped Stimulus behavior that adapts or reacts to SXUC async events safely within the Turbo lifecycle.

---

## Guiding Principle

Symfony-X terminology exists to eliminate ambiguity.

If a term is architecturally important, it must be named consistently and used the same way across documentation, package design, generation, and enforcement.

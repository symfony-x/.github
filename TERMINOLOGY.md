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

Must be generated via Makers.

---

### Behavioral Code

Code that defines logic within an existing structure.

Examples:
- business rules  
- conditionals  
- validation logic  

May be written or refined manually or by AI.

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

### Intent Store

The Buffer subsystem that tracks declared goals and desired system state.

---

### Package Graph

A representation of installed packages and their relationships.

---

### Validation Engine

A Buffer subsystem that enforces architecture rules.

---

### Command Orchestrator

A Buffer subsystem that sequences and executes commands.

---

### Audit Log

A record of all structural actions taken.

---

## Application Terms

### Application Plane

The running Symfony application.

Responsibilities:
- execute business logic  
- serve users  

---

### Control Plane

The Buffer system.

Responsibilities:
- govern structure  
- enforce rules  
- coordinate changes  

---

## UX Terms

### Dashboard

An application-level interface for end users.

Scope:
- user-specific data  
- personal interactions  

---

### Admin

A privileged application interface.

Scope:
- system-level management  
- operational visibility  

Not:
- the control plane  

---

## Rules & Constraints

### Explicitness

All structure and dependencies must be explicit.

---

### Determinism

All structural generation must be reproducible.

---

### Separation of Concerns

- identity defines nature  
- features define capability  
- governance enforces correctness  

---

### No Hidden Behavior

No implicit structure or silent installation of dependencies.

---

## Anti-Terms (Avoid)

Avoid vague or overloaded terms:

- “core” (unless explicitly defined)  
- “platform” (without scope)  
- “magic”  
- “auto-configured” (without explanation)  
- “just works”  

Replace with precise definitions.

---

## Guiding Principle

Clear terminology is required for deterministic systems.

If a term is ambiguous, it introduces architectural risk.

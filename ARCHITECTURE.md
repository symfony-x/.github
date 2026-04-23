# Symfony-X Architecture

## Position

Symfony-X is a constraint-driven architecture for building Symfony applications with a small, explicit, reusable package graph.

It is designed to reduce architectural drift, keep installation deterministic, and make AI-assisted development work within defined boundaries.

## Core Principles

### 1. One Canonical Skeleton

Symfony-X starts from one canonical application skeleton.

The skeleton defines the baseline project shape and developer experience, but it is intentionally minimal. It should not assume every application needs the same feature set.

### 2. Composition Over Monoliths

Applications are assembled by installing focused packages rather than growing one large framework layer.

Symfony-X favors:

- one project shell
- installable bundles for reusable capabilities
- recipes for deterministic wiring
- standards/tooling for consistency
- explicit package boundaries

### 3. Deterministic Installation

Installation should be reproducible.

That means:

- package boundaries should be clear
- recipes should apply predictable configuration
- optional features should remain optional
- defaults should reduce ambiguity instead of increasing it

### 4. LAST-First UI Doctrine

Symfony-X treats the LAST stack as the default UI posture for modern Symfony applications:

- **L**ive Components
- **A**ssetMapper
- **S**timulus
- **T**urbo

This is the default direction for interactive web applications, especially inside Symfony-X UI.

### 5. Async UX by Design

For interactive Symfony-X web applications:

- Turbo governs the immediate request-response cycle
- Mercure governs deferred real-time state propagation back into the UI
- Messenger governs asynchronous work execution

This split is the preferred default for responsive, async-first user experience.

### 6. AI Within Defined Boundaries

Symfony-X now treats **Symfony AI Mate** as the primary development-time AI integration surface.

That means Symfony-X no longer centers AI-assisted development around a custom Maker scaffolding strategy.

Instead:

- Mate extensions provide tools, resources, prompts, and instructions
- recipes provide deterministic installation and wiring
- standards and validation protect architectural consistency
- runtime AI remains a separate concern from development-time AI tooling

## System Model

Symfony-X thinks about application composition through three architectural lenses:

### Identity

What the application is.

This includes the chosen application posture and install surface, not user authentication concerns.

### Capabilities

What the application can do.

Capabilities are installed through packages and enabled through explicit composition.

### Application Structure

How the application is experienced.

This includes web UI, API surfaces, operational dashboards, and other delivery shapes.

## Package Model

Symfony-X recognizes several package types:

### Project

A canonical application shell.

Example:
- `symfony-x/skeleton`

### Bundle

A reusable Symfony package intended for installation across multiple applications.

Examples:
- `symfony-x/ui-bundle`
- `symfony-x/api-bundle`

### Mate Extension

A Composer package that extends Symfony AI Mate for development-time AI assistance.

Example:
- `symfony-x/ai-mate-extension`

### Standards / Tooling Package

A reusable package for coding standards, analysis rules, CI conventions, and related enforcement.

Example:
- `symfony-x/standards`

### Recipes Repository

A dedicated repository for Symfony Flex recipes.

Example:
- `symfony-x/recipes`

## Non-Goals

Symfony-X does not aim to be:

- an everything-in-one monolith
- a speculative package explosion
- a parallel reinvention of Symfony's own official naming
- an excuse for unconstrained AI code generation

## Current Architectural Direction

The organization reset is intentionally conservative.

The initial architecture centers on:

- `.github` for governance and defaults
- `skeleton` as the canonical project shell
- `workbench` as the Mate-enabled maintainer development application
- `recipes` as separate recipe infrastructure
- `ui-bundle` as the reusable UI install surface
- `ai-mate-extension` as the development-time AI surface
- `standards` as the reusable quality and rules package

Additional packages should be created only after their boundaries are proven by actual use.

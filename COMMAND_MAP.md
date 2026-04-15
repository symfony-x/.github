# Symfony-X Command Map

## Purpose

This document defines how human and AI intent is translated into deterministic Symfony-X commands.

It exists to ensure that:

- structural changes are generated through approved commands
- intent is mapped consistently
- AI agents do not invent architecture
- package boundaries remain enforced
- generation remains deterministic and auditable

---

## Core Principle

Intent must be translated into commands before structure is created.

Agents and developers may decide **what** they want to build, but Symfony-X commands determine **how structure is created**.

---

## Intent Translation Model

The command pipeline is:

1. identify intent
2. classify intent
3. resolve owning package
4. map intent to command
5. execute deterministic generation
6. refine implementation inside generated structure

---

## Intent Categories

### 1. Foundation Intent

Intent related to initial project setup or baseline capabilities.

Examples:

- create a new Symfony-X application
- initialize local development environment
- install baseline tooling

Typical command targets:

- project creation commands
- installer/bootstrap commands
- package installation commands

---

### 2. Identity Intent

Intent related to defining what kind of application this is.

Examples:

- make this a UI-first app
- make this an API-first app
- add MCP capabilities

Typical package targets:

- `symfony-x/ui`
- `symfony-x/api`
- `symfony-x/mcp`

Typical command forms:

- `composer require <package>`
- package install command
- package setup command

---

### 3. Feature Intent

Intent related to adding bounded application capability.

Examples:

- add a user system
- add dashboard widgets
- add admin tools
- add OAuth login
- add OAuth server support

Typical package targets:

- `symfony-x/user`
- `symfony-x/dashboard`
- `symfony-x/admin`
- `symfony-x/user-oauth`
- `symfony-x/oauth-server`

---

### 4. Structural Intent

Intent related to generating a package-owned structural element.

Examples:

- create a voter
- create a widget
- create an integration service
- create a policy object
- create a client adapter

Typical command targets:

- package-owned Maker commands

---

### 5. Governance Intent

Intent related to validation, compatibility, linting, and architectural enforcement.

Examples:

- verify package compatibility
- validate architecture
- check standards compliance
- inspect generation readiness

Typical command targets:

- dev-tools commands
- Buffer validation workflows
- QA commands

---

## SXUC-Specific Intent Resolution

If the intent is UI-first and async UX-oriented, ownership resolves to `symfony-x/ui` unless the request is clearly feature-owned.

Examples:

- “make this a UI-first app” → install `symfony-x/ui`
- “create an async table component” → `symfony-x/ui`
- “add a reusable modal component” → `symfony-x/ui`
- “add a user management screen” → likely feature package + `symfony-x/ui` integration
- “install shadcn preset for SXUC” → `symfony-x/ui` + preset bridge package/setup flow

---

## Mapping Rules

### Rule 1 — Package Ownership First

Every intent must resolve to an owning package before generation occurs.

Examples:

- “create a dashboard widget” → `symfony-x/dashboard`
- “create a security voter for users” → `symfony-x/user`
- “add AI traffic logging” → `symfony-x/mcp`
- “add an async UI component” → `symfony-x/ui`

No command should be chosen before ownership is resolved.

---

### Rule 2 — No Freeform Structural Generation

If the intent affects project structure, it must map to a command.

Forbidden behavior:

- inventing files manually when a Maker should exist
- bypassing package contracts
- generating cross-boundary code without an owning command

---

### Rule 3 — Prefer Specific Commands Over Generic Commands

Use the most package-specific command available.

Preferred:

- `make:x-user-voter`
- `make:sxuc:component`

Less preferred:

- generic maker plus manual edits

Reason:

- package-specific Makers encode package rules

---

### Rule 4 — Installation Before Generation

If the required package is not installed, the system must first map intent to installation.

Example:

Intent:

- add dashboard widgets

Resolution:

1. install `symfony-x/dashboard`
2. run dashboard-specific Maker command

---

### Rule 5 — Validation Before High-Risk Changes

If a command changes architecture, package composition, or cross-package behavior, validation should run before or immediately after execution.

Examples:

- adding a new identity package
- enabling multiple major subsystems
- introducing auth/server integration
- adding MCP surfaces
- switching SXUC preset strategy

---

## Resolution Pipeline

### Step 1 — Identify Intent

Interpret the requested outcome.

Examples:

- “I need user login”
- “Create a widget for account activity”
- “Add Google OAuth”
- “Make this an API”
- “Make this a UI-first app”
- “Create a live async component”

---

### Step 2 — Determine Intent Type

Classify the request as one of:

- foundation
- identity
- feature
- structural
- governance

---

### Step 3 — Resolve Package Ownership

Determine which Symfony-X package owns the concept.

Examples:

- login / local identity → `symfony-x/user`
- widget → `symfony-x/dashboard`
- admin panel action → `symfony-x/admin`
- OAuth login → `symfony-x/user-oauth`
- resource-provider auth server → `symfony-x/oauth-server`
- async UI component → `symfony-x/ui`

---

### Step 4 — Resolve Installation State

Check whether the owning package is installed.

If not installed:

- map to installation first
- then map to package-owned generation command if needed

---

### Step 5 — Resolve Identity Dependencies

If the feature depends on a specific identity:

- confirm identity is installed
- install it explicitly if missing
- never assume it silently

Example:

- a UI-owned interactive flow requires `symfony-x/ui`

---

### Step 6 — Select Command

Choose the narrowest valid command.

Examples:

- install UI identity → `composer require symfony-x/ui`
- generate SXUC component → `php bin/console make:sxuc:component`
- generate SXUC live component → `php bin/console make:sxuc:live-component`

---

## SXUC Installation Mapping

### Base UI Identity

Intent:

- make this a UI-first app

Resolution:

1. install `symfony-x/ui`
2. run any UI setup/install command if defined
3. configure explicit preset if desired

---

### SXUC Preset Mapping

Intent:

- use shadcn with SXUC
- use Flowbite with SXUC

Resolution pattern:

1. ensure `symfony-x/ui` is installed
2. install the preset bridge package if required
3. set explicit preset configuration
4. run preset-aware setup or generation commands if defined

Rule:

Preset selection must remain explicit and developer-controlled.

---

## Anti-Patterns

Do not:

- skip package ownership resolution
- generate structure directly
- choose commands before identifying ownership
- silently install identity through feature intent
- infer SXUC preset choice from accidental project state
- invent ad hoc UI generation outside SXUC Makers for SXUC-owned structure

---

## Guiding Principle

Intent becomes safe only after it becomes a command.

If intent is not mapped to an owning package and an explicit command, it is not ready to change structure.

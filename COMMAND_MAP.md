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

- composer require package  
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

## Mapping Rules

### Rule 1 — Package Ownership First

Every intent must resolve to an owning package before generation occurs.

Examples:

- “create a dashboard widget” → `symfony-x/dashboard`
- “create a security voter for users” → `symfony-x/user`
- “add AI traffic logging” → `symfony-x/mcp`

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

---

## Resolution Pipeline

### Step 1 — Identify Intent

Interpret the requested outcome.

Examples:

- “I need user login”
- “Create a widget for account activity”
- “Add Google OAuth”
- “Make this an API”

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

---

### Step 4 — Resolve Installation State

Check whether the owning package is installed.

If not installed:
- map to install action first

If installed:
- continue to command selection

---

### Step 5 — Select Command

Choose the most specific deterministic command available.

Priority order:

1. package-specific Maker command  
2. package install/setup command  
3. governance/validation command  
4. fallback manual implementation only if no structural command should exist  

---

### Step 6 — Execute and Refine

After deterministic generation:
- refine business logic only inside generated boundaries  
- do not mutate package structure arbitrarily  

---

## Canonical Command Forms

### Package Installation

Use Composer installation for package acquisition.

Examples:

- `composer require symfony-x/ui`
- `composer require symfony-x/api`
- `composer require symfony-x/user`

Installation may be followed by:
- recipe execution  
- package setup command  
- validation step  

---

### Package Setup Commands

Some packages may expose installation/setup commands.

Examples:

- `php bin/console x:user:install`
- `php bin/console x:dashboard:install`

These commands should:
- finalize package-local configuration  
- scaffold package baseline artifacts if appropriate  
- remain deterministic  

---

### Package Maker Commands

These generate structural artifacts owned by a package.

Examples:

- `php bin/console make:x-user`
- `php bin/console make:x-user-voter`
- `php bin/console make:x-dashboard-widget`
- `php bin/console make:x-admin-module`
- `php bin/console make:x-oauth-client`

---

### Governance Commands

These validate composition and standards.

Examples:

- `php bin/console x:arch:validate`
- `php bin/console x:package:validate`
- `php bin/console x:maker:lint`
- `php bin/console x:buffer:sync`

Exact command names may evolve, but the governance role must remain explicit.

---

## Intent-to-Command Examples

### Example 1 — “I want a web app with login”

Intent breakdown:

- UI-first application identity  
- local user system  

Resolution:

1. `composer require symfony-x/ui`
2. `composer require symfony-x/user`
3. optional package setup command for user installation profile
4. validate composition

Possible command sequence:

- `composer require symfony-x/ui`
- `composer require symfony-x/user`
- `php bin/console x:user:install --profile=web-app`
- `php bin/console x:arch:validate`

---

### Example 2 — “Create a voter for account access”

Intent breakdown:

- structural element  
- owned by user/security domain  

Resolution:

- use user package Maker

Possible command sequence:

- `php bin/console make:x-user-voter AccountAccess`

---

### Example 3 — “Add a dashboard widget for recent activity”

Intent breakdown:

- feature extension  
- dashboard-owned structural artifact  

Resolution:

1. ensure dashboard package is installed  
2. run dashboard Maker

Possible command sequence:

- `composer require symfony-x/dashboard`
- `php bin/console make:x-dashboard-widget RecentActivity`

---

### Example 4 — “Add Google login”

Intent breakdown:

- OAuth identity-consumer integration  
- local user system extension  

Resolution:

1. ensure user package installed  
2. install user-oauth package  
3. run oauth-specific setup/generation commands  

Possible command sequence:

- `composer require symfony-x/user`
- `composer require symfony-x/user-oauth`
- `php bin/console x:user-oauth:install google`
- `php bin/console x:arch:validate`

---

### Example 5 — “Turn this into an API”

Intent breakdown:

- identity change / expansion  

Resolution:

1. install API identity package  
2. run any setup command if required  
3. validate compatibility with existing packages  

Possible command sequence:

- `composer require symfony-x/api`
- `php bin/console x:api:install`
- `php bin/console x:arch:validate`

---

### Example 6 — “Enable MCP agent tooling”

Intent breakdown:

- identity / integration capability  
- governance-sensitive  

Resolution:

1. install MCP package  
2. run setup  
3. validate policy and compatibility  
4. optionally sync with Buffer  

Possible command sequence:

- `composer require symfony-x/mcp`
- `php bin/console x:mcp:install`
- `php bin/console x:arch:validate`
- `php bin/console x:buffer:sync`

---

## AI Agent Rules

### Rule 1 — Always Map Intent Before Acting

AI must not jump directly from user request to file generation.

AI must first determine:
- intent type  
- owning package  
- appropriate command  

---

### Rule 2 — Never Invent Missing Architecture

If the correct command does not exist, AI must:

- identify the missing command gap  
- avoid inventing hidden structure  
- propose or create the missing Maker through the proper package process  

---

### Rule 3 — Prefer Installation Profiles When Available

If a package provides explicit installation profiles, AI should use them rather than manually assembling equivalent structure.

Example:
- `x:user:install --profile=web-app`

---

### Rule 4 — Refine Only After Generation

AI may implement:
- business logic  
- conditionals  
- validation rules  
- domain-specific code  

Only after deterministic structure exists.

---

## Fallback Rules

### When No Command Exists

If no command exists for a structural concept, the system must decide one of:

1. a new Maker should be added to the owning package  
2. the concept does not belong in Symfony-X generation  
3. manual implementation is acceptable because the concept is non-structural  

### Rule

The absence of a command is an architectural signal, not permission to improvise structure.

---

## Validation Integration

Commands that affect architecture should be followed by validation.

Recommended validation points:

- after identity installation  
- after feature installation  
- after cross-package setup  
- after governance-sensitive enablement  
- before major code generation  

---

## Command Naming Guidance

Recommended command families:

- `make:x-*` for structural generation  
- `x:*:install` for package setup  
- `x:*:validate` for validation  
- `x:*:sync` for external/control-plane coordination  

Naming should remain:

- explicit  
- package-scoped  
- stable  
- predictable  

---

## Anti-Patterns

Forbidden behaviors:

- AI generating structural code without command resolution  
- using generic commands when a package-specific Maker exists  
- skipping package installation state checks  
- mixing ownership across packages  
- silently introducing identity changes  
- bypassing validation for major architectural changes  

---

## Design Checklist

Before executing a command mapping, verify:

- is the intent clearly identified?  
- is the intent category known?  
- is the owning package resolved?  
- is the package installed?  
- is there a package-specific command?  
- should validation run before or after execution?  
- is the planned change structural or only behavioral?  

---

## Guiding Principle

Intent must become a command before it becomes code.

Symfony-X commands are the contract layer between requested outcomes and generated structure.

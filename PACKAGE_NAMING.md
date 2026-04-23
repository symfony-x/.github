# Symfony-X Package Naming

This document defines the naming conventions for Symfony-X repositories and packages.

## Core Rules

### 1. Use Responsibility-Based Names

A package name should describe what a developer installs, not the internal mechanism used to implement it.

Good:
- `ui-bundle`
- `ai-mate-extension`
- `standards`

Bad:
- `runtime`
- `core`
- `kernel`
- `mcp`  
  unless the package is truly about MCP as a protocol surface

### 2. One Primary Installable Package Per Repository

Symfony-X defaults to one primary package per repository unless there is a strong reason to do otherwise.

### 3. Repo Name Should Match Package Name Segment

If the Composer package is:

- `symfony-x/ui-bundle`

then the repository should be:

- `symfony-x/ui-bundle`

### 4. Bundle Names Are a Three-Part Convention

Reusable Symfony bundles must follow all three layers consistently:

| Layer | Pattern | Example |
|---|---|---|
| Composer package | `symfony-x/<name>-bundle` | `symfony-x/ui-bundle` |
| GitHub repository | `<name>-bundle` | `ui-bundle` |
| PHP bundle class | `SymfonyX<Name>Bundle` | `SymfonyXUiBundle` |

All three must align. The repo name is the Composer package segment. The PHP class capitalizes each word and prefixes with `SymfonyX`.

### 5. Reserve `-bundle` for Reusable Symfony Bundles Only

The `-bundle` suffix is reserved for repositories that deliver a reusable Symfony bundle class.

Application repositories must not use `-bundle`:
- correct: `skeleton`, `workbench`

Recipe repositories must not use `-bundle`:
- correct: `recipes`

Mate extension repositories must not use `-bundle`:
- correct: `ai-mate-extension`

### 6. Reserve Abstract Names

Do not create abstract top-level names until the boundary is proven in practice.

Reserved / deferred examples:
- `core`
- `runtime`
- `kernel`
- `contracts`
- `buffer`

## Package Type Naming

### Project Shell

Use a simple, direct name.

Example:
- `symfony-x/skeleton`

### Reusable Symfony Bundles

Reusable Symfony bundles follow the three-part convention established in Core Rule 4:

- Composer: `symfony-x/<name>-bundle`
- Repo: `<name>-bundle`
- PHP class: `SymfonyX<Name>Bundle`

Examples:
- `symfony-x/ui-bundle` → repo `ui-bundle` → class `SymfonyXUiBundle`
- `symfony-x/api-bundle` → repo `api-bundle` → class `SymfonyXApiBundle`
- `symfony-x/user-bundle` → repo `user-bundle` → class `SymfonyXUserBundle`
- `symfony-x/dashboard-bundle` → repo `dashboard-bundle` → class `SymfonyXDashboardBundle`

### Mate Packages

Suffix Symfony AI Mate extension packages with:

- `-mate-extension`

Mate extensions are not Symfony bundles. They do not register a Symfony bundle class and must not use the `-bundle` suffix.

Examples:
- `symfony-x/ai-mate-extension`
- future specialized extensions should follow the same pattern unless there is a compelling reason not to

### Standards / Tooling Packages

Use a direct responsibility-based name.

Examples:
- `symfony-x/standards`

## Naming Doctrine

Symfony-X should prefer names that are:

- explicit
- stable
- ecosystem-aligned
- install-surface oriented

Symfony-X should avoid names that are:

- overly theoretical
- protocol-centric without need
- likely to collide conceptually with Symfony official packages
- unclear to developers browsing the org

## Symfony-X Terminology vs Package Naming

Not every strong architecture term should become a repo name.

Example:
- **SXUC** is a useful architecture term
- **ui-bundle** is the preferred install/package name

Likewise:
- **Identity** is a strong architecture term
- it should not automatically become the package name for auth/user code

## Composer Naming Expectations

Composer package names should remain lowercase and follow the conventional `vendor/package` form.

Symfony-X vendor:
- `symfony-x`

Package segment:
- lowercase
- hyphenated where needed
- responsibility based

## Current Approved Initial Names

- `symfony-x/skeleton` — project shell (public starter app)
- `symfony-x/workbench` — project shell (maintainer validation host; not a package)
- `symfony-x/recipes` — recipes infrastructure
- `symfony-x/ui-bundle` — reusable bundle
- `symfony-x/ai-mate-extension` — Mate extension
- `symfony-x/standards` — standards/tooling

## Approved Deferred Names

- `symfony-x/api-bundle`
- `symfony-x/user-bundle`
- `symfony-x/user-oauth-bundle`
- `symfony-x/dashboard-bundle`
- `symfony-x/agent-runtime-bundle`

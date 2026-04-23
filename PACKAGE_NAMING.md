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

### 4. Reserve Abstract Names

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

Suffix reusable Symfony feature packages with:

- `-bundle`

Examples:
- `symfony-x/ui-bundle`
- `symfony-x/api-bundle`
- `symfony-x/user-bundle`
- `symfony-x/dashboard-bundle`

### Mate Packages

Suffix Symfony AI Mate extension packages with:

- `-mate-extension`

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

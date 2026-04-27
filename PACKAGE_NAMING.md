# Symfony-X Package Naming

This document defines the naming conventions for Symfony-X repositories and packages.

Symfony-X is an independent community project built for Symfony applications. It is not affiliated with, endorsed by, sponsored by, or maintained by Symfony SAS or the Symfony project. Symfony is a trademark of Symfony SAS.

---

## Core Rules

### 1. Use Responsibility-Based Names

A package name should describe what a developer installs, not the internal mechanism used to implement it.

Good:

- `ui-bundle`
- `dashboard-bundle`
- `ai-mate-extension`
- `standards`

Bad unless the boundary is proven:

- `runtime`
- `core`
- `kernel`
- `contracts`
- `mcp`
- `maker`

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
- `maker`
- `mcp`

### 5. Avoid Official-Sounding Claims

Package names and descriptions must not imply that Symfony-X is official Symfony, a Symfony distribution, a certification authority, or a replacement for Symfony.

Symfony-X packages are independent packages built for Symfony applications.

---

## Package Type Naming

### Project Shell

Use a simple, direct name.

Example:

- `symfony-x/skeleton`

### Maintainer Workbench

Use a simple, direct name.

Example:

- `symfony-x/workbench`

The workbench is a maintainer host application, not a reusable package.

### Reusable Symfony Bundles

Suffix reusable Symfony feature packages with:

- `-bundle`

Examples:

- `symfony-x/ui-bundle`
- `symfony-x/dashboard-bundle`
- `symfony-x/api-bundle`
- `symfony-x/user-bundle`

### UX-Oriented Symfony Bundles

Use `-bundle` naming, not vague frontend package naming.

Preferred:

- `symfony-x/ui-bundle`

Avoid:

- `symfony-x/ui-component`
- `symfony-x/components`
- `symfony-x/frontend`

### AI/Mate Packages

Suffix Symfony-X Mate extension packages with:

- `-mate-extension`

Examples:

- `symfony-x/ai-mate-extension`

Future specialized extensions should follow the same pattern unless there is a compelling reason not to.

### Optional Vendor Adapters

Vendor-specific adapters may use names that make the adapter role explicit.

They must not imply that the vendor is required by Symfony-X core architecture.

### Standards / Tooling Packages

Use a direct responsibility-based name.

Examples:

- `symfony-x/standards`

---

## Naming Doctrine

Symfony-X should prefer names that are:

- explicit
- stable
- Symfony-native
- Composer-aligned
- ecosystem-aligned
- install-surface oriented

Symfony-X should avoid names that are:

- overly theoretical
- protocol-centric without need
- likely to collide conceptually with official Symfony packages
- unclear to developers browsing the org
- suggestive of official Symfony status

---

## Symfony-X Terminology vs Package Naming

Not every strong architecture term should become a repo name.

Example:

- **SXUC** is a useful architecture term.
- **ui-bundle** is the preferred install/package name.

Likewise:

- **Identity** is a strong architecture term.
- It should not automatically become the package name for auth/user code.

---

## Composer Naming Expectations

Composer package names should remain lowercase and follow the conventional `vendor/package` form.

Symfony-X vendor:

- `symfony-x`

Package segment:

- lowercase
- hyphenated where needed
- responsibility based

---

## Current Approved Initial Names

- `symfony-x/skeleton` — project shell for new applications
- `symfony-x/workbench` — maintainer validation host; not a package
- `symfony-x/recipes` — recipes infrastructure
- `symfony-x/ui-bundle` — reusable Symfony UX-oriented bundle
- `symfony-x/ai-mate-extension` — vendor-neutral Mate/MCP extension
- `symfony-x/standards` — standards/tooling

---

## Current Planned Names

- `symfony-x/dashboard-bundle` — reusable operational UI surface

---

## Approved Deferred Names

- `symfony-x/api-bundle`
- `symfony-x/user-bundle`
- `symfony-x/user-oauth-bundle`
- `symfony-x/agent-runtime-bundle`
- `symfony-x/mate-observer`

---

## Avoided Public Language

Avoid package descriptions using:

- official Symfony
- certified Symfony-X
- Symfony distribution
- Symfony replacement
- next Symfony
- autonomous AI generator
- software factory

Prefer:

- independent Symfony ecosystem project
- built for Symfony applications
- Symfony-native package composition
- package-first architecture
- Turbo-driven web applications
- AI/Mate developer assistance

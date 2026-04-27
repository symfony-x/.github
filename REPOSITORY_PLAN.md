# Symfony-X Repository Plan

This document defines the current repository reset plan for the Symfony-X organization.

The goal is to create only the repositories whose responsibilities are already clear, and defer speculative boundaries until they are proven.

Symfony-X is an independent community project built for Symfony applications. It is not affiliated with, endorsed by, sponsored by, or maintained by Symfony SAS or the Symfony project. Symfony is a trademark of Symfony SAS.

---

## Current Build Order

The current development order is:

1. `symfony-x/workbench`
2. `symfony-x/ai-mate-extension` baseline
3. `symfony-x/ui-bundle` / SXUC baseline
4. `symfony-x/dashboard-bundle` first usable version
5. Hermes Agent sandbox experiment
6. recipe ownership metadata
7. richer Mate tools
8. optional `symfony-x/mate-observer` later

This order is intentional.

The workbench comes first because Symfony-X needs a real maintainer host application where packages, recipes, Mate tools, UI layers, and dashboard surfaces can be developed and tested together.

---

## Active Foundation Repositories

### `symfony-x/.github`

Purpose:

- organization profile
- default community health files
- canonical governance and architecture documents
- terminology and naming doctrine

Status:

- active foundation repository

### `symfony-x/skeleton`

Purpose:

- canonical Symfony-X project shell
- minimal baseline application
- starting point for new Symfony-X applications
- first-run Symfony-X setup guide / journey map

Status:

- active foundation repository

Notes:

- The skeleton should remain intentionally small.
- It is not a full distribution or product template.
- Its default page should orient developers around Shell → Capability → Wiring → Ownership → Product.

### `symfony-x/workbench`

Purpose:

- maintainer host application for validating package-and-recipe install paths inside a real Symfony-X environment
- Mate-enabled working environment for Symfony-X contributors
- integration target for Symfony-X packages under active development
- proving ground for UI, dashboard, recipes, and AI/Mate tooling

Status:

- next priority

Notes:

- Workbench is not the public starter app.
- Reusable behavior that originates here should be extracted into a package when the boundary is proven.

### `symfony-x/recipes`

Purpose:

- Symfony Flex recipes repository
- deterministic installation-time wiring for Symfony-X packages
- future recipe ownership metadata

Status:

- active foundation repository

### `symfony-x/ai-mate-extension`

Purpose:

- Symfony-X development-time AI/Mate integration
- Mate/MCP tools, resources, prompts, and instructions
- doctrine propagation for AI assistants
- package-shape and architecture validation

Status:

- create after workbench baseline

Notes:

- Vendor-neutral core package.
- Vendor-specific adapters may exist separately.

### `symfony-x/ui-bundle`

Purpose:

- reusable Symfony-X UI bundle
- SXUC foundation
- LAST-first web UI defaults
- Symfony UX-style asset/controller integration
- Turbo-driven UI patterns

Status:

- create after ai-mate-extension baseline

### `symfony-x/dashboard-bundle`

Purpose:

- reusable operational UI surface built on the Symfony-X UI layer
- first practical dashboard surface
- possible visualization point for selected truth/health surfaces

Status:

- create after ui-bundle / SXUC baseline

### `symfony-x/standards`

Purpose:

- reusable coding standards
- static analysis baselines
- architectural rule support
- CI and validation conventions

Status:

- useful foundation package, but not ahead of the workbench / Mate / UI path unless needed

---

## Planned Experiments

### Hermes Agent Sandbox Experiment

Purpose:

- test whether an external agent runtime can safely consume Symfony-X Mate/MCP tools
- discover workflows worth promoting into deterministic tools

Status:

- planned after first dashboard work

Security constraints:

- Docker sandbox required
- restricted egress
- no raw host access
- no production secrets
- no writable access to real Symfony-X repos by default
- must integrate through Symfony-X Mate/MCP tools in workbench

---

## Later / Deferred Repositories

### `symfony-x/api-bundle`

Create when:

- the reusable API surface is clearly defined
- multiple projects need the same installable API behavior

### `symfony-x/user-bundle`

Create when:

- reusable account/user functionality is clearly shared across projects

### `symfony-x/user-oauth-bundle`

Create when:

- external identity/social auth is clearly optional and separable from the base user package

### `symfony-x/agent-runtime-bundle`

Create when:

- Symfony-X has a clearly defined reusable runtime AI layer
- runtime AI boundaries are proven separately from development-time Mate tooling

### `symfony-x/mate-observer`

Create when:

- observational AI/Mate workflows are proven useful
- the package can remain bounded, inspectable, and safe

---

## Deferred — Do Not Recreate Yet

The following names are intentionally deferred because they are too abstract, too mechanism-centric, or not yet justified as standalone installable units:

- `maker`
- `mcp`
- `core`
- `runtime`
- `kernel`
- `contracts`
- `buffer`

These may remain archived, but they are not part of the new primary repository plan.

---

## Rules for New Repository Creation

A new repository should only be created when all of the following are true:

1. The installable responsibility is clear.
2. The boundary is expected to remain stable.
3. The package is reusable or strategically necessary as its own unit.
4. The name reflects developer-facing responsibility, not internal theory alone.
5. The repo does not duplicate another repo's responsibility.
6. The repo can be validated inside the workbench or an equivalent real Symfony host.

---

## Reset Doctrine

The reset is deliberately conservative.

Symfony-X should prefer:

- fewer repos with clearer boundaries
- alignment with Symfony and Composer conventions
- deferred creation over speculative creation
- explicit composition over architectural sprawl
- package-first design over project-local drift
- human-readable doctrine over hidden tooling behavior

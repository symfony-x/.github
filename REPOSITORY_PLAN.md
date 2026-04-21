# Symfony-X Repository Plan

This document defines the current repository reset plan for the Symfony-X organization.

The goal is to create only the repositories whose responsibilities are already clear, and defer speculative boundaries until they are proven.

## Phase 1 — Create Now

### 1. `symfony-x/.github`

Purpose:
- organization profile
- default community health files
- canonical governance and architecture documents

Status:
- create now

### 2. `symfony-x/skeleton`

Purpose:
- canonical Symfony-X project shell
- minimal baseline application
- starting point for new Symfony-X applications

Status:
- create now

### 3. `symfony-x/recipes`

Purpose:
- private Symfony Flex recipes repository
- deterministic installation-time wiring for Symfony-X packages

Status:
- create now

### 4. `symfony-x/ui-bundle`

Purpose:
- reusable Symfony-X UI install surface
- LAST-first web UI defaults
- Symfony-X UI architecture surface

Status:
- create now

### 5. `symfony-x/mate-extension`

Purpose:
- Symfony-X development-time AI integration
- Mate tools, resources, prompts, and instructions
- AI assistance aligned with Symfony-X constraints

Status:
- create now

### 6. `symfony-x/standards`

Purpose:
- reusable coding standards
- static analysis baselines
- architectural rule support
- CI and validation conventions

Status:
- create now

## Phase 2 — Create After Boundaries Are Proven

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

### `symfony-x/dashboard-bundle`

Create when:
- the dashboard is a reusable installable operational UI surface
- it is more than an example app or one-project interface

### `symfony-x/agent-runtime-bundle`

Create when:
- Symfony-X has a clearly defined reusable runtime AI layer on top of Symfony AI runtime components

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

## Rules for New Repository Creation

A new repository should only be created when all of the following are true:

1. The installable responsibility is clear.
2. The boundary is expected to remain stable.
3. The package is reusable or strategically necessary as its own unit.
4. The name reflects developer-facing responsibility, not internal theory alone.
5. The repo does not duplicate another repo's responsibility.

## Reset Doctrine

The reset is deliberately conservative.

Symfony-X should prefer:
- fewer repos with clearer boundaries
- alignment with Symfony and Composer conventions
- deferred creation over speculative creation
- explicit composition over architectural sprawl

# Symfony-X

Symfony-X is a constraint-driven Symfony architecture focused on explicit composition, deterministic installation, and modern Symfony development practices.

The project is being reset around a smaller, clearer foundation so the package graph matches the actual architecture.

## Principles

Symfony-X currently centers on:

- one canonical skeleton
- reusable installable bundles
- a separate recipes repository
- LAST-first UI posture for interactive web applications
- Symfony AI Mate for development-time AI assistance
- runtime AI treated as a separate concern

## Current Repository Plan

### Phase 1

- `.github` — governance, profile, and default community health files
- `skeleton` — canonical Symfony-X project shell
- `recipes` — Symfony Flex recipes repository
- `ui-bundle` — reusable Symfony-X UI install surface
- `mate-extension` — Symfony-X development-time AI extension package
- `standards` — reusable standards, analysis, and validation support

### Phase 2

- `api-bundle`
- `user-bundle`
- `user-oauth-bundle`
- `dashboard-bundle`
- `agent-runtime-bundle`

## Architectural Direction

Symfony-X favors:

- clear package responsibilities
- fewer repos with stronger boundaries
- recipes for deterministic wiring
- modern Symfony conventions
- AI assistance that works within architectural constraints

## Status

This organization is actively being reset and reorganized. Archived repositories may remain for historical reference, but the repository plan documented in `.github` is the current direction.

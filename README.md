# Symfony-X Org Governance

This repository contains the default community health files and the canonical governance documents for the Symfony-X organization.

It is the constitutional repository for the organization, not an implementation repository.

## Purpose

This repository exists to define:

- the public organization profile
- contribution, security, and support defaults
- Symfony-X architectural doctrine
- repository planning and naming rules
- the current AI development strategy

## Scope

This repository **does not** contain:

- application code
- bundle code
- Symfony Flex recipes
- runtime implementation details
- example applications

Those belong in the installable repositories they describe.

## Canonical Documents

- `ARCHITECTURE.md` — top-level architectural doctrine
- `TERMINOLOGY.md` — stable vocabulary for Symfony-X
- `REPOSITORY_PLAN.md` — which repositories exist now, later, and not yet
- `REPOSITORY_TAXONOMY.md` — repo categories and lifecycle rules
- `PACKAGE_NAMING.md` — naming rules for repos, packages, bundles, and recipes
- `AI_STRATEGY.md` — Symfony-X AI development and runtime doctrine
- `GOVERNANCE.md` — organizational governance and decision model

## Default Community Health Files

These files are intended to serve as organization-wide defaults where GitHub supports them:

- `CODE_OF_CONDUCT.md`
- `CONTRIBUTING.md`
- `SECURITY.md`
- `SUPPORT.md`
- `PULL_REQUEST_TEMPLATE.md`
- `.github/ISSUE_TEMPLATE/*`

## Public Org Profile

The public organization profile is defined by:

- `profile/README.md`

## Current Direction

Symfony-X is being reset around a smaller, clearer foundation:

- one canonical skeleton
- reusable Symfony bundles
- a separate recipes repository
- Symfony AI Mate for development-time AI assistance
- runtime AI treated as a separate concern from development tooling

See `REPOSITORY_PLAN.md` and `AI_STRATEGY.md` for the current plan.

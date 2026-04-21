# Symfony-X Governance

## Purpose

This document defines how Symfony-X makes decisions about architecture, naming, repository creation, and contribution boundaries.

## Governance Priorities

Symfony-X prioritizes:

1. architectural clarity
2. deterministic installation and composition
3. alignment with Symfony and Composer conventions
4. conservative repository creation
5. reduced drift in both code and documentation

## Decision Model

### Architectural Decisions

Architectural decisions should favor long-term semantic clarity over short-term convenience.

Changes to canonical architecture documents should be reviewed carefully because they affect the entire organization.

### Repository Creation Decisions

A new repository should not be created just because a concept exists.

A repository should only be created when:
- its installable responsibility is clear
- its boundary is expected to remain stable
- it does not duplicate an existing package
- it reflects developer-facing reality

### Naming Decisions

Naming is part of architecture.

Package and repository names should align with:
- Symfony conventions
- Composer conventions
- the actual install surface
- stable developer understanding

## Authority Model

For now, Symfony-X is architect-led.

That means:
- canonical doctrine is centralized
- naming changes are high-sensitivity changes
- speculative repo proliferation should be resisted
- architecture-first review is expected for major structural changes

## Contribution Expectations

Contributions are welcome when they improve the ecosystem without increasing ambiguity.

Contributors should:
- preserve terminology
- avoid scope creep
- avoid speculative abstractions
- discuss major repo/package boundary changes before implementation

## Repository-Level Ownership

This repository defines organizational defaults, but repository-specific controls may still be stricter.

Examples:
- `CODEOWNERS` should remain per-repository
- branch protections should be configured per-repository
- licenses should be managed per-repository

## Review Doctrine

Review should ask:

- Does this make the install surface clearer or fuzzier?
- Does this preserve package responsibility?
- Does this align with the current repository plan?
- Does this reduce drift or introduce it?
- Is this solving a real proven need?

## Reset Principle

Symfony-X is intentionally willing to reset structure when the existing repo map no longer reflects the best architecture.

Archived repositories may remain for historical reference, but they should not control the new plan.

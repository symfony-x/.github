# Symfony-X Governance

## Purpose

This document defines how Symfony-X makes decisions about architecture, naming, repository creation, contribution boundaries, and public positioning.

Symfony-X is an independent community project built for Symfony applications. It is not affiliated with, endorsed by, sponsored by, or maintained by Symfony SAS or the Symfony project. Symfony is a trademark of Symfony SAS.

---

## Governance Priorities

Symfony-X prioritizes:

1. architectural clarity
2. deterministic installation and composition
3. alignment with Symfony and Composer conventions
4. conservative repository creation
5. reduced drift in both code and documentation
6. respectful public positioning toward Symfony and the Symfony ecosystem
7. safe, bounded AI/Mate tooling

---

## Public Positioning Rule

Symfony-X must be presented as independent and unofficial.

Symfony-X documentation must not imply that the project is:

- official Symfony
- endorsed by Symfony SAS
- maintained by the Symfony project
- a Symfony distribution
- a Symfony replacement
- a certification authority
- a fork of Symfony

Public language should make clear that Symfony-X is built for Symfony applications and uses Symfony's public extension points.

---

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
- it can be validated inside the workbench or another real Symfony host

### Naming Decisions

Naming is part of architecture.

Package and repository names should align with:

- Symfony conventions
- Composer conventions
- the actual install surface
- stable developer understanding
- the independent/unofficial project posture

Names that could imply official Symfony status require extra caution.

---

## Authority Model

For now, Symfony-X is architect-led.

That means:

- canonical doctrine is centralized
- naming changes are high-sensitivity changes
- speculative repo proliferation should be resisted
- architecture-first review is expected for major structural changes
- public positioning changes should be reviewed for Symfony/Symfony-X distinction

---

## Contribution Expectations

Contributions are welcome when they improve the ecosystem without increasing ambiguity.

Contributors should:

- preserve terminology
- avoid scope creep
- avoid speculative abstractions
- discuss major repo/package boundary changes before implementation
- avoid implying official Symfony endorsement
- use vendor-neutral AI language in core docs

---

## Repository-Level Ownership

This repository defines organizational defaults, but repository-specific controls may still be stricter.

Examples:

- `CODEOWNERS` should remain per-repository
- branch protections should be configured per-repository
- licenses should be managed per-repository
- release policies should be set per package

---

## Review Doctrine

Review should ask:

- Does this make the install surface clearer or fuzzier?
- Does this preserve package responsibility?
- Does this align with the current repository plan?
- Does this reduce drift or introduce it?
- Is this solving a real proven need?
- Does this preserve Symfony-native terminology?
- Does this preserve the Symfony/Symfony-X distinction?
- Does this keep AI assistance bounded and auditable?

---

## AI/Mate Governance

Core Symfony-X AI/Mate tooling should remain vendor-neutral.

AI/Mate tools should help developers inspect, understand, validate, and safely operate within Symfony-X constraints.

Mutation tools require:

- explicit command boundaries
- dry-run support where practical
- idempotency where practical
- reviewable output
- no silent host-level mutation

External agent experiments must be sandboxed and treated as experiments, not Symfony-X architecture.

---

## Doctrine Evolution

Symfony-X doctrine should evolve, but it should not drift casually.

The risk is doctrine ossification on one side and doctrine churn on the other.

Changes should preserve a feedback loop:

- human-readable Markdown doctrine remains load-bearing
- Mate tooling reflects doctrine, not replaces it
- successful workflows can become deterministic tools
- failed assumptions should be corrected openly

---

## Reset Principle

Symfony-X is intentionally willing to reset structure when the existing repo map no longer reflects the best architecture.

Archived repositories may remain for historical reference, but they should not control the new plan.

# Contributing to Symfony-X

Thanks for your interest in contributing.

Symfony-X is still in an architecture-forming stage, so contributions should prioritize clarity, stability, and semantic integrity over volume.

## Before You Contribute

Please read these documents first:

- `ARCHITECTURE.md`
- `TERMINOLOGY.md`
- `REPOSITORY_PLAN.md`
- `PACKAGE_NAMING.md`
- `AI_STRATEGY.md`

## Contribution Priorities

Helpful contributions usually do one or more of the following:

- clarify package boundaries
- improve deterministic installation and wiring
- strengthen naming consistency
- improve standards, validation, or developer experience
- fix bugs without introducing architectural ambiguity
- improve documentation precision

## Discuss First When the Change Is Structural

Open an architecture discussion before implementing changes that affect:

- repository creation
- package naming
- package boundaries
- AI development strategy
- canonical terminology
- top-level architecture doctrine

## Pull Request Expectations

Pull requests should be:

- focused
- explicit about purpose
- aligned with current doctrine
- small enough to review carefully

Please include:
- what changed
- why it changed
- whether it affects architecture, naming, or repo boundaries
- any follow-up work that should happen separately

## What to Avoid

Please avoid submitting changes that:

- create speculative abstractions
- duplicate an existing package responsibility
- blur development-time AI and runtime AI concerns
- invent new terminology without strong justification
- treat convenience as a reason to erode architectural clarity

## Code Style and Standards

Repository-specific standards will vary, but Symfony-X generally prefers:

- modern Symfony conventions
- clear package boundaries
- minimal configuration drift
- deterministic installation behavior
- explicit naming

## Security

Do not open public issues for security vulnerabilities.

Please use the process described in `SECURITY.md`.

## Conduct

Participation in Symfony-X is governed by `CODE_OF_CONDUCT.md`.

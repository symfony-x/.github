# Contributing to Symfony-X

Thank you for your interest in Symfony-X.

Symfony-X is an independent community project built for Symfony applications. It is not affiliated with, endorsed by, sponsored by, or maintained by Symfony SAS or the Symfony project. Symfony is a trademark of Symfony SAS.

Symfony-X is early and intentionally conservative. Contributions are most useful when they strengthen the architecture, clarify the doctrine, reduce ambiguity, or validate the package-and-recipe model.

---

## Project Posture

Symfony-X is not trying to replace Symfony.

It is a package-first architecture project built on Symfony's public extension points.

The goal is disciplined composition:

- Composer packages
- Symfony bundles
- Flex recipes
- LAST-stack defaults
- Turbo-driven UX
- focused AI/Mate developer tooling
- predictable, inspectable application growth

---

## Contribution Principles

Good contributions should:

- preserve Symfony-native terminology
- improve clarity
- reduce drift
- respect package boundaries
- avoid speculative abstractions
- avoid unnecessary repository creation
- keep automation explicit and reviewable
- preserve the Symfony/Symfony-X distinction

Avoid contributions that:

- imply Symfony-X is official Symfony
- introduce freeform AI-driven structure
- add project-local reusable behavior that belongs in a package
- create packages before boundaries are proven
- add ceremony without clear value
- privilege one AI vendor in core docs or architecture

---

## Before Opening a Pull Request

Please check:

- Does this align with `ARCHITECTURE.md`?
- Does this preserve terms from `TERMINOLOGY.md`?
- Does this follow `PACKAGE_NAMING.md`?
- Does this match the current `REPOSITORY_PLAN.md`?
- Does this keep Symfony-X independent and unofficial?
- Does this avoid vendor-specific AI assumptions in core docs?

---

## Package-First Rule

Reusable behavior should enter Symfony-X through a package whenever possible.

If runtime Symfony integration is needed, the package should usually be a Symfony bundle.

If setup or wiring is needed, it should be automated through a Flex recipe.

If host application files must be generated, generation should be explicit, deterministic, minimal, and reviewable.

---

## Documentation Contributions

Documentation is part of the architecture.

When editing docs:

- keep tone disciplined, practical, and respectful
- avoid hype
- avoid official-sounding Symfony claims
- avoid “software factory” language
- avoid autonomous AI claims
- use vendor-neutral AI language in core docs
- prefer Symfony-native terms over invented terms

---

## Code Contributions

Code contributions should be scoped to the relevant repository.

The `.github` repository is not an implementation repository.

Implementation belongs in packages such as:

- `skeleton`
- `workbench`
- `ui-bundle`
- `ai-mate-extension`
- `dashboard-bundle`
- `standards`

---

## AI-Assisted Contributions

AI-assisted work is welcome when it remains inside the project constraints.

AI-generated contributions should be reviewed carefully for:

- architectural drift
- invented terminology
- incorrect Symfony assumptions
- vendor lock-in
- vague abstractions
- hidden mutation behavior

The Symfony-X rule remains:

> **AI reasons. Symfony-X commands mutate.**

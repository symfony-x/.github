# Symfony-X Terminology

This document defines the canonical vocabulary for Symfony-X.

Symfony-X should use Symfony-native terms where Symfony already has the right word.

Symfony-X is an independent community project built for Symfony applications. It is not affiliated with, endorsed by, sponsored by, or maintained by Symfony SAS or the Symfony project. Symfony is a trademark of Symfony SAS.

---

## Symfony-X

An independent, unofficial, package-first architecture project for building modern Symfony applications with explicit composition and reduced architectural drift.

Symfony-X is built for Symfony applications. It is not Symfony itself.

---

## Package

A Composer-distributed unit.

A Symfony-X package may provide reusable PHP code, a Symfony bundle, Flex recipe support, frontend assets, standards, documentation, Maker-style generators, Mate tooling, or other clearly scoped functionality.

Use **package** when discussing Composer distribution in general.

---

## Bundle

A reusable Symfony package with runtime framework integration.

In Symfony-X, reusable runtime features should normally be delivered as bundles when they integrate with Symfony's container, configuration, routing, event system, assets, or runtime behavior.

Use **bundle** when the package is a Symfony bundle.

---

## UX Bundle

A Symfony bundle that ships frontend assets, controllers, or UI behavior in the Symfony UX style.

The Symfony-X UI package should be treated as a UX-oriented Symfony bundle.

---

## Recipe

A Symfony Flex recipe that applies deterministic installation-time wiring for a package.

Recipes are the installation and wiring contract for a package.

They are not the capability itself; the capability lives in the package.

Recipes belong in the recipes repository, separate from package code.

---

## Component

A concrete UI, Twig, Live, or Stimulus component primitive inside a UI bundle.

Do not use **component** as a vague substitute for package, bundle, layer, or system.

---

## Skeleton

The canonical Symfony-X application shell.

This is the baseline starting point for new projects and should remain minimal.

The skeleton is not a full distribution, not a dashboard, not a starter product, and not a pile of example features.

---

## Workbench

The Symfony-X maintainer host application.

Workbench exists to validate that the package-and-recipe installation path works correctly inside a real Symfony application.

It is where Symfony-X contributors develop and verify packages, recipes, UI behavior, dashboards, and AI/Mate tooling before they reach users.

It is not a public starter app, not a reusable bundle, and not a product application.

It is distinct from Skeleton, which is the public project shell for new applications.

---

## AI/Mate Extension

A Composer package that provides Symfony-X-specific development-time AI/Mate tools, resources, prompts, instructions, and architecture guidance.

The preferred package name is:

- `symfony-x/ai-mate-extension`

This package should remain vendor-neutral. It should not assume Claude, ChatGPT, Gemini, Codex, local models, or any other specific AI client as the default Symfony-X architecture.

---

## Vendor Adapter

An optional package that provides setup or guidance for a specific AI client, IDE, MCP client, or model environment.

Vendor adapters may exist, but they must not define Symfony-X architecture.

---

## Runtime AI

AI functionality embedded into the running application itself.

This is distinct from AI/Mate development tooling and includes agent workflows, chat interfaces, runtime tools, provider integration, and application-level AI orchestration.

Runtime AI should be treated as its own package concern.

---

## LAST

The default interactive web stack posture in Symfony-X:

- Live Components
- AssetMapper
- Stimulus
- Turbo

---

## SXUC

Symfony-X UI concept/layer.

SXUC is the architectural/UI identity behind the reusable UI install surface.

The install/package name should be:

- `symfony-x/ui-bundle`

SXUC is a documentation and architecture term first. The install surface remains `ui-bundle`.

---

## Turbo-Driven UX

The Symfony-X default web interaction posture where server-driven UI, progressive enhancement, and Turbo request/response flows are first-class.

Default async split:

- Turbo handles immediate request/response UX.
- Mercure handles deferred real-time state propagation.
- Messenger handles asynchronous work execution.

---

## Identity

In Symfony-X architecture, Identity refers to what the application is.

It does **not** mean user identity or authentication by default.

---

## Capability

A reusable feature or installable behavior the application can gain through explicit composition.

A capability should normally enter the application through a package.

---

## Wiring

The explicit configuration, files, routes, services, environment entries, assets, or commands that connect an installed capability to the host application.

Wiring should be deterministic, inspectable, and preferably recipe-driven.

---

## Ownership

The rule that a package owns its reusable concern, while the host application owns product-specific decisions.

Ownership prevents reusable capabilities from dissolving into application-local drift.

---

## Application Structure

How the application is delivered or experienced, such as:

- web UI
- API
- dashboard
- worker/runtime surfaces
- operator or client surfaces

---

## Doctrine

The human-readable architectural guidance, terminology, constraints, and project principles that keep Symfony-X coherent.

Doctrine should remain visible in Markdown, not hidden exclusively inside tools.

---

## Redirection Table

A doctrine mechanism that teaches AI assistants and contributors:

> Instead of X, use Y.

Redirection tables should be expanded as discouraged patterns are discovered.

---

## Standards

Reusable rules, analysis, and conventions that help keep Symfony-X codebases consistent.

---

## Governance

The organizational rules and decision framework that control naming, package creation, review expectations, and architectural authority.

---

## Deferred Repository

A repository idea that has been acknowledged but intentionally not created because its boundaries are not yet proven.

---

## Archived Repository

A repository kept for historical reference, not as part of the current primary structure.

---

## Org Constitutional Repository

The `.github` repository that defines organization-wide defaults and canonical governance documents.

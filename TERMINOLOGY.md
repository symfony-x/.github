# Symfony-X Terminology

This document defines the canonical vocabulary for Symfony-X.

## Symfony-X

A constraint-driven architecture and package ecosystem for building modern Symfony applications with explicit composition and reduced architectural drift.

## Skeleton

The canonical Symfony-X application shell.

This is the baseline starting point for new projects and should remain minimal.

## Bundle

A reusable Symfony package intended to be installed across multiple applications.

In Symfony-X, reusable runtime features should normally be delivered as bundles.

## Recipe

A Symfony Flex recipe that applies deterministic installation-time wiring for a package.

Recipes are not package code. They belong in the recipes repository.

## Mate Extension

A Composer package that extends Symfony AI Mate with development-time AI tools, resources, prompts, and instructions.

This is the preferred Symfony-X development-time AI integration model.

## Runtime AI

AI functionality embedded into the running application itself.

This is distinct from Mate and includes agent, chat, tool, provider, and application runtime concerns.

## LAST

The default interactive web stack posture in Symfony-X:

- Live Components
- AssetMapper
- Stimulus
- Turbo

## SXUC

Symfony-X UI Component.

This is the architectural/UI identity concept behind the reusable UI install surface, currently represented by `symfony-x/ui-bundle`.

SXUC is a documentation and architecture term first. The install surface remains `ui-bundle`.

## Identity

In Symfony-X architecture, Identity refers to what the application is.

It does **not** mean user identity or authentication by default.

## Capability

A reusable feature or installable behavior the application can gain through explicit composition.

## Application Structure

How the application is delivered or experienced, such as:

- web UI
- API
- dashboard
- other operator or client surfaces

## Standards

Reusable rules, analysis, and conventions that help keep Symfony-X codebases consistent.

## Governance

The organizational rules and decision framework that control naming, package creation, review expectations, and architectural authority.

## Deferred Repository

A repository idea that has been acknowledged but intentionally not created because its boundaries are not yet proven.

## Archived Repository

A repository kept for historical reference, not as part of the current primary structure.

## Org Constitutional Repository

The `.github` repository that defines organization-wide defaults and canonical governance documents.

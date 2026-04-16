# Symfony-X Terminology

This document defines the core terms used throughout Symfony-X.

The goal is to provide a shared vocabulary that enables consistent reasoning about system architecture.

---

## Foundation

The minimal baseline of a Symfony application.

Includes:
- kernel
- configuration

Does not include:
- identity
- capabilities
- application structure

Foundation exists only to support composition.

---

## Identity

Defines what an application *is*.

Examples:
- UI (SXUC)
- API
- MCP

Identity determines:
- how the system communicates
- how it behaves at runtime
- how it is interacted with

Identity must always be explicit.

---

## Capability

A bounded, reusable unit of functionality.

Examples:
- user system
- billing module
- integrations

Characteristics:
- independent of identity
- portable across applications
- focused on a single responsibility

Capabilities:
- do not define application structure
- do not assume identity
- do not alter system behavior beyond their scope

---

## Application Structure

A higher-level package that provides application structure built on identity.

Examples:
- dashboard

Application Structure packages:

- depend on identity
- assemble capabilities
- provide a usable application surface

They define how a system is experienced, not what the system fundamentally is.

---

## Application Surface

The user-facing system produced by an Application Structure package.

Examples:
- dashboard UI
- administrative interface
- operational console

An application surface is the result of composition.

---

## Composition

The process of building an application by combining:

- identity
- capabilities
- application structure

Symfony-X applications are composed, not generated.

---

## Recipe

A mechanism for configuring an application during installation.

Recipes:
- enable bundles
- configure services
- set up routes

Recipes do not define system behavior.

---

## Maker

A deterministic code generator.

Makers:
- create structure
- enforce conventions
- maintain consistency

Makers do not define architecture.

---

## Buffer

A governance layer responsible for validating architectural correctness.

The buffer ensures that:
- constraints are respected
- structure remains consistent
- drift is detected early

---

## Constraint

A rule that enforces architectural correctness.

Constraints define:
- allowed dependencies
- forbidden relationships
- required structure

Constraints are enforced across the system.

---

## System Drift

The gradual degradation of architectural consistency over time.

Causes:
- implicit structure
- unclear boundaries
- uncontrolled changes

Symfony-X is designed to prevent drift through explicit composition and enforceable constraints.

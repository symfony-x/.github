# Symfony-X Repository Taxonomy

This document defines how repositories are organized within the Symfony-X organization.

Each repository must map to a single architectural role.

---

## Tier A — Foundation

Examples:
- symfony-x/skeleton

Purpose:
- minimal application baseline

Rules:
- no application logic
- no identity
- no capabilities
- no application structure

---

## Tier B — Identity

Examples:
- symfony-x/ui
- symfony-x/api
- symfony-x/mcp

Purpose:
- define application type

Rules:
- must define interaction model
- must remain independent of application structure
- must not depend on Application Structure repositories

---

## Tier C — Capability

Examples:
- symfony-x/user
- symfony-x/user-oauth
- symfony-x/billing

Purpose:
- provide reusable functionality

Rules:
- must be identity-agnostic
- must remain portable
- must not define application structure
- must not depend on Application Structure repositories

---

## Tier D — Application Structure

Examples:
- symfony-x/dashboard

Purpose:
- provide higher-level application structure

Rules:
- must depend on Identity
- may depend on Capability repositories
- must remain additive
- must not redefine application identity

---

## Tier E — Governance

Examples:
- symfony-x/maker
- symfony-x/recipes
- symfony-x/dev-tools
- symfony-x/buffer

Purpose:
- enforce architecture
- provide tooling

Rules:
- must not define application behavior
- must not introduce application structure

---

## Classification Guide

When creating a repository:

- defines application type → Identity
- provides reusable functionality → Capability
- assembles a usable system → Application Structure
- enforces or supports system rules → Governance

---

## Core Rule

> Each repository must have a single, unambiguous architectural role.

# Repository Taxonomy

Defines how repositories are classified within the Symfony-X organization.

---

## Purpose

The taxonomy exists to:

- enforce architectural boundaries
- prevent responsibility overlap
- guide contributor decisions
- enable automated validation

---

## Classification Layers

### Tier A — Foundation
Minimal baseline.

Examples:
- symfony-x/skeleton

Rule:
- Must contain no application-specific logic

---

### Tier B — Identity
Defines application nature.

Examples:
- symfony-x/ui
- symfony-x/api
- symfony-x/mcp

Rules:
- Must define interaction model
- Must not depend on compositions

---

### Tier C — Capability Repositories
Reusable functional modules.

Examples:
- symfony-x/user
- symfony-x/user-oauth
- symfony-x/oauth-server

Rules:
- Must remain identity-agnostic
- Must not define application structure
- Must not depend on compositions

---

### Tier D — Composition Repositories
Pre-wired application surfaces.

Examples:
- symfony-x/dashboard

Rules:
- Must depend on identity
- May assemble capabilities
- Must remain additive
- Must not redefine identity implicitly

---

### Tier E — Governance
System enforcement and tooling.

Examples:
- symfony-x/maker
- symfony-x/recipes
- symfony-x/buffer

Rules:
- Must not contain business logic
- Must not define runtime behavior

---

## Classification Decision Guide

When creating a new repository:

Ask:

1. Does this define what the app *is*?
→ Identity

2. Does this add isolated functionality?
→ Capability

3. Does this create a usable application surface?
→ Composition

4. Does this enforce rules or generate structure?
→ Governance

---

## Anti-Patterns

❌ Capability that assumes UI  
❌ Composition that hides identity  
❌ Identity that depends on composition  
❌ Repo that mixes multiple layers  

---

## Principle

> Every repository must have a single architectural responsibility.

# Symfony-X Command Map

The Command Map defines how human intent is resolved into deterministic system actions.

It ensures that both developers and AI agents produce consistent, valid architecture.

---

## Core Principle

> Every intent must resolve to a clear architectural action.

No ambiguity. No implicit behavior.

---

## Intent Types

### Identity Intent

Defines what the application *is*.

Examples:
- "create a UI app"
- "build an API"
- "set up an MCP service"

Resolution:
→ install an Identity package

---

### Capability Intent

Adds reusable functionality.

Examples:
- "add user authentication"
- "add billing"
- "integrate OAuth"

Resolution:
→ install a Capability package

---

### Application Structure Intent

Defines how the application is experienced.

Examples:
- "add a dashboard"
- "create an admin interface"
- "add an operational UI"

Resolution:
→ install an Application Structure package

---

### Generation Intent

Creates deterministic structure within the system.

Examples:
- "create a user entity"
- "generate a dashboard widget"
- "add a new component"

Resolution:
→ invoke Maker commands

---

## Resolution Rules

When interpreting intent:

- Identity intent has highest priority
- Application Structure intent defines system surface
- Capability intent adds functionality
- Generation intent creates internal structure

---

## Conflict Resolution

When intent is ambiguous:

1. Identify if the request defines application type → Identity
2. Identify if it defines system surface → Application Structure
3. Identify if it adds reusable functionality → Capability
4. Otherwise → Generation

Example:

"create a dashboard app"

→ Identity (if missing)  
→ Application Structure (dashboard)

NOT:
→ Capability

---

## Behavioral Alignment

Under UI identity (SXUC):

- user interaction is immediate (Turbo)
- system updates are asynchronous (Mercure)

Commands that affect UI must align with this model.

---

## Anti-Patterns

Invalid interpretations include:

- treating Application Structure as a Capability
- installing Capabilities to define system structure
- generating architecture instead of composing it
- resolving ambiguous intent without classification

---

## Summary

The Command Map is not a command list.

It is:

> the contract between intent and architecture

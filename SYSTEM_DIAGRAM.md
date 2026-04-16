# Symfony-X System Diagram

This diagram represents the architectural structure of Symfony-X.

It illustrates the relationship between system layers and the direction of dependencies.

---

## Layered Architecture

```
+-------------------------------+
|     Application Structure     |
|        (e.g. Dashboard)       |
+-------------------------------+
               ↓
+-------------------------------+
|          Identity             |
|   (UI / API / MCP Runtime)    |
+-------------------------------+
               ↓
+-------------------------------+
|          Capability           |
|   (User, Billing, OAuth...)   |
+-------------------------------+
               ↓
+-------------------------------+
|          Foundation           |
|     (Symfony Baseline)        |
+-------------------------------+
```

---

## Dependency Flow

Dependencies flow downward:

- Application Structure depends on Identity
- Application Structure may depend on Capability
- Identity depends on Foundation
- Capability depends on Foundation

Forbidden:

- Capability must NOT depend on Application Structure
- Identity must NOT depend on Application Structure

---

## Composition Model

An application is composed by combining:

- Identity
- Capabilities
- Application Structure

The final system emerges from this composition.

---

## Behavioral Overlay (SXUC)

For UI-based systems:

- Turbo handles immediate interaction
- Mercure propagates state asynchronously

This creates:

- immediate user feedback
- deferred system resolution
- eventual consistency

---

## Key Principle

> Structure defines experience, not identity.

Application Structure determines how the system is used,  
but Identity defines what the system is.

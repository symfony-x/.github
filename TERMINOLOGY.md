# Symfony-X Terminology

## Core Concepts

### Foundation
The minimal Symfony baseline.  
Contains no UI, no persistence, no identity, and no business logic.

---

### Identity Package
Defines the fundamental nature of the application.

Examples:
- symfony-x/ui (SXUC)
- symfony-x/api
- symfony-x/mcp

Rules:
- Identity must be explicitly installed
- Identity defines runtime interaction model
- Multiple identities must not conflict

---

### Capability Package
A bounded, reusable package that provides isolated functionality.

Examples:
- symfony-x/user
- symfony-x/user-oauth
- symfony-x/billing

Rules:
- Must not define application identity
- Must not assume UI/API unless explicitly optional
- Must remain portable across identities

---

### Composition Package
An identity-dependent package that provides a pre-wired application surface.

Examples:
- symfony-x/dashboard

Characteristics:
- Depends on an Identity Package
- Provides default wiring and structure
- Assembles runtime components and capabilities
- Produces a usable application surface

Rules:
- Must be additive, not transformative
- Must declare identity dependency explicitly
- Must not silently redefine application identity

---

### Application Surface
The user-facing interface layer produced by a Composition Package.

---

### Recipe
Install-time automation for package setup.

Responsibilities:
- Enable bundles
- Configure routes/services
- Provide default config

Non-Responsibilities:
- Business logic
- Runtime behavior

---

### Maker
A deterministic code generator.

Responsibilities:
- Generate structure
- Enforce conventions
- Maintain architectural boundaries

---

### Buffer
An external governance layer that validates architectural correctness.

Responsibilities:
- Validate structure
- Enforce rules
- Prevent drift

---

## Key Rules

- Identity must be explicit
- Capabilities must remain isolated
- Compositions may depend on identity and capabilities
- Capabilities must NOT depend on compositions
- Recipes configure, not define
- Makers generate, not decide

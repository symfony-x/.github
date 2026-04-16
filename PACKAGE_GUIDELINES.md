# Package Guidelines

## Package Types

### Identity Packages
Define application nature.

Examples:
- ui
- api
- mcp

---

### Capability Packages
Provide reusable functionality.

Examples:
- user
- oauth
- billing

Must:
- Be independent
- Avoid assumptions about UI/API

---

### Composition Packages
Provide pre-wired application experiences.

Examples:
- dashboard

Must:
- Depend on identity
- Provide usable application surface
- Remain additive

Must NOT:
- Implicitly redefine identity
- Override unrelated packages

---

### Governance Packages
Provide tooling and enforcement.

Examples:
- maker
- recipes
- buffer

---

## Hard Rules

- Capabilities must not depend on compositions
- Compositions may depend on capabilities
- Identity must always be explicit
- No package may silently alter application type

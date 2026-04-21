# Symfony-X Repository Taxonomy

This document classifies the repository types used by Symfony-X.

## 1. Organizational Governance Repository

### Example
- `symfony-x/.github`

### Purpose
Defines organization-wide defaults, public profile content, governance rules, repository planning, and canonical terminology.

### Notes
This is not an implementation repository.

---

## 2. Project Shell Repository

### Example
- `symfony-x/skeleton`

### Purpose
Provides the canonical application shell for new Symfony-X projects.

### Characteristics
- Composer `type: project`
- intended as an application starting point
- minimal baseline
- not a reusable feature bundle

---

## 3. Recipes Infrastructure Repository

### Example
- `symfony-x/recipes`

### Purpose
Stores Symfony Flex recipes separate from package code.

### Characteristics
- recipe-only repository
- deterministic package wiring
- versioned recipe structure
- no application runtime code

---

## 4. Reusable Bundle Repository

### Examples
- `symfony-x/ui-bundle`
- `symfony-x/api-bundle`
- `symfony-x/user-bundle`

### Purpose
Provides reusable Symfony runtime features that can be installed across multiple applications.

### Characteristics
- one primary installable package per repo
- bundle class and Symfony integration
- package name should describe installable responsibility
- should not exist unless the boundary is proven

---

## 5. Mate Extension Repository

### Example
- `symfony-x/mate-extension`

### Purpose
Provides Symfony-X-specific development-time AI tooling through Symfony AI Mate.

### Characteristics
- Composer library
- discovered via Mate extension metadata
- may include tools, resources, prompts, and instructions
- not a runtime AI package

---

## 6. Standards / Tooling Repository

### Example
- `symfony-x/standards`

### Purpose
Provides reusable standards, analysis rules, and validation support for Symfony-X repositories.

### Characteristics
- usually not a Symfony bundle by default
- focuses on code quality and consistency
- may include CI conventions and architecture rules

---

## 7. Deferred Repository Concept

### Examples
- `core`
- `runtime`
- `kernel`
- `contracts`
- `buffer`

### Purpose
These names are acknowledged as concepts or historical explorations, but are not current approved repository types.

### Characteristics
- intentionally not recreated
- may remain archived
- require new justification before returning to the active plan

## Approval Expectations by Type

### Governance Repository
- high review discipline
- architectural review required for canonical doctrine changes

### Project Shell
- high review discipline
- changes should favor stability and minimalism

### Recipes Infrastructure
- changes must be deterministic and installation-safe
- recipe drift should be tightly controlled

### Reusable Bundle
- changes must preserve package responsibility and avoid scope creep

### Mate Extension
- changes must align with Symfony-X AI strategy and avoid unconstrained code generation behavior

### Standards / Tooling
- changes must improve consistency, not add ceremony without value

# Symfony-X Repository Taxonomy

This document classifies the repository types used by Symfony-X.

Symfony-X is an independent community project built for Symfony applications. It is not affiliated with, endorsed by, sponsored by, or maintained by Symfony SAS or the Symfony project. Symfony is a trademark of Symfony SAS.

---

## 1. Organizational Governance Repository

### Example

- `symfony-x/.github`

### Purpose

Defines organization-wide defaults, public profile content, governance rules, repository planning, naming doctrine, and canonical terminology.

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
- contains first-run orientation / setup guide
- not a reusable feature bundle
- not a full distribution

---

## 3. Maintainer Workbench Repository

### Example

- `symfony-x/workbench`

### Purpose

Provides the integration and validation environment where Symfony-X contributors confirm that the package-and-recipe installation path works correctly inside a real Symfony host application.

It is also the primary working environment for Symfony-X-specific AI/Mate tooling.

### Characteristics

- Composer `type: project`
- maintainer-only host application
- not a public starter app
- not a package
- not a reusable bundle
- Mate-enabled by design for Symfony-X development
- distinct from `skeleton`, which is the public project shell
- reusable behavior that originates here should be extracted into a package

---

## 4. Recipes Infrastructure Repository

### Example

- `symfony-x/recipes`

### Purpose

Stores Symfony Flex recipes separate from package code.

### Characteristics

- recipe-only repository
- deterministic package wiring
- versioned recipe structure
- future recipe ownership metadata
- no application runtime code

---

## 5. Reusable Bundle Repository

### Examples

- `symfony-x/ui-bundle`
- `symfony-x/dashboard-bundle`
- `symfony-x/api-bundle`
- `symfony-x/user-bundle`

### Purpose

Provides reusable Symfony runtime features that can be installed across multiple applications.

### Characteristics

- one primary installable package per repo
- bundle class and Symfony integration
- package name describes installable responsibility
- should not exist unless the boundary is proven

---

## 6. UX Bundle Repository

### Example

- `symfony-x/ui-bundle`

### Purpose

Provides frontend assets, Stimulus controllers, Live/Twig components, Turbo defaults, and UI behavior in the Symfony UX style.

### Characteristics

- Symfony bundle
- frontend assets are package-owned where possible
- supports AssetMapper
- supports LAST-stack defaults
- may provide optional presets or adapters
- should remain Symfony-native

---

## 7. AI/Mate Extension Repository

### Example

- `symfony-x/ai-mate-extension`

### Purpose

Provides Symfony-X-specific development-time AI tooling through Mate/MCP-compatible surfaces.

### Characteristics

- Composer library
- vendor-neutral
- may include tools, resources, prompts, and instructions
- provides doctrine propagation
- helps AI assistants inspect and reason about Symfony-X projects
- not a runtime AI package

---

## 8. Optional Vendor Adapter Repository

### Examples

- future `symfony-x/*-mate` adapter packages if needed

### Purpose

Provides optional setup files, prompts, MCP config examples, or guidance for a specific AI client or developer environment.

### Characteristics

- optional
- vendor-specific
- not required by core Symfony-X packages
- must not define Symfony-X architecture

---

## 9. Standards / Tooling Repository

### Example

- `symfony-x/standards`

### Purpose

Provides reusable standards, analysis rules, and validation support for Symfony-X repositories.

### Characteristics

- usually not a Symfony bundle by default
- focuses on code quality and consistency
- may include CI conventions and architecture rules

---

## 10. Deferred Repository Concept

### Examples

- `core`
- `runtime`
- `kernel`
- `contracts`
- `buffer`
- `maker`
- `mcp`

### Purpose

These names are acknowledged as concepts or historical explorations, but are not current approved repository types.

### Characteristics

- intentionally not recreated
- may remain archived
- require new justification before returning to the active plan

---

## Approval Expectations by Type

### Governance Repository

- high review discipline
- architectural review required for canonical doctrine changes

### Project Shell

- high review discipline
- changes should favor stability and minimalism
- first-run guidance should remain practical, honest, and non-hype

### Maintainer Workbench

- changes must serve Symfony-X contributor and maintainer workflow
- changes should improve validation of the package-and-recipe install path
- should not grow into a public install surface or example app
- should not accumulate reusable behavior that belongs in a dedicated package

### Recipes Infrastructure

- changes must be deterministic and installation-safe
- recipe drift should be tightly controlled
- ownership metadata should clarify package responsibility

### Reusable Bundle

- changes must preserve package responsibility
- avoid scope creep
- avoid hiding application-specific product decisions inside reusable packages

### UX Bundle

- changes must remain Symfony UX-compatible
- preserve LAST-stack defaults
- do not assume unnecessary frontend build complexity

### AI/Mate Extension

- changes must align with Symfony-X AI strategy
- avoid unconstrained code generation behavior
- remain vendor-neutral unless the repository is explicitly a vendor adapter

### Optional Vendor Adapter

- must stay optional
- must not define Symfony-X doctrine
- must not be required by the workbench or core packages

### Standards / Tooling

- changes must improve consistency
- avoid ceremony without clear value

---

## Repository Creation Rule

A repository should not be created because a concept sounds important.

A repository should be created only when the install surface, ownership boundary, and validation path are clear.

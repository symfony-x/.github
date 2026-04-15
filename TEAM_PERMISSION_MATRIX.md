# Symfony-X Team Permission Matrix

## Purpose

This document defines **access control, responsibilities, and approval requirements** across all Symfony-X repositories.

It ensures:

- architectural integrity  
- controlled evolution  
- protection against low-quality or agent-generated changes  
- consistent governance enforcement  

---

## Core Principle

Permissions are based on **architectural impact**, not convenience.

The more a repository affects the system, the stricter its controls.

---

## Repository Tiers

### Tier A — Core

Examples:
- `symfony-x/skeleton`
- `symfony-x/recipes`
- `symfony-x/maker`
- `symfony-x/dev-tools`

Impact:
- defines system architecture  
- affects all downstream packages  

---

### Tier B — Identity

Examples:
- `symfony-x/ui`
- `symfony-x/api`
- `symfony-x/mcp`

Impact:
- defines application nature  
- shapes integration patterns  

---

### Tier C — Features

Examples:
- `symfony-x/user`
- `symfony-x/dashboard`
- `symfony-x/admin`
- `symfony-x/user-oauth`
- `symfony-x/oauth-server`

Impact:
- adds composable application capability  

---

### Tier D — Cross-Cutting

Examples:
- `symfony-x/mercure`
- `symfony-x/messenger`
- `symfony-x/testing`

Impact:
- reusable infrastructure integrations  

---

### Tier P — Product

Examples:
- `symfony-x/buffer`

Impact:
- governs the entire ecosystem  
- control-plane authority  

---

## Role Definitions

### Maintainer

- full repository control  
- approves architectural changes  
- enforces constraints  

---

### Trusted Contributor

- can open PRs  
- may be assigned reviews  
- understands Symfony-X architecture  

---

### Contributor

- may propose changes via PR  
- limited permissions  
- requires review for all changes  

---

### AI Agent

- may generate proposals  
- must operate via command system  
- cannot merge or bypass review  

---

## Permission Matrix

### Tier A — Core Repositories

| Role                | Permissions |
|---------------------|------------|
| Maintainer          | Full access |
| Trusted Contributor | PR only |
| Contributor         | PR only (restricted) |
| AI Agent            | PR generation only |

Requirements:

- collaborator-controlled PRs only (no anonymous contributions by default)  
- minimum 2 approvals  
- at least 1 maintainer approval required  
- CODEOWNERS enforced  
- all checks must pass  
- squash merge only  
- direct pushes to main branch prohibited  

---

### Tier B — Identity Repositories

| Role                | Permissions |
|---------------------|------------|
| Maintainer          | Full access |
| Trusted Contributor | PR + review |
| Contributor         | PR only |
| AI Agent            | PR generation only |

Requirements:

- minimum 1–2 approvals  
- maintainer approval required for public contract changes  
- strict review on dependency or API changes  
- all checks must pass  

---

### Tier C — Feature Repositories

| Role                | Permissions |
|---------------------|------------|
| Maintainer          | Full access |
| Trusted Contributor | PR + review |
| Contributor         | PR only |
| AI Agent            | PR generation only |

Requirements:

- minimum 1 approval  
- maintainer review required for:
  - new extension points  
  - public API changes  
- all checks must pass  

---

### Tier D — Cross-Cutting Repositories

| Role                | Permissions |
|---------------------|------------|
| Maintainer          | Full access |
| Trusted Contributor | PR + review |
| Contributor         | PR only |
| AI Agent            | PR generation only |

Requirements:

- minimum 1 approval  
- architectural review required before expanding scope  
- all checks must pass  

---

### Tier P — Product Repositories (Buffer)

| Role                | Permissions |
|---------------------|------------|
| Maintainer          | Full access |
| Trusted Contributor | PR only (restricted) |
| Contributor         | PR only (restricted) |
| AI Agent            | PR generation only |

Requirements:

- collaborator-only PRs  
- minimum 2 approvals  
- mandatory maintainer approval  
- security review required for:
  - authentication  
  - MCP interfaces  
  - command execution paths  
- protected environments for deployment  
- release process required  
- audit logging enforced  

---

## Pull Request Rules

All PRs must:

- pass Dev Tools checks  
- follow PACKAGE_GUIDELINES.md  
- respect CONSTRAINTS.md  
- use Makers for structural changes  
- align with ARCHITECTURE.md  

---

## AI Contribution Policy

AI-generated contributions must:

- follow COMMAND_MAP.md  
- use deterministic Makers  
- not introduce structural code manually  
- be reviewed as untrusted input  

### Rule

AI output is treated as **untrusted until validated**.

---

## Approval Rules

### Standard Changes

- meet minimum approval count  
- pass all checks  
- no architectural violations  

---

### Architectural Changes

Require:

- maintainer approval  
- alignment with architecture documents  
- cross-repo impact analysis  

---

### Governance Changes

Require:

- maintainer consensus  
- update to `.github` documentation  
- validation of enforcement implications  

---

## Branch Protection

All repositories must enforce:

- protected default branch  
- required status checks  
- required reviews  
- no force pushes  
- no direct commits to main  

---

## Repository Creation Permissions

Only maintainers may:

- create new repositories  
- define repository tier  
- assign governance level  

### Rule

New repositories must align with:

- REPOSITORY_TAXONOMY.md  
- ARCHITECTURE.md  

---

## Escalation Model

If a change:

- affects multiple repositories  
- modifies architecture  
- introduces new patterns  

It must be escalated to maintainers.

---

## Enforcement Integration

Permissions are enforced through:

- GitHub branch protection rules  
- CI/CD checks  
- Dev Tools validation  
- Buffer governance (when integrated)  

---

## Anti-Patterns

Forbidden:

- bypassing review requirements  
- merging failing checks  
- granting excessive permissions  
- allowing uncontrolled PRs  
- accepting AI-generated code without validation  

---

## Guiding Principle

Access is granted based on system impact.

The closer a repository is to the architecture, the stricter its control.

# File: .github/REPOSITORY_TAXONOMY.md

# Symfony-X Repository Taxonomy

## Tier A — Core Architecture Repositories

Examples:
- symfony-x/core
- symfony-x/runtime
- symfony-x/contracts
- symfony-x/kernel
- symfony-x/event-system
- symfony-x/messaging

Policy:
- collaborator-only PRs
- 2 approvals minimum
- CODEOWNERS required
- architect signoff required

## Tier B — Platform Extensions

Examples:
- symfony-x/mercure-bridge
- symfony-x/messenger-adapters
- symfony-x/cognito-bundle
- symfony-x/google-cloud-runtime

Policy:
- trusted contributors allowed
- 1 to 2 approvals
- maintainer review required

## Tier C — UX / Toolkit Layer

Examples:
- symfony-x/ux-abstractions
- symfony-x/ui-flowbite
- symfony-x/ui-shadcn
- symfony-x/live-components-plus

Policy:
- trusted contributors may submit PRs
- API changes require architect review

## Tier D — Community Contribution Repositories

Examples:
- symfony-x/docs
- symfony-x/examples
- symfony-x/recipes
- symfony-x/starter-kits

Policy:
- public PRs allowed
- triage-first review queue

## Tier E — Experimental Labs

Examples:
- symfony-x/labs-agent-routing
- symfony-x/labs-event-sourcing
- symfony-x/labs-reactive-runtime

Policy:
- invite-only contributors
- unstable branch model allowed

## Tier F — Internal Infrastructure

Examples:
- symfony-x/release-engineering
- symfony-x/security-advisories
- symfony-x/deployment-infra

Policy:
- maintainers only

## Default PR Access by Tier

| Tier | Outside Public PRs |
|------|--------------------|
| A | No |
| B | Limited |
| C | Limited |
| D | Yes |
| E | No |
| F | No |

## Branch Protection Standards

### Tier A
- 2 approvals required
- latest push approval required
- stale approvals dismissed
- CODEOWNERS required
- strict CI required

### Tier B / Tier C
- 1 to 2 approvals required
- CI required
- CODEOWNERS required

### Tier D
- 1 approval required
- basic CI required
- maintainer merge only

### Tier E
- maintainer discretion

### Tier F
- maintainers only
- restricted branch pushes

## Initial Suggested Repositories

- .github
- core
- contracts
- runtime
- docs
- examples
- recipes
- ux-abstractions
- mercure-bridge
- labs

# File: .github/TEAM_PERMISSION_MATRIX.md

# Symfony-X Team Permission Matrix

## Teams

- core-architects
- maintainers
- trusted-contributors
- triage-team
- docs-team
- integration-team
- security-reviewers
- release-managers
- community-moderators

## Permissions

| Team | Org Role | Core Repos | Extension Repos | Docs Repos | Infra Repos |
|------|----------|------------|-----------------|------------|-------------|
| core-architects | Admin | Admin | Admin | Admin | Admin |
| maintainers | Member | Maintain | Maintain | Maintain | Maintain |
| trusted-contributors | Member | Write (selected) | Write | Write | None |
| triage-team | Member | Triage | Triage | Triage | None |
| docs-team | Member | Read | Read | Write | None |
| integration-team | Member | Read | Maintain | Write | None |
| security-reviewers | Member | Read | Read | None | Maintain |
| release-managers | Member | Read | Read | None | Maintain |
| community-moderators | Member | None | None | Triage | None |

## Responsibilities

### core-architects
Approves:
- architecture changes
- public API changes
- package splits and merges

### maintainers
Responsible for:
- merge decisions
- release cadence
- enforcing contribution policy

### trusted-contributors
Can:
- submit code to approved repos
- review limited pull requests

Cannot:
- override architecture decisions

### triage-team
Responsible for:
- filtering low-quality PRs
- handling spam issues
- identifying duplicates
- protecting maintainers from review overload

### docs-team
Responsible for:
- documentation repos
- guides
- onboarding materials

### integration-team
Responsible for:
- adapters
- bridges
- third-party integrations

### security-reviewers
Responsible for:
- dependency audits
- vulnerability review
- sensitive security-related changes

### release-managers
Responsible for:
- release tagging
- changelog validation
- version coordination

### community-moderators
Responsible for:
- discussions moderation
- issue conduct enforcement

# Security Policy

Symfony-X takes security seriously, especially anywhere AI-assisted tooling, recipes, generated files, local development tools, or agent experiments are involved.

Symfony-X is an independent community project built for Symfony applications. It is not affiliated with, endorsed by, sponsored by, or maintained by Symfony SAS or the Symfony project. Symfony is a trademark of Symfony SAS.

---

## Reporting Security Issues

Please do not disclose security vulnerabilities publicly before maintainers have had a chance to review them.

Use the repository's private vulnerability reporting feature where available, or contact the maintainers through the appropriate private channel listed for the specific repository.

Include:

- affected repository
- affected package/version if known
- reproduction steps
- impact summary
- suggested mitigation if available

---

## Scope

This policy applies to Symfony-X repositories and packages, including:

- skeleton setup concerns
- recipes and installation wiring
- bundle behavior
- development tooling
- AI/Mate tooling
- standards and validation tooling
- sandboxed agent experiments

This policy does not replace Symfony's own security reporting process for Symfony framework vulnerabilities.

---

## AI and Agent Security

AI-assisted tooling must not be treated as a trusted host-level operator.

Agentic workflows and external runtimes must be sandboxed by default.

Expected posture:

- Docker sandbox for agent runtimes
- restricted egress
- no raw host access
- no production secrets
- no writable access to real Symfony-X repositories by default
- explicit user control for mutation
- auditable command output

Symfony-X should prefer one agent/runtime at a time by default. Advanced users may opt into more complex setups intentionally.

---

## Recipes and Generated Files

Recipes and generators can affect host applications.

Security-sensitive changes should be:

- explicit
- deterministic
- minimal
- reviewable
- reversible where practical

Recipes should not silently introduce unsafe defaults.

---

## Supported Versions

Symfony-X is currently pre-stable and in foundation-building mode.

Security expectations apply to active repositories, but formal version support windows may be defined later per package.

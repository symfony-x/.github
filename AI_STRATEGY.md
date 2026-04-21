# Symfony-X AI Strategy

## Current Direction

Symfony-X now uses **Symfony AI Mate** as the primary development-time AI integration surface.

This is a deliberate shift away from centering AI-assisted development around a custom Maker scaffolding strategy.

## Development-Time AI

Development-time AI is about helping a developer work on the codebase locally.

In Symfony-X, this should be handled through:

- Symfony AI Mate
- Symfony-X Mate extensions
- tool/resource/prompt-based guidance
- instruction files and explicit repository context
- standards and validation to constrain drift

### What This Replaces

Symfony-X no longer treats custom Maker-based scaffolding as the main AI control surface.

Maker may still exist for normal developer ergonomics where it is useful, but it is no longer the governing AI strategy.

### Development-Time Goals

Development-time AI in Symfony-X should:

- understand the codebase and package boundaries
- follow Symfony-X terminology and naming rules
- prefer recipes and existing install surfaces over improvised structure
- reduce architectural drift
- help developers work faster without bypassing constraints

## Runtime AI

Runtime AI is separate from Mate.

Runtime AI includes AI behavior that executes inside the running application itself, such as:

- agent workflows
- chat interfaces
- runtime tools
- provider integration
- application-level AI orchestration

Symfony-X should treat runtime AI as its own package concern and not blur it with development-time tooling.

## Repository Implications

### `symfony-x/mate-extension`

This repository is the primary home for Symfony-X development-time AI integration.

It should contain Symfony-X-specific:

- Mate tools
- Mate resources
- Mate prompts
- instructions
- local development guidance
- architecture-aware assistance surfaces

### `symfony-x/agent-runtime-bundle`

This repository is deferred until Symfony-X has a clearly defined reusable runtime AI layer.

## Doctrine

Symfony-X AI doctrine is now:

- **Mate for development-time AI**
- **recipes for deterministic install-time wiring**
- **standards for validation and consistency**
- **runtime AI treated separately from development tooling**

## Guardrails

AI usage in Symfony-X should never become a justification for:

- uncontrolled repository sprawl
- freeform architectural invention
- bypassing package boundaries
- hiding complexity inside vague abstractions

AI should accelerate work inside the architecture, not dissolve the architecture.

# SXUC Architecture

## Purpose

This document defines the architecture of **SXUC** (`symfony-x/ui`).

SXUC is not a UI library.

It is the **governed async UX substrate** for UI-first Symfony-X applications.

---

## Core Principle

> **In SXUC, Turbo governs the immediate request-response interaction cycle, while Mercure governs deferred real-time state propagation back into the UI.**

---

## SXUC Invariants

SXUC is built on:

- Live Components
- AssetMapper
- Stimulus
- Turbo
- Mercure

These are architectural invariants.

---

## Runtime Model

### Immediate UX Path

- user action
- Turbo / Live request
- immediate response
- UI update

---

### Deferred Completion Path

- background processing
- domain event
- Mercure publish
- Turbo Stream update

---

## Ownership

SXUC owns:

- async UI transport semantics
- Turbo/Mercure interaction model
- UI-first identity behavior
- LAST stack integration
- async-aware Makers
- preset resolution

---

## Topic Conventions

Examples:

- `/sxuc/component/{id}`
- `/sxuc/user/{id}`
- `/sxuc/job/{id}`
- `/sxuc/resource/{type}/{id}`

---

## Preset Model

Presets:

- `none`
- `shadcn`
- `flowbite`

### Presets MAY:

- define markup
- define styling

### Presets MUST NOT:

- redefine async transport
- change runtime model

---

## Maker Requirements

SXUC Makers must generate:

- Turbo-ready templates
- predictable DOM targets
- async-aware structure

---

## Guiding Principle

SXUC defines how UI behaves over time.

Not just how it renders.

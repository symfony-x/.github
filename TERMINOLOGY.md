# Symfony-X Terminology Specification

This document defines the canonical terminology for Symfony-X.

> Goal: eliminate ambiguity, enforce consistency, and improve determinism for developers and AI-assisted workflows.

---

# 1. Core Actors

## Developer

A **Developer** is a person building an application using Symfony-X.

- installs packages
- writes code
- configures the system

Never refer to Developers as “Users”.

---

## Application User

An **Application User** is a person using the application built with Symfony-X.

Examples:
- customer
- admin user
- end-user of the app

---

## User Entity

The **User Entity** is the internal representation of an Application User in code.

Examples:
- `App\Entity\User`
- database records

---

# 2. Identity & Authentication

## Account

**Account** is the UI-facing term for an Application User.

Use in:
- UI (“My Account”)
- documentation when discussing user-facing concepts

---

## External Identity

An **External Identity** is identity data provided by an external system.

Examples:
- Google account
- GitHub account

---

## OAuth Provider

An **OAuth Provider** is a third-party system that authenticates users.

Examples:
- Google
- GitHub

---

## OAuth Account

An **OAuth Account** links an External Identity to a User Entity.

---

## Auth Session

An **Auth Session** is the authenticated session managed by Symfony Security.

---

# 3. Architecture & Packaging

## Package

A **Package** is a Composer package.

Examples:
- `symfony-x/user`
- `symfony-x/user-oauth`

---

## Bundle

A **Bundle** is a Symfony-specific code structure.

This is an internal implementation detail, not a product concept.

---

## Feature Module

A **Feature Module** is a Symfony-X concept:

> an installable package that provides a complete feature with backend and UI.

Examples:
- `symfony-x/user`
- `symfony-x/admin`

---

## Starter Stack

A **Starter Stack** is a curated set of Feature Modules.

Examples:
- `symfony-x/starter-saas`
- `symfony-x/starter-user`

---

# 4. Security & Authorization

## Security Role

A **Security Role** is used by Symfony Security.

Examples:
- `ROLE_USER`
- `ROLE_ADMIN`

---

## Permission

A **Permission** represents business-level authorization.

It is not tied directly to Symfony roles and is used in domain logic.

---

# 5. Async & Messaging

## Message

A **Message** is a unit of work handled by Symfony Messenger.

---

## Async Job

An **Async Job** is a Message processed asynchronously.

---

## Worker

A **Worker** is a process that consumes Messages.

---

## Domain Event

A **Domain Event** represents something that happened in the business domain.

---

# 6. Frontend & Interaction

## UI State

**UI State** refers to the state of the frontend.

---

## Entity State

**Entity State** refers to the state of domain objects.

---

## UI Event

A **UI Event** is a frontend interaction.

Examples:
- click
- form submit

---

# 7. Networking & Integration

## HTTP Client

Used for making HTTP requests.

---

## OAuth Client

Credentials or configuration used to communicate with an OAuth Provider.

---

## Browser

The frontend runtime environment.

---

# 8. Tokens

All tokens must be explicitly qualified.

Use:
- CSRF Token
- Access Token
- Refresh Token
- API Token
- Reset Token

Never use “token” alone.

---

# 9. Sessions & Context

## Browser Session

The session managed by the browser.

---

## Auth Session

The authenticated session.

---

## Context

Context must always be qualified.

Examples:
- Security Context
- Request Context
- AI Context

---

# 10. AI Concepts

## AI Agent

An **AI Agent** is an autonomous system component.

---

## Worker

A **Worker** is not an AI Agent.

- Worker = executes jobs
- AI Agent = makes decisions

---

# 11. Environment

## App Environment

Defined by `APP_ENV`.

Examples:
- `dev`
- `prod`

---

## Deployment Environment

Infrastructure-level environment.

Examples:
- local
- staging
- production

---

# 12. Naming Rules

## Always Qualify Ambiguous Terms

If a term has multiple meanings, it must be qualified.

Examples:
- not `token`
- use `Access Token`

- not `client`
- use `OAuth Client`

---

## Avoid Overloading Terms

One term should have one meaning within Symfony-X documentation and architecture.

---

## Prefer Explicitness Over Brevity

Clarity is more important than short names.

---

# 13. Canonical Mental Model

    Developer
        ↓
    Application (Symfony-X)
        ↓
    Application User
        ↓
    User Entity

---

# 14. Guiding Principle

> If a word can mean more than one thing, it must be disambiguated.

---

# 15. Enforcement

This document applies to:
- package naming
- code, including classes and interfaces
- documentation
- generators and Maker commands
- AI prompts and outputs

---

# 16. Philosophy

Symfony-X prioritizes:
- determinism
- clarity
- composability
- reduced ambiguity
- AI-friendly structure

---

End of Specification

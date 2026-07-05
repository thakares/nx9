# NX9 Roadmap

> **Engineering Beyond Frameworks**
>
> *Building a complete ecosystem of self-hosted, privacy-first, single-binary applications.*

---

# Vision

NX9 is not a single application.

It is an ecosystem of independent, interoperable, self-hosted tools designed around a common engineering philosophy:

* Build only what is necessary.
* Avoid unnecessary frameworks.
* Minimize dependencies.
* Keep deployments simple.
* Respect user privacy.
* Eliminate vendor lock-in.
* Remain fully open source.

Every project should be deployable in minutes, understandable by a single engineer, and maintainable for years—not months.

---

# Core Principles

Every NX9 project follows the same architectural principles.

## Privacy First

No telemetry.

No tracking.

No analytics.

Your data belongs to you.

---

## Self-Hosted First

Cloud deployment is optional.

Self-hosting is the default.

Users should own their infrastructure.

---

## Linux Native

Linux is the primary deployment platform.

Applications should feel like first-class Linux software.

---

## Rust Native

Rust provides:

* predictable performance
* memory safety
* modern tooling
* excellent concurrency
* minimal runtime requirements

---

## Single Binary Applications

Whenever practical:

* one executable
* one configuration directory
* one service
* one deployment

No dependency on heavyweight runtime ecosystems.

---

## Explicit Over Implicit

Nothing should happen "by convention."

Routes.

Configuration.

Permissions.

Features.

Everything should be explicit.

---

## Minimal Dependencies

Dependencies are engineering decisions—not conveniences.

Every dependency:

* increases maintenance
* expands attack surface
* introduces supply-chain risk

If a problem can be solved internally with reasonable effort, that may be preferable to importing another dependency.

---

## Operational Simplicity

Deployment should be boring.

Installation should be boring.

Upgrades should be boring.

Reliability is more valuable than cleverness.

---

# Current Projects

## BZOD

**Status:** Stable

Privacy-first URL shortener.

Features include:

* custom aliases
* QR codes
* expiration
* password protection
* analytics
* audit logs
* REST API
* SQLite
* PostgreSQL
* Docker
* single-binary deployment

---

## nx9-auth

**Status:** Active Development

Authentication platform designed for self-hosted applications.

Goals include:

* OAuth2
* OpenID Connect
* JWT
* session management
* user management
* API authentication
* SSO for NX9 ecosystem

---

## ChronoSeal

**Status:** Planned

Digital timestamping platform.

Goals:

* trusted timestamping
* immutable records
* hash verification
* document integrity
* long-term verification

---

# Planned Ecosystem

The long-term objective is a cohesive ecosystem where every application shares the same design philosophy and integrates naturally with the others.

Potential projects include:

## File Sharing

Simple.

Fast.

Self-hosted.

No unnecessary complexity.

---

## Password Manager

Encrypted.

Offline-first.

Self-hostable.

---

## Notification Service

Email.

Webhooks.

Push.

Simple API.

---

## Monitoring Dashboard

Infrastructure monitoring.

System health.

Container health.

Notifications.

---

## Documentation Platform

Markdown-first.

Fast.

Searchable.

Single binary.

---

## Workflow Automation

Simple automation engine for self-hosted infrastructure.

Designed for practical administration rather than enterprise complexity.

---

# Technical Direction

## Frontend

Preference for:

* HTML5
* CSS3
* Vanilla JavaScript

JavaScript frameworks should only be introduced when they solve demonstrable engineering problems.

---

## Backend

Primary language:

* Rust

Preferred characteristics:

* async
* efficient
* predictable
* memory safe

---

## Database

Primary:

* SQLite

Optional:

* PostgreSQL

Applications should not require a database server unless the workload justifies it.

---

## APIs

REST-first.

JSON.

Well documented.

Versioned.

Simple.

---

## Deployment

Supported environments:

* Linux
* Docker
* Podman

Future consideration:

* FreeBSD

---

## Reverse Proxy

Recommended:

* Nginx

Applications should work behind any standards-compliant reverse proxy.

---

# Security Philosophy

Security begins with architecture.

NX9 emphasizes:

* explicit routing
* reduced attack surface
* minimal dependencies
* least privilege
* secure defaults
* modern cryptography
* reproducible builds

Security features should emerge naturally from good engineering—not from accumulating layers of defensive software.

---

# Non-Goals

NX9 does **not** aim to:

* replace every web framework;
* eliminate JavaScript;
* compete with enterprise platforms;
* build monolithic "all-in-one" systems;
* chase technology trends;
* optimize for resume-driven development.

The objective is thoughtful engineering, not ideological minimalism.

---

# Design Philosophy

Every new feature should answer three questions:

1. Does it solve a real problem?
2. Can it be implemented simply?
3. Does it increase long-term maintenance disproportionately?

If the answer to the third question is **yes**, the feature should be reconsidered.

---

# Success Criteria

A successful NX9 application should be:

* understandable by reading the source;
* deployable within minutes;
* maintainable by a small team—or even a single developer;
* performant without extraordinary hardware;
* secure through simplicity;
* pleasant to operate.

---

# Community Principles

NX9 welcomes contributions that align with its philosophy.

Preferred contributions include:

* bug fixes
* documentation
* accessibility improvements
* performance optimizations
* security improvements
* interoperability
* code simplification

Contributions that significantly increase complexity without corresponding long-term value may not align with the project's direction.

---

# Looking Forward

The goal of NX9 is not to build the largest software ecosystem.

It is to build one of the most coherent.

Every project should feel familiar.

Every deployment should feel predictable.

Every application should respect the user's ownership of their data and infrastructure.

The roadmap will continue to evolve as new ideas emerge, but one principle will remain unchanged:

> **Choose the simplest architecture capable of solving the problem well.**

Because software should empower its users—not burden them with unnecessary complexity.

---

**NX9**

*Engineering Beyond Frameworks.*
*Build only what you need.*
*Deploy only what you trust.*
*Maintain only what you own.*

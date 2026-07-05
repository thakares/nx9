# NX9

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://nx9.in/logo-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="https://nx9.in/logo-light.svg">
  <img src="https://nx9.in/logo-light.svg" width="320" alt="NX9 Logo">
</picture>

**NX9 (Next Generation 9)** is an ecosystem of independent, open-source, self-hosted software built in Rust.

Every project follows the same philosophy:

> **Infrastructure should belong to its operator—not to a cloud provider, subscription service, or vendor.**

NX9 develops software that is lightweight, privacy-first, Linux-native, and designed to remain understandable, maintainable, and deployable for years—not just until the next framework trend arrives.

---

## Philosophy

Modern software has become increasingly dependent on cloud platforms, proprietary services, massive dependency trees, and unnecessary complexity.

NX9 takes the opposite approach.

Every project is designed to be:

- Self-hostable
- Privacy-first
- Single-binary whenever practical
- Linux-native
- Lightweight
- Open source
- Easy to deploy
- Easy to understand
- Free from vendor lock-in

Rather than building one monolithic platform, NX9 consists of independent applications that each solve a single problem well while sharing the same engineering philosophy.

---

## Projects

Current projects under the NX9 ecosystem include:

### nx9-url-shortener

A modern multi-user URL shortener featuring:

- Analytics
- QR codes
- Password protection
- Link expiration
- Tenant isolation
- REST API
- SQLite-first architecture

Repository:

- https://github.com/thakares/nx9-url-shortener
- https://codeberg.org/thakares/nx9-url-shortener

---

### nx9-auth

Lightweight identity and access management.

Features include:

- User authentication
- Sessions
- Personal Access Tokens (PATs)
- RBAC
- Audit logging
- Multi-tenant support

Repository:

- https://github.com/thakares/nx9-auth
- https://codeberg.org/thakares/nx9-auth

---

### nx9-dns-server

An authoritative DNS server designed for self-hosted infrastructure.

Features:

- DNSSEC
- Zone management
- Lightweight architecture
- Rust implementation

Repository:

- https://github.com/thakares/nx9-dns-server
- https://codeberg.org/thakares/nx9-dns-server

---

### nx9-chronoseal-rs

A privacy-first browser attestation framework that helps distinguish legitimate browsers from automated abuse without invasive tracking.

Repository:

- https://github.com/thakares/nx9-chronoseal-rs
- https://codeberg.org/thakares/nx9-chronoseal-rs

---

## Engineering Principles

Every NX9 project follows these principles:

- Single-purpose applications
- Explicit routing over magic
- SQLite-first whenever appropriate
- Minimal dependencies
- Predictable deployment
- Human-readable configuration
- Secure by default
- Long-term maintainability
- Open standards
- Backward compatibility whenever practical

---

## Documentation

- Architecture Overview
- Roadmap
- Engineering Philosophy
- Design Decisions

(Detailed documentation will continue to expand as the ecosystem grows.)

---

## Website

Official website:

**https://nx9.in**

The website source is maintained in this repository under `www/`.

---

## Core Values

- Privacy First
- Operator Ownership
- Simplicity Over Complexity
- Linux Native
- Open Source
- Single Binary
- Explicit Design
- No Telemetry
- No Vendor Lock-in
- Long-Term Stability

---

## Contributing

Bug reports, documentation improvements, feature requests, and code contributions are all welcome.

If you believe software should remain understandable, deployable, and fully controlled by its users, you'll feel at home in the NX9 ecosystem.

---

## Links

- Website: https://nx9.in
- GitHub: https://github.com/thakares
- Codeberg: https://codeberg.org/thakares

---

**NX9**

**Software people can own, understand, and control.**
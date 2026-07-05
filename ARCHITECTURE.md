# NX9 Architecture

## A Philosophy-Driven Ecosystem for Self-Hosted Infrastructure

**NX9** is an ecosystem of independent, philosophically aligned infrastructure software built by Sunil Thakare (@thakares).

Every project is designed around one simple idea:

> **Infrastructure should belong to its operator — not to a cloud provider, subscription service, or vendor.**

NX9 is not a framework.  
It is not a platform that requires dozens of services.  
It is not a cloud product that happens to support self-hosting.

Instead, NX9 is a collection of carefully engineered **single-binary Rust applications** that prioritize:

- Privacy
- Simplicity
- Reliability
- Performance
- Operational Excellence
- Long-term Maintainability

Every application is fully open-source, Linux-native, resource-efficient, and designed to run equally well on Raspberry Pi, mini PCs, VPS instances, enterprise servers, air-gapped government infrastructure, or personal homelabs.

**No telemetry. No vendor lock-in. No mandatory cloud. No unnecessary complexity.**

---

## Design Philosophy

The NX9 ecosystem follows several consistent principles across every project.

### 1. Operator Ownership

The operator owns the binaries, the configuration, the databases, the backups, the encryption keys, and the deployment.

No service depends on proprietary APIs or cloud-hosted control planes.

### 2. Self-Hosting First

Every architectural decision begins with one question:

> "Can this be deployed and operated by a single administrator?"

If the answer requires Kubernetes, managed databases, cloud messaging, or external dependencies, the design is reconsidered.

### 3. Simplicity Over Complexity

NX9 intentionally avoids fashionable complexity. Instead of dozens of microservices, service meshes, or distributed databases, NX9 prefers:

- One binary
- One configuration
- One (or a few) SQLite databases
- One administrator

Simple systems are easier to understand, secure, and recover.

### 4. Privacy by Default

Privacy is a design requirement, not an optional feature. Applications never assume cloud connectivity, analytics collection, or third-party tracking.

### 5. Security by Design

Security is embedded throughout the stack:

- Argon2id password hashing
- Ed25519 signatures
- BLAKE3 hashing
- RBAC
- CSRF protection
- Secure cookies
- Transaction-safe audit logs
- Hardened compilation flags

### 6. Operational Excellence

Every project includes:

- Diagnostics and health checks
- Backup and restore procedures
- Migration tools
- CLI administration
- Reproducible deployments
- Structured logging
- Documentation

### 7. Long-Term Stability

NX9 intentionally avoids dependency churn. Projects are expected to remain understandable and maintainable years into the future.

---

## Core Architectural Pillars

### 1. Pure Rust

All projects are implemented in modern Rust (2021 Edition) for memory safety, predictable performance, and minimal runtime overhead. Typical binaries are around 10–12 MB.

### 2. Single Binary Deployment

One executable contains the HTTP server, business logic, authentication, database migrations, CLI, and templates.

Installation is often as simple as:

```bash
cargo build --release
./application serve
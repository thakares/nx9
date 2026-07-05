# NX9

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://nx9.in/icon-dark.svg">
  <img src="https://nx9.in/logo.svg" width="300" alt="NX9 Logo">
</picture>

**Next Generation 9** — A philosophy-driven ecosystem of self-hosted, privacy-first software.

Every project is built around one core idea:

> **Infrastructure should belong to its operator — not to a cloud provider, subscription service, or vendor.**

### Philosophy

NX9 is not a framework or a platform. It is a collection of independent, single-binary Rust applications designed for:

- Operator ownership
- Privacy by default
- Self-hosting first
- Simplicity over complexity
- Long-term maintainability
- Zero telemetry or vendor lock-in

We deliberately choose minimal dependencies, explicit routing, SQLite-first storage, and Linux-native design. The goal is software that is easy to understand, deploy, operate, and trust — even years from now.

### Core Projects

- **[nx9-url-shortener](https://codeberg.org/thakares/nx9-url-shortener)**  
  Multi-user URL shortener with analytics, QR codes, password protection, expiration, and tenant isolation.

- **[nx9-auth](https://codeberg.org/thakares/nx9-auth)**  
  Lightweight identity and access management service with sessions, PATs, RBAC, and audit logging.

- **[nx9-dns-server](https://codeberg.org/thakares/nx9-dns-server)**  
  Authoritative DNS server with DNSSEC support. Lightweight and designed for self-hosted use.

- **[nx9-chronoseal-rs](https://codeberg.org/thakares/nx9-chronoseal-rs)**  
  Privacy-first browser attestation framework for anti-bot and anti-AI scraping protection.

### Documentation

- [Philosophy → Engineering Beyond Frameworks](https://nx9.in/case-study.html)
- [Architecture Overview](ARCHITECTURE.md)
- [Case Study: How Simplicity Defended Against Real Attacks](https://nx9.in/case-study.html)
- [Roadmap](ROADMAP.md)

### Website

The full website source is available in the [`www/`](www/) directory.

### Values

- Privacy by design
- Single binary deployments
- Explicit routing
- Operator sovereignty
- Open Source (permissive licenses)
- No telemetry. No vendor lock-in.

### Get Involved

- Star or fork the projects you find useful
- Open issues or discussions for feedback
- All projects are independent but share the same architectural principles

---

**NX9** — Software people can own, understand, and control.

Built by [Sunil Thakare](https://codeberg.org/thakares).
# Local Management Interface

## Overview

NX9 follows a **CLI-first** philosophy.

Every application is designed to be fully manageable from the command line. The CLI is considered the authoritative interface for administration, automation, scripting, backups, diagnostics, and system integration.

To complement—not replace—the CLI, every NX9 application may expose a **Local Management Interface**: a lightweight web UI intended exclusively for administrators operating on the local machine.

Unlike traditional web applications, the Local Management Interface is **never intended for public access**. It is bound only to the loopback interface (`127.0.0.1`) and provides a graphical representation of the same administrative capabilities already available through the CLI.

The web interface exists purely for convenience and visualization. It should never become a dependency for operating an NX9 application.

---

# Motivation

Most modern web applications expose both public and administrative functionality through the same web server.

```
Internet
     │
     ▼
 Public Web Server
     │
 ┌───┴──────────────┐
 │                  │
 ▼                  ▼
Public Pages    Admin Pages
                Debug APIs
                Metrics
                Configuration
                Logs
```

These administrative endpoints are typically protected using:

- Authentication
- Authorization
- Middleware
- Reverse proxies
- VPNs
- Firewalls

While effective, this approach increases complexity and permanently enlarges the public attack surface.

NX9 takes a different approach.

Administrative functionality simply does **not exist** on the public interface.

---

# Architecture

Each NX9 application exposes two completely independent interfaces.

```
                    Internet
                        │
                        ▼
         Public Interface (0.0.0.0:<base-port>)
                        │
                        ▼
                 Public Router
                        │
        ┌───────────────┴───────────────┐
        │                               │
   Static Website                 Public APIs
        │                               │
        ▼                               ▼
   End Users                      API Clients


──────────────────────────────────────────────────────


                  Local Machine
                        │
                        ▼
 Local Management Interface (127.0.0.1:<base-port+1>)
                        │
                        ▼
                  Admin Router
                        │
      ┌─────────────┼─────────────┐
      │             │             │
 Dashboard      Diagnostics    Configuration
 Logs           Health         Maintenance
 Metrics        Backup         Monitoring
```

Each interface owns its own TCP listener and its own HTTP router.

The application core remains shared.

---

# Two Independent TCP Listeners

A typical implementation looks like:

```rust
let public = TcpListener::bind("0.0.0.0:8654").await?;
let admin  = TcpListener::bind("127.0.0.1:8655").await?;
```

Both listeners execute within the same process.

No second daemon.

No management service.

No sidecar container.

No IPC.

One executable.

One process.

Two trust boundaries.

---

# Public Interface

The public listener serves Internet-facing functionality.

Typical routes include:

```
/
robots.txt
sitemap.xml
API endpoints
Public documentation
Static assets
```

Nothing more.

No dashboards.

No configuration.

No maintenance.

No diagnostics.

No hidden administration pages.

---

# Local Management Interface

The local listener provides a graphical representation of administrative functionality.

Typical capabilities include:

- Dashboard
- Application status
- Runtime metrics
- Memory usage
- CPU utilisation
- Active connections
- Live logs
- Configuration viewer
- Configuration editor
- Database browser
- Backup & Restore
- Maintenance operations
- Health monitoring
- Diagnostics
- Version information
- Build information

Everything accessible through the Local Management Interface should also be available through the CLI.

The web UI is an additional convenience layer—not an alternative management interface.

---

# CLI First

The CLI remains the primary interface for:

- Automation
- Scripting
- SSH administration
- CI/CD pipelines
- Cron jobs
- Disaster recovery
- Headless deployments

Typical workflow:

```
Automation
Scripts
SSH
CI/CD
        │
        ▼
       CLI
        │
        ▼
 Application Core
        ▲
        │
Local Management Interface
```

An NX9 application must remain fully operable without ever opening a browser.

---

# Security Model

NX9 intentionally separates administration from public services.

Administrative routes are never registered on the public listener.

For example, the following routes may exist only on the Local Management Interface:

```
/dashboard
/config
/logs
/metrics
/backup
/database
/maintenance
/diagnostics
```

A request arriving on the public interface can never reach these endpoints because they simply do not exist within the public router.

There is nothing to authenticate.

Nothing to authorize.

Nothing to accidentally expose.

This follows one of the fundamental NX9 principles:

> **The smallest attack surface is the one that was never exposed.**

---

# Why Not Authentication?

Authentication remains valuable when multiple local users require different permissions.

However, authentication should not compensate for architectural decisions.

Instead of exposing administration endpoints publicly and protecting them with increasingly complex security layers, NX9 removes them from the public interface entirely.

The Internet cannot attack endpoints that do not exist.

---

# Design Principles

The Local Management Interface follows several architectural principles.

## CLI First

The CLI remains the complete administrative interface.

The web UI complements it.

---

## Network-Level Isolation

Administrative functionality exists only on the loopback interface.

No Internet exposure.

No reverse proxy.

No TLS requirement.

No public routing.

---

## Single Binary

Every NX9 application remains a single executable.

The management interface is built into the application itself.

---

## Lightweight

The management interface should be:

- HTML5
- CSS3
- Vanilla JavaScript

No frontend frameworks.

No Node.js runtime.

No build pipeline.

No npm dependencies.

---

## Responsive

The interface should function equally well on:

- Desktop
- Tablet
- Mobile browser

Administrators should be able to inspect an application quickly from any modern browser.

---

# Typical Features

The Local Management Interface may provide:

## System

- Application information
- Version
- Build date
- Uptime
- Runtime

## Monitoring

- CPU
- Memory
- Active sessions
- Connections
- Queue sizes

## Logging

- Live logs
- Error logs
- Audit logs
- Request logs

## Database

- Browse records
- Execute maintenance
- Backup
- Restore

## Configuration

- View configuration
- Edit configuration
- Reload configuration

## Diagnostics

- Health checks
- Dependency status
- Environment
- Runtime diagnostics

---

# Suggested Port Convention

NX9 applications commonly reserve consecutive ports.

| Application | Public | Local Management |
|------------|--------:|-----------------:|
| BZOD | 8654 | 8655 |
| ChronoSeal | 8383 | 8384 |
| nx9-auth | 9010 | 9011 |
| IoT Hub | 18800 | 18801 |

This convention keeps deployments predictable while remaining easy to remember.

---

# Future Possibilities

Future NX9 applications may expose lightweight machine-readable metadata.

Example:

```
GET /.nx9/status
```

```json
{
    "application": "BZOD",
    "version": "0.5.3",
    "status": "healthy",
    "uptime": "18d 07h",
    "database": "SQLite"
}
```

This would enable a future **NX9 Local Dashboard** to automatically discover and monitor every NX9 application running on a machine.

Because every application follows the same architecture, discovery becomes trivial.

---

# Philosophy

The Local Management Interface embodies several core NX9 principles.

- **CLI-first**
- **Web UI as a convenience**
- **Network-level isolation**
- **Single binary deployment**
- **Minimal attack surface**
- **No unnecessary dependencies**
- **Operational simplicity**

Rather than protecting administrative functionality behind increasingly sophisticated security mechanisms, NX9 reduces complexity through architectural separation.

The result is software that is easier to understand, easier to operate, easier to secure, and remains faithful to the guiding philosophy of the NX9 ecosystem:

> **Expose only what must be public. Everything else belongs on localhost.**
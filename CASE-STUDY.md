# NX9 Philosophy: Engineering Beyond Frameworks

## A Real-World Case Study in Software Minimalism, Explicit Routing, and Reduced Attack Surface

> *"The best way to reduce complexity is not to manage more software—it is to deploy less software."*

---

## Executive Summary

This case study examines the first publicly accessible deployment of **NX9** and the unsolicited Internet traffic it received immediately after exposure.

The objective was not to conduct a penetration test or security benchmark. Instead, the production access logs were analyzed to understand how real-world Internet scanners interacted with a deliberately minimal software stack.

The results were revealing.

During the observed period:

* **362 HTTP requests** were received.
* **331 requests (91.4%)** resulted in **`404 Not Found`**.
* **20 requests (5.5%)** returned **`304 Not Modified`**, indicating normal browser caching.
* **11 requests (3.1%)** returned **`200 OK`**, serving legitimate published resources.

The overwhelming majority of incoming requests were **not attempts to use the application**.

They were attempts to identify technologies that were never deployed.

---

# Introduction

Modern software engineering frequently begins with a familiar question:

> **"Which framework should we use?"**

NX9 begins with a different question:

> **"Do we need one at all?"**

This distinction is fundamental.

NX9 is not opposed to frameworks.

Frameworks such as React, Angular, Laravel, Spring Boot, Django, and Next.js have solved genuine engineering problems at enormous scale.

React solved Facebook's UI challenges.

Angular addressed Google's enterprise applications.

Laravel transformed PHP productivity.

Those are significant engineering achievements.

The question NX9 asks is simply:

> **Does our project have those same problems?**

Many self-hosted services do not.

A documentation website.

A URL shortener.

An authentication server.

A digital timestamping service.

A lightweight dashboard.

These applications often require reliability, simplicity, maintainability, and operational transparency far more than they require extensive framework ecosystems.

NX9 therefore adopts a different philosophy.

---

# The NX9 Philosophy

Every NX9 project follows a common set of engineering principles.

* Privacy First
* Self-Hosted First
* Linux Native
* Rust Native
* Single Binary Applications
* Explicit Routing
* Minimal Dependencies
* Open Source (FOSS)
* No Vendor Lock-In
* Operational Simplicity

Rather than beginning with a framework and removing features, NX9 begins with the application itself and adds only the software required to solve the problem.

Nothing more.

Nothing less.

---

# Complexity Is Not Free

Every dependency introduces responsibility.

Someone must eventually:

* install it;
* configure it;
* update it;
* monitor it;
* patch it;
* audit it;
* understand it.

Modern web applications frequently include:

* thousands of npm packages;
* hundreds of indirect dependencies;
* build systems;
* transpilers;
* runtime environments;
* middleware layers;
* plugins;
* framework conventions.

Each component may be valuable.

Collectively, they also increase operational complexity and expand the software that must be maintained throughout the application's lifetime.

NX9 therefore asks a much simpler engineering question:

> **Can this problem be solved with significantly less software?**

If the answer is yes, simplicity becomes the preferred engineering decision.

---

# Production Snapshot

This study is based entirely on production access logs collected after **nx9.in** became publicly accessible.

This was **not**:

* a penetration test;
* a laboratory simulation;
* synthetic benchmark traffic.

It was ordinary Internet traffic.

Within a short period of public exposure:

* automated vulnerability scanners began probing the server;
* legitimate browsers accessed the published website;
* Twitter/X generated preview cards;
* search crawlers indexed the content;
* additional independent scanners continued probing throughout the observation period.

---

# Observed Traffic

During the observation period:

| Response         |   Count | Percentage |
| ---------------- | ------: | ---------: |
| 404 Not Found    | **331** |  **91.4%** |
| 304 Not Modified |      20 |       5.5% |
| 200 OK           |      11 |       3.1% |

The most striking observation is that **over 91% of incoming requests were not attempts to use the application.**

They were attempts to discover software that was never deployed.

---

# What Were the Bots Looking For?

Representative examples include:

```text
/.env
/vendor/.env
/wp-admin/
/wp-content/
/wp-includes/
/phpinfo.php
/admin.php
/public/css.php
/f35.php
/222.php
/chosen.php
/vercel.json
/vite.config.ts
/vendors~main.bundle.js
/vue/
/v1/admin/
```

These requests reveal remarkably consistent assumptions.

| Requested Resource       | What the Scanner Expected   |
| ------------------------ | --------------------------- |
| `.env`                   | Laravel / PHP configuration |
| `vendor/.env`            | Composer project            |
| `wp-admin`               | WordPress                   |
| `wp-content`             | WordPress plugins           |
| `phpinfo.php`            | PHP runtime                 |
| `admin.php`              | PHP administration panel    |
| `f35.php`                | PHP web shell               |
| `public/css.php`         | Vulnerable PHP application  |
| `vite.config.ts`         | Vite project                |
| `vendors~main.bundle.js` | Webpack / React build       |
| `vercel.json`            | Vercel deployment           |
| `vue/.env`               | Vue application             |

The scanners were not attempting to identify NX9.

They were attempting to identify technologies commonly deployed across today's Internet.

---

# What Actually Happened?

Every vulnerability probe received essentially the same response.

```text
404 Not Found
```

Not because NX9 blocked the request.

Not because a Web Application Firewall intercepted it.

Not because an intrusion detection system analyzed it.

The requested resources simply did not exist.

This distinction is critical.

There is a significant engineering difference between software successfully defending itself and software that was never deployed in the first place.

---

# Explicit Routing

NX9 applications expose only routes intentionally defined by the developer.

Conceptually:

```text
/
├── /
├── /projects
├── /about
├── /contact
└── 404
```

There is:

* no automatic controller discovery;
* no runtime file resolution;
* no directory-based routing;
* no framework-generated endpoints.

If a route was never implemented, it simply cannot be reached.

Unknown requests terminate immediately at the fallback handler.

---

# Security Begins Before Deployment

Security is often discussed in terms of:

* firewalls;
* intrusion detection systems;
* endpoint protection;
* monitoring platforms.

Those remain valuable.

However, architecture itself is also a security decision.

The NX9 deployment contained:

* no PHP interpreter;
* no WordPress;
* no Laravel;
* no Composer vendor directory;
* no Node.js runtime;
* no exposed `.env`;
* no framework-generated administration interface;
* no debug endpoints.

Those components were never installed.

Consequently, they never became part of the deployment's attack surface.

This is not **security through obscurity**.

It is **security through intentional software selection**.

---

# A Smaller Stack

Many modern web deployments resemble:

```text
Internet
      │
      ▼
Reverse Proxy
      │
      ▼
Runtime
      │
      ▼
Framework
      │
      ▼
Middleware
      │
      ▼
Plugins
      │
      ▼
Packages
      │
      ▼
Application
```

NX9 deliberately reduces the deployment:

```text
Internet
      │
      ▼
Nginx
      │
      ▼
Rust Binary
      │
      ▼
Explicit Route Table
      │
      ▼
Application Logic
```

The objective is not minimalism for its own sake.

The objective is engineering proportional to the problem being solved.

---

# Frameworks Are Not the Enemy

This case study should not be interpreted as criticism of frameworks.

Frameworks solve difficult engineering problems.

Many projects genuinely require them.

NX9 simply argues that every dependency should justify its existence.

Engineering is not about choosing the most fashionable technology.

It is about choosing the most appropriate technology.

Sometimes that means a sophisticated framework.

Sometimes that means a single Rust binary.

---

# Legitimate Traffic Continued Normally

An equally important observation is what **did** work.

Legitimate clients successfully accessed the application throughout the observation period.

This included:

* desktop browsers;
* Android browsers;
* Twitter/X preview generation;
* search engine crawlers;
* browser cache validation (`304 Not Modified`).

The minimal deployment remained fully functional for intended users while exposing no unnecessary application surface.

---

# Non-Goals

This article does **not** claim:

* that Rust is immune to vulnerabilities;
* that frameworks are insecure;
* that 404 responses alone provide security;
* that NX9 cannot contain bugs.

Instead, it demonstrates a much simpler engineering principle:

> **Software that is never deployed cannot become part of your deployment's attack surface.**

---

# Lessons Learned

The production logs reveal a surprisingly simple truth.

The overwhelming majority of unsolicited Internet traffic was not exploring the application itself.

It was exploring assumptions.

The scanners assumed:

* PHP;
* WordPress;
* Laravel;
* Vue;
* Node.js;
* Composer;
* Vite;
* Vercel;
* common administration panels.

NX9 deliberately deployed none of them.

The result was not that sophisticated defensive software defeated the attacks.

The result was that the attacks found nothing matching their expectations.

---

# Conclusion

Every NX9 project begins with the same engineering question:

> **What is the smallest amount of software required to solve this problem well?**

Sometimes that answer includes a framework.

Often it does not.

This case study demonstrates that software minimalism is not merely an aesthetic preference.

It is an architectural decision with practical operational consequences.

During the observed period, more than **91%** of incoming requests were attempts to identify technologies that simply were not present.

That outcome was not accidental.

It was the direct consequence of choosing a smaller, simpler, explicitly designed software stack.

**Build only what you need.**

**Deploy only what you trust.**

**Maintain only what you own.**

Because every component you choose **not** to deploy is one less component to configure, patch, monitor, audit—and one less component available to be targeted.

**That is the NX9 philosophy.**

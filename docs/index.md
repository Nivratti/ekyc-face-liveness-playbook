# Face Liveness Docs

## Simple main guide + deep reference for eKYC teams

This documentation is designed to be easy for first-time readers **and** still useful for deeper technical work.

Instead of forcing everyone through a long encyclopedia-style path, the site has two layers:

- **Main guide** — simple, practical, and fast to understand
- **Appendix / deep reference** — detailed technical, testing, standards, security, and vendor material

---

## Start here

### New to face liveness?
Read these first:

1. [00. Overview](00-overview.md)
2. [01. Face Liveness Guide](01-face-liveness-guide.md)

### Working on eKYC flow design?
Then read:

3. [02. eKYC Integration](02-ekyc-integration.md)

### Building or deploying the system?
Then read:

4. [03. Deployment Guide](03-deployment-guide.md)
5. [04. Best Practices](04-best-practices.md)

### Need deeper detail?
Go to:

- [Appendix](appendix/A1-key-terms.md)
- the detailed topic chapters under **Deep Reference by Topic** in the left navigation

---

## Quick map

```mermaid
flowchart LR
    A[00 Overview] --> B[01 Face Liveness Guide]
    B --> C[02 eKYC Integration]
    C --> D[03 Deployment Guide]
    D --> E[04 Best Practices]
    B --> F[Appendix]
    C --> F
    D --> F
    E --> F
```

---

## What this documentation covers

- what face liveness is
- why it matters in eKYC
- how passive, active, and hybrid methods differ
- common attack types from print and replay to injection and AI-generated content
- input quality, score interpretation, and thresholding
- deployment choices such as on-device, server-side, and hybrid
- testing, monitoring, and model updates
- security, privacy, and vendor evaluation

---

## How to use this site

!!! tip "Fastest practical path"
    If you want a simple but complete understanding, read the five main pages first. That gives you the end-to-end picture without getting overloaded by standards and taxonomy detail.

!!! tip "Use appendix only when needed"
    The appendix exists so the main guide stays clean. Use it when you need attack depth, metrics detail, standards mapping, or procurement checklists.

!!! note "Detailed topic pages are preserved"
    The earlier deep-dive chapters are still available. They now serve as reference material rather than the first reading path.

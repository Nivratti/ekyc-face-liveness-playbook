# 00. Overview

## Who should read this page

This page is for anyone who wants the **fastest orientation** before going deeper.

---

## What this documentation is

This repository explains **face liveness for eKYC** in simple language while still covering the points that matter in real systems.

Face liveness answers one core question:

> Is the camera seeing a real person who is physically present right now, or is it seeing some kind of spoof?

A spoof could be:

- a printed photo
- a replayed video on another screen
- a mask
- an injected image or video stream
- AI-generated or manipulated face content

---

## Why this repo was reorganized

A lot of face liveness material becomes hard to read because it mixes everything together too early:

- definitions
- attack taxonomy
- metrics
- deployment engineering
- standards and compliance
- vendor evaluation

That makes the first reading heavy.

This repo now uses a simpler structure:

### Main guide
Use this first. It explains the core ideas in plain English.

### Appendix and deep reference
Use this when you need technical detail, standards context, long checklists, or deeper testing material.

---

## The big idea to remember

A **face match** system and a **face liveness** system solve different problems.

| Check | Main question |
|------|---------------|
| Face match | Does this face look like the enrolled face or the ID portrait? |
| Face liveness | Is this a real live person present during capture? |

A system can be good at face matching and still accept a spoof.

That is why remote eKYC usually needs both.

---

## Reading path by role

| Role | Start with | Then go to |
|------|------------|------------|
| Product or business | [01-face-liveness-guide.md](01-face-liveness-guide.md) | [02-ekyc-integration.md](02-ekyc-integration.md), [04-best-practices.md](04-best-practices.md) |
| ML engineer | [01-face-liveness-guide.md](01-face-liveness-guide.md) | [03-deployment-guide.md](03-deployment-guide.md), [appendix/A3-metrics-and-evaluation.md](appendix/A3-metrics-and-evaluation.md) |
| Backend or platform engineer | [02-ekyc-integration.md](02-ekyc-integration.md) | [03-deployment-guide.md](03-deployment-guide.md), [appendix/A5-security-and-privacy.md](appendix/A5-security-and-privacy.md) |
| Risk or fraud team | [01-face-liveness-guide.md](01-face-liveness-guide.md) | [appendix/A2-attack-taxonomy.md](appendix/A2-attack-taxonomy.md), [appendix/A5-security-and-privacy.md](appendix/A5-security-and-privacy.md) |
| Compliance or procurement | [01-face-liveness-guide.md](01-face-liveness-guide.md) | [appendix/A4-standards-and-compliance.md](appendix/A4-standards-and-compliance.md), [appendix/A6-vendor-evaluation-checklist.md](appendix/A6-vendor-evaluation-checklist.md) |

---

## The five main pages

| Page | Why it exists |
|------|---------------|
| [01. Face Liveness Guide](01-face-liveness-guide.md) | Explains the core concepts in simple English |
| [02. eKYC Integration](02-ekyc-integration.md) | Shows where liveness fits in the full onboarding flow |
| [03. Deployment Guide](03-deployment-guide.md) | Covers real engineering and runtime choices |
| [04. Best Practices](04-best-practices.md) | Gives a practical do-and-don't checklist |
| [05. Real-World Examples](05-real-world-examples.md) | Shows where liveness is used in actual journeys |
| [06. API and Response Examples](06-api-and-response-examples.md) | Gives practical response patterns and integration ideas |
| [07. Decision Logic](07-decision-logic.md) | Shows how to turn score into action |
| [08. Evaluation Playbook](08-evaluation-playbook.md) | Explains how to test readiness on real attacks and devices |
| [09. Common Failures](09-common-failures.md) | Explains where production issues usually come from |
| [10. Product Guide](10-product-guide.md) | Translates liveness into product trade-offs |
| [11. Advanced Topics](11-advanced-topics.md) | Introduces fusion, calibration, and maturity topics |
| [12. Fusion and Meta-Model](12-fusion-and-meta-model.md) | Explains how to combine multiple signals into one decision layer |
| [13. Dataset Strategy](13-dataset-strategy.md) | Defines the data needed for base models, fusion, and reliable testing |
| [14. Score Calibration and Thresholding](14-score-calibration-and-thresholding.md) | Shows how scores become stable policy decisions |
| [15. Error Analysis](15-error-analysis.md) | Turns failures into root causes and next actions |
| [16. Monitoring and Operations](16-monitoring-and-operations.md) | Covers dashboards, alerts, and post-launch control |
| [17. Security Hardening](17-security-hardening.md) | Adds the non-model controls that protect the full system |
| [18. Device and Platform Matrix](18-device-and-platform-matrix.md) | Maps app, web, browser, and device-class differences |
| [19. Model Governance](19-model-governance.md) | Explains release discipline, rollback, and auditability |
| [20. FAQ](20-faq.md) | Gives fast answers to common questions |
| [21. Troubleshooting](21-troubleshooting.md) | Helps teams debug issues quickly in production |
| [22. Case Studies](22-case-studies.md) | Shows how policy changes by journey type |
| [23. System Architecture](23-system-architecture.md) | Ties capture, inference, policy, and monitoring into one system view |
| [Appendix](appendix/A1-key-terms.md) | Holds deep technical, metrics, security, and vendor material |

---

## Visual reading map

```mermaid
flowchart TD
    A[Start] --> B[00 Overview]
    B --> C[01 Face Liveness Guide]
    C --> D[02 eKYC Integration]
    D --> E[03 Deployment Guide]
    E --> F[04 Best Practices]
    F --> H[05 to 11 Practical Playbook]
    H --> I[12 to 19 Engineering and Operations]
    I --> J[20 to 23 FAQ, Troubleshooting, Cases, Architecture]
    C --> G[Appendix A1-A10]
    D --> G
    E --> G
    F --> G
    H --> G
    I --> G
    J --> G
```

---

## A simple mental model

Think about face liveness as one layer in a larger trust pipeline:

```mermaid
flowchart LR
    A[Capture] --> B[Quality checks]
    B --> C[Liveness]
    C --> D[Face match]
    D --> E[Risk policy]
    E --> F[Decision]
```

Face liveness is important, but it is not the whole system.

---

## Related docs

- [01. Face Liveness Guide](01-face-liveness-guide.md)
- [02. eKYC Integration](02-ekyc-integration.md)
- [05. Real-World Examples](05-real-world-examples.md)
- [12. Fusion and Meta-Model](12-fusion-and-meta-model.md)
- [Appendix A1 — Key Terms](appendix/A1-key-terms.md)

## Read next

Go to [01. Face Liveness Guide](01-face-liveness-guide.md).

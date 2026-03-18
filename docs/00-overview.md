# 00. Overview

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

## Who should read what

| Role | Start with | Then go to |
|------|------------|------------|
| Product or business | [01-face-liveness-guide.md](01-face-liveness-guide.md) | [02-ekyc-integration.md](02-ekyc-integration.md), [04-best-practices.md](04-best-practices.md) |
| ML engineer | [01-face-liveness-guide.md](01-face-liveness-guide.md) | [03-deployment-guide.md](03-deployment-guide.md), [appendix/A3-metrics-and-evaluation.md](appendix/A3-metrics-and-evaluation.md) |
| Backend or platform engineer | [02-ekyc-integration.md](02-ekyc-integration.md) | [03-deployment-guide.md](03-deployment-guide.md), [appendix/A5-security-and-privacy.md](appendix/A5-security-and-privacy.md) |
| Risk or fraud team | [01-face-liveness-guide.md](01-face-liveness-guide.md) | [appendix/A2-attack-taxonomy.md](appendix/A2-attack-taxonomy.md), [appendix/A5-security-and-privacy.md](appendix/A5-security-and-privacy.md) |
| Compliance or procurement | [01-face-liveness-guide.md](01-face-liveness-guide.md) | [appendix/A4-standards-and-compliance.md](appendix/A4-standards-and-compliance.md), [appendix/A6-vendor-evaluation-checklist.md](appendix/A6-vendor-evaluation-checklist.md) |

---

## The five main pages

### 1. Face Liveness Guide
A simple explanation of what face liveness is, why it matters, how it works, and where teams usually make mistakes.

### 2. eKYC Integration
Shows where liveness fits in the full onboarding and verification flow.

### 3. Deployment Guide
Covers real engineering choices such as mobile vs web, on-device vs server-side, rollout, monitoring, and runtime constraints.

### 4. Best Practices
A practical do-and-don't page you can use as a project checklist.

### 5. Appendix
Deep material for taxonomy, metrics, standards, privacy, security, and vendor evaluation.

---

## Simple reading path

1. Start with [01. Face Liveness Guide](01-face-liveness-guide.md)
2. Then see where it fits in [02. eKYC Integration](02-ekyc-integration.md)
3. Then review [03. Deployment Guide](03-deployment-guide.md)
4. Then use [04. Best Practices](04-best-practices.md)
5. Open appendix pages only when you need more detail

---

## What is intentionally kept out of the beginner path

To keep the main guide easy to follow, these heavy topics are moved out of the first reading path:

- full attack taxonomy
- long metric discussions
- standards detail and certification context
- large vendor checklists
- detailed regulatory notes
- extended reference lists

That material is still important. It is just not shown first.

---

## Practical takeaway

If you read only the five main pages, you should still come away with a solid understanding of:

- what face liveness does
- why it matters in eKYC
- where it sits in the pipeline
- how it should be deployed
- what teams should test and monitor

The appendix is there when you need to go deeper, not to slow down the first pass.

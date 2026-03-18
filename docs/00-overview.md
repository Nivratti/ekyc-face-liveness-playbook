# 00. Overview

## What this documentation is

This repository explains **face liveness for eKYC** in a way that is easier to understand than a traditional technical manual, while still covering all major topics needed for product, engineering, security, and compliance work.

Face liveness answers a simple question:

> Is the camera seeing a real person who is physically present right now, or is it seeing a spoof such as a printed photo, replayed video, mask, injected stream, or AI-generated face content?

---

## Why this documentation was reorganized

Many face liveness documents are complete but hard to read. They often mix together:

- beginner concepts
- attack taxonomy
- standards
- deployment details
- procurement material
- regulatory notes

That makes the first reading path heavy.

This repo now separates the content into two levels:

### Main guide
Use this for the first pass. It explains the core ideas in simple English.

### Appendix and deep reference
Use this when you need technical detail, standards context, or long checklists.

---

## Who should read what

| Role | Start with | Then go to |
|------|------------|------------|
| Product / business | `01-face-liveness-guide.md` | `02-ekyc-integration.md`, `04-best-practices.md` |
| ML engineer | `01-face-liveness-guide.md` | `03-deployment-guide.md`, `appendix/A3-metrics-and-evaluation.md` |
| Backend / platform engineer | `02-ekyc-integration.md` | `03-deployment-guide.md`, `appendix/A5-security-and-privacy.md` |
| Fraud / risk team | `01-face-liveness-guide.md` | `appendix/A2-attack-taxonomy.md`, `appendix/A5-security-and-privacy.md` |
| Compliance / procurement | `01-face-liveness-guide.md` | `appendix/A4-standards-and-compliance.md`, `appendix/A6-vendor-evaluation-checklist.md` |

---

## The five main pages

### 1. Face Liveness Guide
The simplest complete introduction. Read this first.

### 2. eKYC Integration
Shows where liveness fits in the onboarding and verification pipeline.

### 3. Deployment Guide
Focuses on engineering choices, runtime constraints, and rollout concerns.

### 4. Best Practices
A practical do-and-don't guide.

### 5. Appendix
Detailed reference material for deeper work.

---

## Core idea to remember

A face match model and a face liveness model solve **different problems**:

- **Face match** asks: *Does this face match the enrolled person or ID document?*
- **Face liveness** asks: *Is this a real, live, physically present person?*

In remote eKYC, both checks are usually needed.

---

## Simple reading path

1. Understand the problem — [01. Face Liveness Guide](01-face-liveness-guide.md)
2. Place it in the business flow — [02. eKYC Integration](02-ekyc-integration.md)
3. Understand deployment choices — [03. Deployment Guide](03-deployment-guide.md)
4. Review practical guidance — [04. Best Practices](04-best-practices.md)
5. Use appendix when deeper detail is needed

---

## What is intentionally kept out of the beginner path

To keep the main guide clear, these heavy topics are moved to appendix or detailed reference pages:

- full attack taxonomy
- standards detail and certification context
- long metrics discussions
- vendor procurement checklists
- extensive compliance notes
- large link collections and research references

That material is still important. It is just not shown first.

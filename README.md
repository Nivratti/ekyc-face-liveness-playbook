# Face Liveness Docs

Simple, practical documentation for **face liveness in eKYC**.

This repository is designed for mixed audiences. A product manager should be able to understand the first few pages quickly, while an ML engineer or security reviewer should still be able to drill down into the technical details.

## Why this repo is structured this way

Many face liveness write-ups become hard to read because they put everything into one long flow:

- basic concepts
- attack taxonomy
- deployment detail
- metrics and standards
- privacy and compliance
- vendor evaluation

All of that matters, but not all of it should appear on page one.

This repo therefore has **two layers**:

1. **Main guide** — plain English, practical, and suitable for a first full read
2. **Appendix / deep reference** — detailed technical, testing, security, standards, and evaluation material

That keeps the learning path simple without losing important depth.

## Who this repo is for

- Product teams designing onboarding and verification flows
- ML engineers building or evaluating liveness models
- Backend and platform engineers integrating SDKs or APIs
- Solution architects planning deployment and rollout
- Risk, fraud, security, and compliance teams reviewing controls
- Procurement teams comparing vendors or SDK options

## Reading path

### If you are new to face liveness
Start here:

1. [docs/00-overview.md](docs/00-overview.md)
2. [docs/01-face-liveness-guide.md](docs/01-face-liveness-guide.md)

### If you design eKYC flows
Then read:

3. [docs/02-ekyc-integration.md](docs/02-ekyc-integration.md)

### If you build or deploy systems
Then read:

4. [docs/03-deployment-guide.md](docs/03-deployment-guide.md)
5. [docs/04-best-practices.md](docs/04-best-practices.md)

### If you need deeper detail
Use:

- [docs/appendix/A1-key-terms.md](docs/appendix/A1-key-terms.md) as the appendix starting page
- the topic pages under `docs/01-*` to `docs/10-*`

## Repository structure

```text
face-liveness-docs/
├─ README.md
├─ docs/
│  ├─ 00-overview.md
│  ├─ 01-face-liveness-guide.md
│  ├─ 02-ekyc-integration.md
│  ├─ 03-deployment-guide.md
│  ├─ 04-best-practices.md
│  ├─ appendix/
│  ├─ images/
│  └─ ... detailed topic folders ...
├─ diagrams/
│  ├─ source/
│  └─ exported/
├─ templates/
├─ references/
└─ changelog.md
```

## Main document map

| File | Purpose |
|------|---------|
| [docs/00-overview.md](docs/00-overview.md) | Quick orientation, audience map, and reading order |
| [docs/01-face-liveness-guide.md](docs/01-face-liveness-guide.md) | Main simple guide to core concepts |
| [docs/02-ekyc-integration.md](docs/02-ekyc-integration.md) | Shows where liveness sits inside the full eKYC flow |
| [docs/03-deployment-guide.md](docs/03-deployment-guide.md) | Engineering and runtime deployment choices |
| [docs/04-best-practices.md](docs/04-best-practices.md) | Practical checklist of what to do and what to avoid |

## Appendix map

| File | Purpose |
|------|---------|
| [docs/appendix/A1-key-terms.md](docs/appendix/A1-key-terms.md) | Short glossary in plain English |
| [docs/appendix/A2-attack-taxonomy.md](docs/appendix/A2-attack-taxonomy.md) | Expanded attack grouping and examples |
| [docs/appendix/A3-metrics-and-evaluation.md](docs/appendix/A3-metrics-and-evaluation.md) | Metrics, thresholds, and evaluation design |
| [docs/appendix/A4-standards-and-compliance.md](docs/appendix/A4-standards-and-compliance.md) | Standards and compliance orientation |
| [docs/appendix/A5-security-and-privacy.md](docs/appendix/A5-security-and-privacy.md) | Security controls and privacy concerns |
| [docs/appendix/A6-vendor-evaluation-checklist.md](docs/appendix/A6-vendor-evaluation-checklist.md) | Procurement and vendor assessment checklist |
| [docs/appendix/A7-references.md](docs/appendix/A7-references.md) | Reference map to deeper pages and reading material |

## What changed from the earlier structure

The repo originally read more like an encyclopedia. It now has a clearer reading path:

- learn the basics first
- understand where liveness fits in eKYC
- move into deployment and operations
- use appendix only when deeper detail is needed

The earlier detailed pages are still preserved, but they are no longer the first path a new reader must follow.

## Local development

```bash
pip install -r requirements.txt
mkdocs serve
```

Then open `http://127.0.0.1:8000`.

## Recommended next improvements

If you want to keep improving this repo over time, the best next additions are:

1. simple architecture diagrams
2. example decision trees for retry and escalation
3. deployment playbooks for mobile, web, and hybrid setups
4. sample vendor evaluation scorecards
5. sample test plans and go-live checklists

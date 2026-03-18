# Face Liveness Docs

Simple, practical documentation for **face liveness in eKYC**.

This repository is designed for mixed audiences. A product manager should be able to understand the first few pages quickly, while an ML engineer or security reviewer should still be able to drill down into deeper technical detail when needed.

## What changed in this version

This repo now has a clearer in-content navigation layer:

- stronger beginner reading path
- clickable related-doc links inside the pages
- **Read next** sections at the bottom of the main pages
- appendix pages that link back to the main guide
- simple diagrams and comparison tables in the core docs

## Two reading layers

### Main guide
Use this first. It is written in simpler English and explains the end-to-end picture without too much standards or taxonomy detail.

### Appendix and deep reference
Use this when you need metrics detail, standards context, security controls, vendor checklists, or topic-by-topic deep dives.

## Fastest reading paths

| Role | Start here | Then read |
|------|------------|-----------|
| New reader | [docs/00-overview.md](docs/00-overview.md) | [docs/01-face-liveness-guide.md](docs/01-face-liveness-guide.md) |
| Product / business | [docs/01-face-liveness-guide.md](docs/01-face-liveness-guide.md) | [docs/02-ekyc-integration.md](docs/02-ekyc-integration.md), [docs/04-best-practices.md](docs/04-best-practices.md) |
| ML / evaluation | [docs/01-face-liveness-guide.md](docs/01-face-liveness-guide.md) | [docs/03-deployment-guide.md](docs/03-deployment-guide.md), [docs/appendix/A3-metrics-and-evaluation.md](docs/appendix/A3-metrics-and-evaluation.md) |
| Platform / backend | [docs/02-ekyc-integration.md](docs/02-ekyc-integration.md) | [docs/03-deployment-guide.md](docs/03-deployment-guide.md), [docs/appendix/A5-security-and-privacy.md](docs/appendix/A5-security-and-privacy.md) |
| Procurement / compliance | [docs/01-face-liveness-guide.md](docs/01-face-liveness-guide.md) | [docs/appendix/A4-standards-and-compliance.md](docs/appendix/A4-standards-and-compliance.md), [docs/appendix/A6-vendor-evaluation-checklist.md](docs/appendix/A6-vendor-evaluation-checklist.md) |

## Main reading path

1. [docs/00-overview.md](docs/00-overview.md)
2. [docs/01-face-liveness-guide.md](docs/01-face-liveness-guide.md)
3. [docs/02-ekyc-integration.md](docs/02-ekyc-integration.md)
4. [docs/03-deployment-guide.md](docs/03-deployment-guide.md)
5. [docs/04-best-practices.md](docs/04-best-practices.md)

## Appendix map

- [docs/appendix/A1-key-terms.md](docs/appendix/A1-key-terms.md)
- [docs/appendix/A2-attack-taxonomy.md](docs/appendix/A2-attack-taxonomy.md)
- [docs/appendix/A3-metrics-and-evaluation.md](docs/appendix/A3-metrics-and-evaluation.md)
- [docs/appendix/A4-standards-and-compliance.md](docs/appendix/A4-standards-and-compliance.md)
- [docs/appendix/A5-security-and-privacy.md](docs/appendix/A5-security-and-privacy.md)
- [docs/appendix/A6-vendor-evaluation-checklist.md](docs/appendix/A6-vendor-evaluation-checklist.md)
- [docs/appendix/A7-references.md](docs/appendix/A7-references.md)

## Site navigation tips

When you run the MkDocs site:

- use the **Start Here** section first
- use the left sidebar for topic browsing
- use the **previous / next** page navigation at the bottom of pages
- use the **Related docs** and **Read next** sections inside the pages

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
├─ javascripts/
├─ templates/
├─ references/
└─ changelog.md
```

## Local development

```bash
pip install -r requirements.txt
mkdocs serve
```

Then open `http://127.0.0.1:8000`.

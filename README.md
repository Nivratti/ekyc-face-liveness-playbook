# Face Liveness Docs

Simple, complete documentation for **face liveness in eKYC**.

This repository is organized in two layers:

1. **Main guide** — easy to read, practical, and suitable for first-time readers.
2. **Appendix / deep reference** — detailed technical, security, testing, standards, and vendor material.

The goal is to keep the learning path simple **without losing important depth**.

---

## Who This Repo Is For

- Product managers designing onboarding and verification flows
- ML engineers building or evaluating liveness models
- Backend / platform engineers integrating SDKs and APIs
- Solution architects planning deployment patterns
- Risk, fraud, and compliance stakeholders reviewing controls

---

## Reading Path

### If you are new to face liveness
Start here:
1. `docs/00-overview.md`
2. `docs/01-face-liveness-guide.md`

### If you design eKYC flows
Then read:
3. `docs/02-ekyc-integration.md`

### If you build or deploy systems
Then read:
4. `docs/03-deployment-guide.md`
5. `docs/04-best-practices.md`

### If you need detailed reference material
Use:
- `docs/appendix/`
- the legacy deep-dive topic pages already in `docs/01-*` to `docs/10-*`

---

## Repository Structure

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
│  │  ├─ A1-key-terms.md
│  │  ├─ A2-attack-taxonomy.md
│  │  ├─ A3-metrics-and-evaluation.md
│  │  ├─ A4-standards-and-compliance.md
│  │  ├─ A5-security-and-privacy.md
│  │  ├─ A6-vendor-evaluation-checklist.md
│  │  └─ A7-references.md
│  ├─ images/
│  └─ ... existing detailed topic folders ...
├─ diagrams/
│  ├─ source/
│  └─ exported/
├─ templates/
├─ references/
└─ changelog.md
```

---

## Main Document Map

| File | Purpose |
|------|---------|
| `docs/00-overview.md` | Quick orientation and reading path |
| `docs/01-face-liveness-guide.md` | Main simple guide |
| `docs/02-ekyc-integration.md` | How liveness fits into the full eKYC workflow |
| `docs/03-deployment-guide.md` | Engineering and deployment decisions |
| `docs/04-best-practices.md` | Practical implementation guidance and common mistakes |

---

## Appendix Map

| File | Purpose |
|------|---------|
| `A1-key-terms.md` | Short glossary in plain English |
| `A2-attack-taxonomy.md` | Full attack grouping and examples |
| `A3-metrics-and-evaluation.md` | Metrics, thresholding, test design |
| `A4-standards-and-compliance.md` | Standards and compliance orientation |
| `A5-security-and-privacy.md` | Security controls and privacy considerations |
| `A6-vendor-evaluation-checklist.md` | Procurement and vendor assessment checklist |
| `A7-references.md` | Reference map to detailed pages and external reading placeholders |

---

## How This Repo Is Different Now

The repo previously read mainly like a deep encyclopedia. It now has a clearer structure:

- **Start simple first**
- **Keep deep material separate**
- **Make deployment guidance easier to find**
- **Keep standards and taxonomy out of the beginner path**

---

## Local Development

```bash
pip install -r requirements.txt
mkdocs serve
```

Then open `http://127.0.0.1:8000`.

---

## Notes

- The new top-level pages are written in simpler English.
- The existing detailed topic pages are still preserved for depth.
- You can gradually expand diagrams, examples, and internal standards mapping without changing the basic reading path.

# Appendix A9 — Data Collection and Labeling

## Purpose

This appendix describes practical guidance for collecting, labeling, and packaging liveness data so that training and evaluation stay useful and reproducible.

---

## Data collection principles

A strong collection plan should define:

- target use case
- attack families to cover
- channels and platforms to cover
- privacy and consent rules
- storage and retention rules
- split and version strategy

---

## Useful label fields

At minimum, try to store:

- `sample_id`
- `person_id`
- `session_id`
- `label`
- `attack_family`
- `attack_type`
- `platform`
- `device_class`
- `capture_type`
- `lighting_bucket`
- `quality_bucket`
- `review_status`

---

## Labeling rules should be written down

A practical labeling guide should answer:

- what counts as bona fide
- what counts as spoof
- how to label uncertain or ambiguous samples
- how to label multi-problem cases such as spoof plus poor quality
- how to escalate disagreements between reviewers

---

## Suggested review states

| State | Meaning |
|-------|---------|
| confirmed | label agreed and accepted |
| uncertain | label not reliable enough yet |
| disputed | reviewer disagreement exists |
| excluded | should not be used for training or main evaluation |

---

## Reviewer agreement matters

Useful practices:

- sample a subset for double review
- track disagreement rate
- define escalation path for hard cases
- store review notes for repeated edge cases

This reduces silent label noise.

---

## Naming and packaging hygiene

Use consistent identifiers and keep metadata outside filenames when possible.

A simple pattern is:

```text
sample_id, person_id, session_id, label, attack_type, platform, split
```

This makes joins and audits easier.

---

## Privacy and consent reminders

Data collection should respect the program's privacy and legal obligations.

Typical considerations include:

- user consent where required
- storage minimization
- retention policy
- restricted access to raw media
- audit trail for access

---

## Common mistakes

| Mistake | Why it hurts |
|---------|--------------|
| only binary labels | blocks deeper error analysis |
| no uncertain bucket | noisy labels pollute training |
| no reviewer audit trail | hard to improve label quality |
| no device metadata | segmentation becomes weak |
| changing label schema without versioning | experiments become hard to compare |

---

## Related docs

- [13. Dataset Strategy](../13-dataset-strategy.md)
- [15. Error Analysis](../15-error-analysis.md)
- [Appendix A10 — Experiment Design](A10-experiment-design.md)

# Appendix A10 — Experiment Design

## Purpose

This appendix gives a practical structure for designing experiments so that model, fusion, and policy changes can be compared fairly.

---

## What a good experiment should answer

A useful experiment should say:

- what changed
- what hypothesis is being tested
- what data split is used
- what metrics will decide success
- what segments must not regress

---

## Common experiment types

| Experiment type | Example question |
|-----------------|------------------|
| base-model comparison | is model B better than model A on replay attacks? |
| fusion experiment | does calibrated fusion reduce false accepts without hurting retries? |
| threshold search | which score bands fit onboarding best? |
| channel-specific policy | should web use a stricter threshold than app? |
| data ablation | does low-light data improve false rejects in dim conditions? |

---

## A useful experiment template

1. objective
2. hypothesis
3. data and split version
4. model / policy versions under test
5. evaluation metrics
6. protected segments
7. acceptance criteria
8. failure review plan

---

## Example acceptance criteria

- APCER improves on replay attacks
- BPCER does not regress beyond tolerance
- retry rate does not rise above allowed level
- p95 latency stays within budget
- no protected segment has major degradation

---

## Common mistakes

| Mistake | Why it hurts |
|---------|--------------|
| changing model and threshold together without control | hard to know what helped |
| testing on the same data used for tuning | results become optimistic |
| no segment analysis | hidden regressions survive |
| no experiment record | hard to reproduce findings |

---

## Related docs

- [08. Evaluation Playbook](../08-evaluation-playbook.md)
- [12. Fusion and Meta-Model](../12-fusion-and-meta-model.md)
- [19. Model Governance](../19-model-governance.md)

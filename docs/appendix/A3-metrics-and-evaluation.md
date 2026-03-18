# Appendix A3 — Metrics and Evaluation

## Purpose

This appendix gives a practical overview of how to evaluate face liveness systems.

---

## Important metrics

### APCER
How often attack presentations are incorrectly accepted.

### BPCER
How often genuine users are incorrectly rejected.

### ACER
A simple average of APCER and BPCER. Useful as a summary, but not sufficient by itself.

### Latency
How long the user waits for the result. Real systems should track more than average latency; percentiles matter.

### Retry rate
How often the system asks users to try again.

### Completion rate
How many genuine users successfully finish the process.

---

## Why one number is not enough

A model can look strong on one summary metric and still fail in production because of:

- hard device segments
- weak lighting
- browser-specific issues
- injection attack gaps
- retry policy problems

Evaluation should always include segmented analysis.

---

## Good evaluation design

Test across:
- device classes
- front camera quality levels
- operating systems and browsers
- lighting conditions
- indoor and outdoor scenes
- glasses / occlusion conditions
- different attack instruments
- network variability where relevant

---

## Threshold tuning

Thresholds should be tuned using realistic operational goals, not just lab accuracy.

A good threshold policy usually defines:
- pass zone
- uncertain zone
- fail zone

The uncertain zone supports safer retry or escalation logic.

---

## Production monitoring metrics

After launch, keep tracking:
- pass/retry/fail rate
- score distribution shifts
- latency percentiles
- device-wise behavior
- region-wise anomalies
- manual review escalation rate
- confirmed fraud outcomes where available

---

## Related detailed pages in this repo

- [Performance metrics](../08-quality-testing/performance-metrics.md)
- [Testing methodology](../08-quality-testing/testing-methodology.md)
- [Red team and penetration testing](../08-quality-testing/red-team.md)
- [Edge cases](../08-quality-testing/edge-cases.md)
- [Demographic performance](../08-quality-testing/demographic-performance.md)
- [Datasets](../08-quality-testing/datasets.md)

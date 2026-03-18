# 21. Troubleshooting

## Who should read this page

This page is mainly for support teams, QA teams, backend engineers, SDK engineers, and release owners who need a practical response when something starts going wrong.

---

## Why this page exists

When a liveness issue appears in production, teams usually need quick triage.

The goal of this page is to help answer:

- where the issue is happening
- whether it is model, policy, UX, SDK, or infrastructure related
- what to check first

---

## Fast triage checklist

- [ ] identify affected platform or channel
- [ ] identify affected version: model, policy, SDK, app, or browser
- [ ] check pass / retry / fail shifts
- [ ] check latency and timeout changes
- [ ] inspect top recent failure examples
- [ ] see whether a rollback or hotfix path exists

---

## Symptom: retry rate suddenly jumps

### Likely causes

- threshold became too strict
- capture guidance regressed
- camera behavior changed after app release
- web browser issue or permission behavior changed
- low-light traffic increased

### First checks

- compare by platform and version
- inspect quality metrics
- compare score distributions before and after release

---

## Symptom: spoof acceptance incident

### Likely causes

- new attack pattern not covered
- weakened threshold or policy
- security control bypass
- one channel has weaker enforcement

### First checks

- classify attack family
- inspect intermediate model scores
- check whether client or session security signals fired
- isolate affected channel and version

---

## Symptom: latency is much worse

### Likely causes

- infrastructure regression
- heavy model or fusion change
- client-side capture slowdown
- network path issue

### First checks

- compare p50/p95/p99 latency by channel
- identify whether slowdown is client, API, or model stage
- compare with latest release changes

---

## Symptom: web flow behaves much worse than app flow

### Likely causes

- weak webcam quality
- browser media constraints
- virtual camera or replay exposure
- web-specific policy not tuned

### First checks

- segment by browser family and version
- inspect webcam quality and face-size statistics
- compare threshold and challenge behavior by channel

---

## Symptom: one model says live and another says spoof

### Likely causes

- model disagreement on edge case
- calibration issue
- channel-specific weakness
- bad fusion weight or policy

### First checks

- compare calibrated vs raw scores
- check if disagreement is concentrated on one segment
- review recent fusion or threshold changes

---

## Symptom: many real users fail in dim light

### Likely causes

- weak low-light data coverage
- quality gate too strict
- device class heavily affecting capture

### First checks

- compare by lighting bucket and device class
- inspect false rejects with quality metrics
- test whether retry guidance helps significantly

---

## Symptom: one SDK or app version is much worse

### Likely causes

- camera pipeline change
- image compression change
- integration bug
- metadata missing or malformed

### First checks

- compare release notes
- verify request schema and captured payload
- inspect sample media from affected version

---

## A simple triage matrix

| Signal | Most likely owner |
|--------|-------------------|
| score shift only | ML / calibration / policy |
| latency and timeouts | platform / backend |
| camera or permission failures | SDK / client |
| attack bypass | security + ML |
| one version regressed | release owner + owning team |

---

## When to rollback quickly

Consider fast rollback when:

- spoof acceptance is confirmed in a sensitive flow
- retry or failure spikes sharply after release
- one key channel becomes unreliable
- incident impact is already customer-visible

---

## Final takeaway

Troubleshooting works best when the system already logs:

- request IDs
- versions
- key intermediate signals
- channel and device metadata
- latency stages

Without that, the team ends up guessing.

---

## Related docs

- [15. Error Analysis](15-error-analysis.md)
- [16. Monitoring and Operations](16-monitoring-and-operations.md)
- [17. Security Hardening](17-security-hardening.md)
- [19. Model Governance](19-model-governance.md)

## Read next

Go to [22. Case Studies](22-case-studies.md).

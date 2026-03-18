# 03. Deployment Guide

## What this page covers

This page focuses on the practical side of taking face liveness from a model or SDK into a real production environment.

A system that works in a demo can still fail in production because of:

- poor device coverage
- unstable network conditions
- weak browser capture
- high latency
- missing injection defenses
- weak observability
- poorly tuned thresholds

---

## Deployment choices

## On-device vs server-side

| Choice | Strengths | Limitations |
|--------|-----------|-------------|
| On-device | lower round-trip latency, better privacy posture in some designs, can work better in unstable network conditions | device performance variation, app integration complexity, harder model management |
| Server-side | centralized control, easier model updates, unified logging and policy | more bandwidth use, transport security burden, latency depends on network |
| Hybrid | balanced approach, common in practice | more moving parts, careful interface design needed |

A hybrid design is often the most practical for eKYC.

---

## Mobile vs web

### Mobile app deployment
Usually gives stronger control over:
- camera capture quality
- device context
- anti-tampering controls
- UX guidance

### Web deployment
Often wins on reach and rollout speed, but requires stronger attention to:
- browser variability
- virtual camera / injection risk
- media API behavior
- cross-device consistency

---

## Runtime considerations

### Latency
Users notice delay quickly. Keep the full flow responsive.

Latency comes from:
- capture time
- upload time
- preprocessing
- model inference
- policy/risk services
- retries

### Bandwidth
Video-based or multi-frame flows can fail badly on weak networks. Compression, frame selection, and adaptive capture policy matter.

### Device performance
Low-end devices may struggle with:
- real-time challenge rendering
- high-resolution processing
- stable autofocus
- memory pressure

---

## Input quality and capture UX

Good deployment depends heavily on capture design.

Recommended controls:
- guide face size and framing
- warn about low light and backlight
- detect blur early
- handle glasses glare where possible
- prevent multi-face confusion
- keep instructions short and visible

A model is easier to trust when the capture process is also controlled well.

---

## Threshold and policy deployment

Do not push a liveness model into production without a deployment policy.

You need to define:
- pass threshold
- uncertain band
- retry rules
- max attempts
- manual review conditions
- model version ownership
- rollback conditions

The model output and the policy output should be treated separately.

---

## Monitoring and observability

Production systems should monitor at least:

- pass / retry / fail rates
- device-wise performance
- browser/app-version performance
- latency percentiles
- traffic spikes
- environment-specific failure patterns
- manual review escalation rate
- drift in score distribution

A sudden change in score distribution can indicate:
- a model issue
- capture UX regression
- a new attack pattern
- device-specific breakage

---

## Model updates

Model updates should be treated like a controlled release, not an isolated file replacement.

Recommended practice:
- keep model versioning explicit
- track training/evaluation baseline per version
- run shadow or canary rollout when possible
- compare old vs new score distributions
- keep rollback ready

---

## Security controls around deployment

A face liveness system should not trust raw capture blindly.

Deployment should consider:
- anti-injection protections
- request signing or secure session binding where relevant
- replay resistance
- transport encryption
- device integrity signals
- server-side validation of expected media properties
- secure logging with minimal sensitive retention

For deeper detail, see [Appendix A5 — Security and Privacy](appendix/A5-security-and-privacy.md).

---

## A practical rollout plan

### Phase 1 — controlled pilot
- limited device / region set
- higher manual review support
- strong instrumentation

### Phase 2 — threshold tuning
- compare fraud outcomes and genuine-user friction
- refine retry policy
- monitor device/browser splits

### Phase 3 — wider rollout
- expand traffic gradually
- monitor regressions daily
- keep rollback and feature flag controls ready

### Phase 4 — continuous improvement
- red-team regularly
- re-test on new devices
- review attack coverage periodically

---

## Practical takeaway

Good deployment is not just about choosing a model. It is about making the entire runtime system dependable under real-world conditions.

That means the team must think about:
- capture quality
- device diversity
- network variability
- policy design
- observability
- secure integration
- safe rollout strategy

# 16. Monitoring and Operations

## Who should read this page

This page is mainly for platform teams, ML operations teams, fraud operations teams, backend engineers, and release owners.

---

## Why this page exists

A liveness system is not finished when it goes live.

After launch, the real job becomes:

- monitoring behavior
- spotting drift
- detecting incidents
- protecting the user journey
- controlling regressions after updates

---

## What should be monitored

A good monitoring plan covers four layers.

| Layer | What to monitor |
|-------|-----------------|
| user journey | pass rate, retry rate, completion rate |
| security | spoof acceptance trends, attack spikes, security-signal events |
| model behavior | score distributions, calibration drift, disagreement between models |
| infrastructure | latency, timeouts, API errors, device/platform failures |

---

## A simple monitoring loop

```mermaid
flowchart LR
    A[Live traffic] --> B[Metrics and logs]
    B --> C[Dashboards and alerts]
    C --> D[Incident triage]
    D --> E[Fix, rollback, or retrain]
    E --> F[Release validation]
```

---

## Core business and UX metrics

| Metric | Why it matters |
|--------|----------------|
| pass rate | overall flow success |
| retry rate | hidden friction and ambiguity |
| completion rate | customer conversion impact |
| manual review rate | operational burden |
| abandonment rate | whether users leave mid-flow |

These are often more visible to product teams than model-specific metrics.

---

## Core security metrics

| Metric | Why it matters |
|--------|----------------|
| spoof acceptance trend | direct fraud exposure signal |
| attack-type concentration | shows what attackers are trying |
| injection / virtual-camera detections | indicates advanced attack activity |
| high-risk session rate | shows pressure on step-up flow |

---

## Core model and policy metrics

| Metric | Why it matters |
|--------|----------------|
| live score distribution | shows drift in genuine traffic |
| spoof score distribution | shows whether attacks are getting harder |
| calibration drift | thresholds may be aging |
| per-segment pass/retry/reject | catches hidden regressions |
| model disagreement rate | useful in fusion systems |

---

## Core infrastructure metrics

| Metric | Why it matters |
|--------|----------------|
| p50 / p95 / p99 latency | affects user experience |
| request failure rate | API stability |
| timeout rate | can look like model failure |
| SDK crash or camera error rate | client reliability |
| platform-specific failure rate | device and browser health |

---

## Dashboard slices that matter

Dashboards are more useful when they can be segmented by:

- flow type
- platform
- device class
- browser family
- SDK version
- app version
- geography if relevant
- model version
- policy version

Without slicing, major problems stay hidden inside averages.

---

## Alerting examples

| Alert example | Why it matters |
|---------------|----------------|
| retry rate jumps 30% on web | likely UX, threshold, or browser regression |
| spoof acceptance spikes in one channel | possible active attack campaign |
| p95 latency doubles after release | infrastructure or model-load issue |
| model disagreement jumps sharply | possible calibration or fusion regression |
| one SDK version has high capture failure | client release quality issue |

---

## Drift to watch for

Not all drift is fraud. Some drift is normal environmental change.

Useful drift categories:

- traffic mix drift
- device mix drift
- score distribution drift
- quality drift
- attack-pattern drift
- seasonal or campaign-based drift

The goal is to separate normal movement from dangerous change.

---

## Incident handling playbook

When a serious issue appears, teams should know the response path.

### Example incident flow

1. confirm the signal is real
2. identify affected channels and versions
3. classify as fraud, model, policy, SDK, or infrastructure issue
4. reduce impact with rollback or policy change if needed
5. run focused error analysis
6. document follow-up actions and owners

---

## Release gating and operations

Monitoring works best when tied to release policy.

Before a major release, define:

- key launch metrics
- rollback thresholds
- who approves release
- how long the guarded rollout lasts
- what traffic slices will be watched first

More on this is covered in [19. Model Governance](19-model-governance.md).

---

## What to log for safe operations

A useful operational record often includes:

- request ID
- channel and platform
- SDK / app / model version
- final decision
- intermediate scores or score bands
- quality signals
- latency
- retry count
- security signal summary

Keep privacy policy and retention rules in mind when designing logs.

---

## Example monitoring event

A monitoring-friendly event should preserve enough context to explain what happened without exposing more data than necessary.

```json
{
  "request_id": "req_34b9",
  "timestamp": "2026-03-18T11:42:09Z",
  "flow_type": "transaction_approval",
  "platform": "web",
  "browser_family": "chrome",
  "sdk_version": "web-2.4.1",
  "model_version": "fusion-0.6.4",
  "policy_version": "policy-2026-03-10",
  "decision": "retry",
  "decision_band": "uncertain",
  "latency_ms": 1288,
  "quality": {
    "blur_score": 0.31,
    "brightness_score": 0.42
  },
  "scores": {
    "passive": 0.58,
    "active": 0.62,
    "fusion": 0.61
  },
  "security": {
    "virtual_camera_signal": false,
    "injection_signal": false
  }
}
```

This kind of event supports dashboards, incident review, and threshold tuning.

---

## Example alert thresholds

| Signal | Example trigger | Typical first action |
|--------|------------------|----------------------|
| retry rate | +25% vs trailing 7-day baseline | check quality, browser, and threshold slices |
| p95 latency | above 2x normal for 15 minutes | inspect infrastructure, model load, and timeouts |
| disagreement rate | above normal after release | compare calibration and fusion versions |
| spoof acceptance proxy | spike in one flow or geography | tighten policy, review sessions, escalate fraud review |
| camera failures | one client version spikes | pause rollout or hotfix SDK |

---

## Need term help?

For terms used on this page, keep these references nearby:

- [Appendix A1 — Key Terms](appendix/A1-key-terms.md)
- [Appendix A3 — Metrics and Evaluation](appendix/A3-metrics-and-evaluation.md)
- [19. Model Governance](19-model-governance.md)

---

## Common operational mistakes

| Mistake | Why it hurts |
|---------|--------------|
| only monitoring overall pass rate | hides device and channel problems |
| not versioning thresholds and policy | makes regression analysis harder |
| no alert for disagreement or drift | fusion failures can stay invisible |
| no rollback plan | incidents take longer to control |
| keeping no post-launch review cadence | issues accumulate quietly |

---

## Final takeaway

A strong liveness deployment needs more than a strong model.

It needs:

- clear metrics
- segmented dashboards
- alerting
- incident response
- release discipline
- a feedback loop into data and model improvement

That is what turns a model into a reliable service.

---

## Related docs

- [15. Error Analysis](15-error-analysis.md)
- [17. Security Hardening](17-security-hardening.md)
- [19. Model Governance](19-model-governance.md)
- [21. Troubleshooting](21-troubleshooting.md)

## Read next

Go to [17. Security Hardening](17-security-hardening.md).

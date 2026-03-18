# Appendix A6 — Vendor Evaluation Checklist

## Purpose

Use this checklist when comparing face liveness vendors or even when comparing internal model options.

---

## 1. Threat coverage

- [ ] Does the solution clearly describe which attack groups it covers?
- [ ] Is print attack coverage demonstrated?
- [ ] Is replay attack coverage demonstrated?
- [ ] Are injection risks addressed, not only physical spoofing?
- [ ] Is there a stated plan or evidence for AI-generated media resilience?

---

## 2. Evaluation evidence

- [ ] Are results broken down by attack type?
- [ ] Are results broken down by device or environment?
- [ ] Is there clarity on test protocol and dataset construction?
- [ ] Are both false accepts and false rejects visible?
- [ ] Is operational latency measured, not only model inference latency?

---

## 3. Product and integration quality

- [ ] Is capture UX mature and understandable?
- [ ] Are SDKs or APIs stable and documented?
- [ ] Is there support for mobile, web, or both?
- [ ] Is the retry and fallback model configurable?
- [ ] Are logs and diagnostics available?

---

## 4. Security and privacy

- [ ] Are injection defenses explained?
- [ ] Is media transport protected?
- [ ] Is retention policy configurable?
- [ ] Are privacy and consent controls documented?
- [ ] Can the vendor explain security responsibilities clearly?

---

## 5. Operations

- [ ] Are model versions traceable?
- [ ] Is rollback support available?
- [ ] Is monitoring support available?
- [ ] Are incident and support processes clear?
- [ ] Is low-end device behavior understood?

---

## 6. Business fit

- [ ] Does the solution match the risk level of the target use case?
- [ ] Does the friction level match the conversion goals?
- [ ] Are pricing and scaling assumptions clear?
- [ ] Is deployment flexibility sufficient for your architecture?
- [ ] Is there clarity on roadmap and support commitments?

---

## Related detailed pages in this repo

- [Vendor evaluation framework](../10-business-strategy/vendor-evaluation.md)
- [Build vs buy](../10-business-strategy/build-vs-buy.md)
- [Cost analysis and ROI](../10-business-strategy/cost-roi.md)
- [Implementation roadmap](../10-business-strategy/implementation-roadmap.md)
- [RFP template](../appendices/rfp-template.md)

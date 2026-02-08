# 9.5 Legal & Contractual Framework

---

## Liability Framework

| Scenario | Typical Liability | Contractual Protection |
|----------|------------------|----------------------|
| Liveness bypass leads to fraud | Vendor (if within contracted performance) or Bank (if outside contracted scope) | SLA with APCER guarantees and financial penalties for breach |
| False rejection of genuine customer | Bank (customer relationship) | Insurance + vendor SLA on BPCER |
| Data breach of biometric data | Bank (as data controller under GDPR/DPDPA) | Data processor agreement with vendor |
| Regulatory non-compliance | Bank | Vendor provides compliance documentation and audit support |

## Key Contract Clauses for Liveness Vendors

| Clause | What to Include |
|--------|----------------|
| **Performance SLA** | APCER ≤ X% and BPCER ≤ Y% at defined operating point |
| **Availability SLA** | 99.9%+ uptime with defined maintenance windows |
| **Latency SLA** | P95 response time < 500ms |
| **Certification** | Maintain iBeta Level 1/2 certification (re-certify after major updates) |
| **Indemnification** | Vendor indemnifies for losses caused by PAD failures within SLA |
| **Data processing** | GDPR/DPDPA-compliant data processor agreement |
| **Audit rights** | Bank can audit vendor's security, data handling, model performance |
| **Model updates** | Minimum quarterly model updates with testing evidence |
| **Incident response** | Defined notification timelines and cooperation obligations |
| **Exit clause** | Data portability and transition support upon contract termination |

*Back to: [Security Hardening →](security-hardening.md)*

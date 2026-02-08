# 10.2 Vendor Evaluation Framework

---

## Evaluation Criteria Matrix

| Category | Criteria | Weight | Scoring (1-5) |
|----------|---------|--------|---------------|
| **Security** | iBeta Level 1 certification | 15% | 5=L2 certified, 4=L1, 3=Testing, 1=None |
| **Security** | Deepfake detection capability | 10% | 5=Real-time + offline, 3=Basic, 1=None |
| **Security** | Injection attack defense | 8% | 5=Comprehensive, 3=Basic, 1=None |
| **Performance** | APCER (overall) | 10% | 5=<0.1%, 3=<1%, 1=>5% |
| **Performance** | BPCER | 8% | 5=<1%, 3=<3%, 1=>5% |
| **Performance** | Latency (P95) | 5% | 5=<300ms, 3=<1s, 1=>3s |
| **UX** | Passive liveness support | 7% | 5=Full, 3=Partial, 1=Active only |
| **UX** | Drop-off rate | 5% | 5=<5%, 3=<10%, 1=>15% |
| **Compliance** | GDPR/DPDPA compliant | 7% | 5=Fully, 3=Partially, 1=No |
| **Compliance** | Data residency options | 5% | 5=Any region, 3=Major regions, 1=US only |
| **Technical** | SDK size (mobile) | 3% | 5=<5MB, 3=<10MB, 1=>20MB |
| **Technical** | Platform coverage | 5% | 5=iOS+Android+Web, 3=Mobile only, 1=Single |
| **Technical** | On-device inference option | 3% | 5=Full, 3=Partial, 1=None |
| **Business** | Pricing model | 4% | 5=Per-transaction, 3=Tiered, 1=Fixed high |
| **Business** | SLA guarantees | 5% | 5=Strong with penalties, 3=Basic, 1=None |

## PoC Testing Protocol

| Phase | Duration | Activities |
|-------|----------|-----------|
| **Phase 1: Technical Integration** | 1-2 weeks | SDK integration, API connectivity, basic functionality |
| **Phase 2: Security Testing** | 2-3 weeks | Internal attack testing (10+ PAI species), injection testing |
| **Phase 3: UX Testing** | 1-2 weeks | User testing with 50+ subjects, drop-off measurement |
| **Phase 4: Scale Testing** | 1 week | Load testing, latency measurement, failure mode testing |
| **Phase 5: Evaluation** | 1 week | Score against criteria matrix, vendor comparison |

*Next: [Cost Analysis & ROI →](cost-roi.md)*

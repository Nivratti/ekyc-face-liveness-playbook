# 10.3 Cost Analysis & ROI

---

## Cost Components

| Component | One-Time | Annual Recurring |
|-----------|----------|-----------------|
| SDK/API license | $0-50K (setup) | $100K-500K (volume-dependent) |
| Integration development | $50K-200K | $20K-50K (maintenance) |
| Infrastructure (GPU) | $0 (if cloud API) | $50K-200K (if self-hosted) |
| iBeta certification (if in-house) | $30K-80K | $15K-30K (re-certification) |
| Security testing | $20K-50K | $10K-30K |
| Compliance & legal | $10K-30K | $5K-15K |
| **Total (Buy)** | **$80K-300K** | **$150K-600K** |
| **Total (Build)** | **$500K-2M** | **$300K-1M** |

## ROI Model

```
Annual Fraud Prevention Savings:
  Digital onboarding attempts/year:     500,000
  Attempted fraud rate:                 0.5% (2,500 attacks)
  Average fraud loss per success:       $5,000
  
  Without liveness (80% attack success): 2,000 × $5,000 = $10,000,000
  With liveness (0.5% success):          12 × $5,000  = $60,000
  
  Annual fraud savings:                  $9,940,000

Operational Savings:
  Branch KYC cost/verification:          $30
  Digital KYC cost/verification:         $1.50
  Annual verifications:                  500,000
  Annual operational savings:            $14,250,000

Total Annual Benefit:                    $24,190,000
Total Annual Cost (Buy model):           $300,000
ROI:                                     80x
Payback Period:                          < 2 months
```

*Next: [Implementation Roadmap →](implementation-roadmap.md)*

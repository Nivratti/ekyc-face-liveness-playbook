# 7.3 Video KYC (V-CIP)

---

## RBI V-CIP Framework

Video-based Customer Identification Process (V-CIP) is an **RBI-approved method** for remote KYC in India, where a bank official conducts a live video call with the customer.

## How Liveness Integrates with V-CIP

```mermaid
graph TD
    A["Customer connects\nto video call"] --> B["Automated liveness\ncheck runs\ncontinuously"]
    B --> C["Bank official\nverifies identity\nvia video"]
    C --> D["Official captures\nscreenshots as\nevidence"]
    D --> E["Automated face\nmatching against\nID document"]
    E --> F["V-CIP session\nrecorded and\narchived"]
```

| V-CIP Requirement | Liveness Role |
|-------------------|---------------|
| Real-time interaction | Continuous liveness monitoring throughout call |
| Customer identification | Liveness + face matching against ID |
| Geo-tagging | Verify customer's claimed location matches device GPS |
| Video recording | Ensure recorded video is of live person (not replayed) |
| Official verification | Liveness assists official; doesn't replace human judgment |

*Next: [Loan Disbursement →](loan-disbursement.md)*

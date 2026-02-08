# 2.5 Comparison Matrix

---

## Comprehensive Comparison

| Criteria | Active | Passive | Hybrid | Hardware-Assisted |
|----------|--------|---------|--------|-------------------|
| **User Experience** | ⭐⭐⭐ Moderate | ⭐⭐⭐⭐⭐ Excellent | ⭐⭐⭐⭐ Good | ⭐⭐⭐⭐⭐ Excellent |
| **Security (2D)** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| **Security (3D Masks)** | ⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| **Security (Deepfakes)** | ⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| **Security (Injection)** | ⭐⭐⭐ | ⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| **Accessibility** | ⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐ (device dependent) |
| **Drop-off Rate** | 10-25% | 2-5% | 5-10% | 2-5% |
| **Processing Time** | 5-15s | 1-3s | 2-8s | 1-2s |
| **Device Requirements** | Camera + Display | Camera only | Camera + Display | Specialized sensors |
| **Regulatory Acceptance** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ Growing | ⭐⭐⭐⭐⭐ Highest | ⭐⭐⭐⭐ |
| **Implementation Cost** | Medium | Medium | High | Low (SDK) |
| **Maintenance Cost** | Medium | Medium | High | Low |
| **Scalability** | Good | Excellent | Good | Limited by device |

---

## Decision Matrix for Banking

```mermaid
graph TD
    A["What is your\nprimary deployment?"] --> B{"Mobile App?"}
    B -->|"Yes"| C{"User base\ndevice diversity?"}
    B -->|"No (Web/Kiosk)"| D{"Controlled\nhardware?"}
    
    C -->|"High diversity\n(India, SEA, Africa)"| E["Hybrid:\nPassive-first +\nActive escalation"]
    C -->|"Flagship devices\n(Developed markets)"| F["Hybrid with\nhardware signals\nwhen available"]
    
    D -->|"Yes (ATM/Kiosk)"| G["Hardware-assisted\n(NIR + RGB)"]
    D -->|"No (Web browser)"| H["Passive primary +\nDevice attestation"]
    
    style E fill:#1B4F72,color:#fff
    style F fill:#2471A3,color:#fff
    style G fill:#27ae60,color:#fff
    style H fill:#f39c12,color:#fff
```

!!! success "The Banking Recommendation"
    **Hybrid (passive-first with active escalation)** is the recommended approach for most banking deployments. It provides the best balance of security, user experience, accessibility, and regulatory compliance.

---

*Next: [Part III — Attack Taxonomy Overview →](../03-attack-landscape/taxonomy-overview.md)*

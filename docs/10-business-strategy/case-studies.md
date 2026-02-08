# 10.5 Case Studies

---

## Case 1: Large Indian Private Bank — Digital Onboarding Transformation

| Aspect | Before | After |
|--------|--------|-------|
| **KYC method** | Branch-based with Aadhaar biometric | Digital eKYC with face liveness |
| **Onboarding time** | 3-5 days | 8 minutes average |
| **Monthly new accounts** | 45,000 | 180,000 |
| **Cost per account** | ₹350 ($4.20) | ₹25 ($0.30) |
| **Fraud rate** | 0.4% | 0.03% |
| **Liveness approach** | N/A | Hybrid (passive + active) |
| **Key challenge** | High device diversity (budget Android phones) | Tuned for low-end devices, progressive quality guidance |

## Case 2: European Neobank — Deepfake Attack Incident

| Timeline | Event |
|----------|-------|
| **Month 1** | Neobank launches with passive-only liveness (vendor A) |
| **Month 4** | Fraud team detects 23 accounts opened with AI-generated faces (StyleGAN) |
| **Month 5** | Investigation reveals additional 150+ synthetic identity accounts |
| **Month 6** | Switched to vendor B with deepfake detection; added active challenges for high-risk |
| **Month 8** | Synthetic identity fraud dropped to zero; overall fraud rate down 94% |
| **Lesson** | Passive-only liveness without deepfake detection is insufficient for digital banking |

## Case 3: Southeast Asian Digital Bank — Accessibility-Driven Design

| Challenge | Solution | Result |
|-----------|----------|--------|
| Diverse user base including elderly with limited tech literacy | Passive-first approach with simple guidance overlay | 89% first-attempt completion rate |
| Multiple languages (Thai, Malay, Bahasa, English) | Localized challenge prompts and guidance | 12% improvement in completion for non-English speakers |
| Hot climate causing face moisture/reflection issues | Adaptive specular highlight handling | 40% reduction in outdoor false rejections |
| Low-end devices (< $100 phones) | Lightweight on-device model + server-side verification | Works on devices with 2GB RAM |

*Next: [Future Trends →](future-trends.md)*

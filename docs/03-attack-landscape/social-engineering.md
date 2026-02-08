# 3.6 Social Engineering & Process Attacks

---

## Overview

These attacks exploit **human factors and process weaknesses** rather than technology. They are particularly dangerous because the person presenting to the camera IS a live human — so liveness detection alone cannot stop them.

---

## Attack Types

### Coercion & Duress

| Attack | Description | Detection | Mitigation |
|--------|-------------|-----------|------------|
| **Physical coercion** | Victim forced to complete liveness under threat | Stress detection (micro-expressions, pupil dilation) — unreliable | Duress codes, behavioral analytics, post-verification checks |
| **Social engineering of victim** | Victim tricked into completing liveness ("verify your account") | N/A — victim cooperates willingly | Customer education, transaction confirmation via separate channel |
| **Insider collusion** | Bank employee manipulates verification or overrides results | N/A at technology level | Dual-approval workflows, audit trails, insider threat monitoring |

### Identity Exploitation

| Attack | Description | Why Liveness Can't Help | Mitigation |
|--------|-------------|------------------------|------------|
| **Identical twins** | Twin passes liveness and face matching for sibling | Twin IS live and looks like the target | Secondary verification (OTP to registered phone), behavioral biometrics, knowledge-based verification |
| **Lookalike** | Person with similar appearance attempts verification | Person IS live | High-precision face matching (tighter thresholds), document verification |
| **Willing account mule** | Legitimate person knowingly opens account for criminal use | Person is genuinely who they claim to be | Transaction monitoring, behavioral analytics, network analysis |

### Process Manipulation

| Attack | Description | Mitigation |
|--------|-------------|------------|
| **Fallback exploitation** | Deliberately fail digital liveness to trigger weaker manual process | Ensure fallback processes are equally secure; don't make manual review "easier" |
| **Session timing exploit** | Pass liveness, then manipulate data before face matching runs | Atomic session processing; server-side orchestration; no client-controlled timing |
| **Review queue manipulation** | Flood manual review queue with fraudulent applications to overwhelm reviewers | Prioritized queuing, automated pre-screening, reviewer capacity planning |

---

## Key Insight

!!! warning "Technology Alone Is Insufficient"
    Social engineering attacks require **process-level defenses**: dual approvals, audit trails, behavioral monitoring, customer education, and insider threat programs. No liveness system, no matter how advanced, can detect a willing participant or an insider.

---

*Next: [Adversarial ML Attacks →](adversarial-ml.md)*

# 02. eKYC Integration

## What this page covers

This page explains where face liveness fits inside the **full remote eKYC flow**.

The main idea is simple:

> Face liveness should not be treated as a standalone feature. It should sit at the right point in the capture, identity, fraud, and decision pipeline.

---

## A typical remote eKYC flow

A common flow looks like this:

1. User starts onboarding
2. Device or browser permissions are checked
3. ID document capture happens
4. Document verification happens
5. Selfie or short video capture happens
6. Face quality checks run
7. Face liveness runs
8. Face match runs against the ID portrait or enrolled face
9. Other fraud and risk checks run
10. Final policy decision is made
11. Audit records are stored

Some regulated or high-risk flows may add extra steps, but this structure is a good mental model.

---

## Where liveness should sit

In most flows, face liveness should happen **before you fully trust the selfie for identity comparison**.

Why? Because a clean face match score does not prove the media is real.

### Common placement patterns

#### Pattern A — quality check → liveness → face match
This is often the clearest production flow.

Benefits:

- bad input is rejected early
- compute is not wasted on obviously unusable capture
- live presence is checked before identity trust increases

#### Pattern B — liveness and face match in parallel
Useful when latency matters and the final decision waits for both results.

Benefits:

- faster end-to-end flow
- good for optimized production systems

Watchouts:

- the policy layer must still treat both checks separately
- a strong face match should not hide a weak liveness result

#### Pattern C — adaptive flow
Use passive liveness first, then ask for an active challenge only when risk is high or confidence is weak.

Benefits:

- better balance of security and user experience
- lower friction for good users

---

## A simple decision pipeline

### Step 1 — capture checks
Check for things like:

- single face present
- enough brightness
- acceptable blur
- stable framing
- face size in range

### Step 2 — liveness result
Possible outcomes:

- pass
- uncertain
- fail

### Step 3 — face match result
Possible outcomes:

- strong match
- weak match
- no match

### Step 4 — risk policy
Bring in supporting signals such as:

- document confidence
- device risk
- prior fraud signals
- retry history
- account policy

### Step 5 — final action
Possible actions:

- auto approve
- retry
- stronger challenge
- manual review
- hard reject

---

## Why retry logic matters

Retry is not only a UX feature. It is part of security design.

### Good retry design

- explains the issue clearly
- separates quality problems from spoof suspicion
- caps the number of attempts
- logs why each retry happened
- can increase scrutiny after repeated uncertainty

### Bad retry design

- vague messages such as “verification failed”
- unlimited retries
- no difference between blur and spoof suspicion
- repeated use of the exact same weak path

---

## Manual review and fallback

Some systems need fallback for users who cannot pass the normal flow because of:

- poor network conditions
- weak camera hardware
- accessibility needs
- repeated uncertainty
- regulated cases that require human review

Fallback is necessary, but it must be designed carefully. A weak fallback path can become the easiest fraud bypass.

---

## Audit trail and explainability

A production eKYC system should record enough information to answer:

- what capture was attempted
- which quality checks passed or failed
- what liveness result was produced
- what face match result was produced
- what final decision was made
- which model version and policy version were active

This is useful for fraud review, incident response, model monitoring, customer support, and regulatory traceability.

---

## Integration patterns

### Mobile SDK flow
Common when the team wants stronger control over capture UX, device signals, and runtime behavior.

### Web SDK flow
Useful for faster rollout and broad reach, but browser variability and injection hardening matter more.

### Backend API flow
Useful for centralized decisioning, but raw media transport, latency, privacy, and secure session binding become more important.

### Hybrid flow
Capture and some checks happen on device, while deeper scoring and policy run on the server.

This is often the most practical design in real systems.

---

## A recommended default approach

For many eKYC systems, a good default structure is:

1. quality gating
2. passive liveness
3. active challenge only when needed
4. face match
5. risk fusion
6. final policy decision

This usually gives a good balance of security, conversion, and operational control.

---

## Practical takeaway

The most important design mistake is treating face liveness like a detached model score.

It should be integrated into:

- capture quality
- retry policy
- face match logic
- broader fraud checks
- final business decisioning
- audit and review workflows

When it is placed correctly in the flow, face liveness becomes much more valuable and easier to operate.

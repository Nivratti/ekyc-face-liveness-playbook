# 02. eKYC Integration

## What this page covers

This page explains where face liveness fits into the **end-to-end eKYC workflow**.

The main idea is simple:

> Face liveness should not be treated as a standalone feature. It should be placed at the right point in the capture, identity, fraud, and decision pipeline.

---

## Typical remote eKYC flow

A common flow looks like this:

1. User starts onboarding
2. Device/browser permissions are checked
3. Document capture happens
4. Document verification happens
5. Selfie or video capture happens
6. Face quality checks run
7. Face liveness runs
8. Face match against document portrait or enrolled face runs
9. Additional fraud/risk checks run
10. Final policy decision is made
11. Audit trail is stored

Depending on the business and regulation, some steps may be reordered or expanded.

---

## Where liveness should be placed

In most flows, face liveness should happen **before trusting the selfie for identity comparison**.

That is because a clean face match score is not enough if the image or video itself is spoofed.

### Common placement options

#### Option A — quality check first, then liveness, then face match
This is often the clearest production flow.

- reject unusable captures early
- avoid wasting compute on clearly bad input
- validate live presence before identity comparison

#### Option B — run liveness and face match in parallel
Useful when low latency matters and the system can safely gate the final decision after both results are available.

#### Option C — adaptive flow
Use passive liveness first, then ask for active challenge only when confidence is weak or risk is high.

---

## Example decision pipeline

### Step 1: Capture checks
Look for:
- face present
- single face
- enough brightness
- acceptable blur
- stable framing

### Step 2: Liveness decision
Possible outputs:
- pass
- uncertain / retry
- fail

### Step 3: Face match
Possible outputs:
- strong match
- weak match
- no match

### Step 4: Risk policy
Bring in:
- document confidence
- device risk
- prior fraud signals
- retry history
- business rules

### Step 5: Final action
Possible actions:
- auto approve
- ask for retry
- ask for stronger challenge
- escalate to manual review
- hard reject

---

## Retry logic matters

A retry is not just a UX detail. It is part of the security and conversion design.

### Good retry design
- explain the issue clearly
- distinguish quality problems from spoof suspicion
- cap retry attempts
- log why each retry happened
- use stronger checks after repeated uncertainty

### Bad retry design
- vague error messages
- unlimited retries
- using the same weak logic every time
- no separation between quality failure and fraud suspicion

---

## Manual review and fallback

Some systems need a fallback path for:

- poor network or device conditions
- accessibility constraints
- older devices with weak camera performance
- users who repeatedly land in the uncertain band
- regulated flows that require human review

Fallback must be designed carefully. A weak fallback can become the easiest bypass path.

---

## Audit trail and explainability

A production eKYC system should record enough evidence to answer:

- what capture was attempted
- what quality checks failed or passed
- what liveness result was produced
- what face match result was produced
- what final decision was made
- which model version and policy version were active

This helps with fraud review, incident response, model monitoring, and regulator-facing traceability.

---

## Integration patterns

### Mobile SDK flow
Common when the business wants stronger control over capture UX and device context.

### Web SDK flow
Useful for fast rollout and broad reach, but browser and injection hardening become especially important.

### Backend API flow
Useful for centralized decisioning, but raw media transport, latency, and privacy handling matter more.

### Hybrid flow
Capture and some quality steps on device, with deeper scoring and policy on the server.

---

## Practical guidance

In most real eKYC systems, the strongest structure is:

1. quality gating
2. passive liveness
3. adaptive challenge only when needed
4. face match
5. risk fusion
6. final policy decision

This gives a good balance of security, usability, and operational control.

---

## What to read next

- For engineering choices: [03. Deployment Guide](03-deployment-guide.md)
- For do-and-don't guidance: [04. Best Practices](04-best-practices.md)
- For deeper architecture: `docs/04-technical-architecture/`

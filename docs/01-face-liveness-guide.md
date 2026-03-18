# 01. Face Liveness Guide

## What face liveness means

Face liveness verifies that the face presented to the camera belongs to a **real person who is physically present** during capture.

This is important because a face recognition system can correctly match a face to an ID document and still be fooled by a spoof. For example, an attacker might show a printed photo, replay a recorded video, inject a digital stream, or use AI-generated content.

So in remote eKYC:

- **face matching** confirms identity similarity
- **face liveness** confirms physical presence and authenticity of the capture

Both are often necessary.

---

## Why it matters in eKYC

Remote onboarding and remote authentication remove the safety of in-person supervision. That creates fraud opportunities.

Without liveness, a system may accept:

- a photo of the target person displayed on another phone
- a replayed video of the target person blinking or smiling
- a mask or partial disguise designed to pass capture checks
- an injected camera stream from a compromised device or browser
- AI-generated or manipulated content that looks realistic enough to fool weak systems

Face liveness reduces this risk. It is now a core control in digital onboarding, video KYC, account recovery, and step-up verification.

---

## Face liveness vs face match

| Question | Face match | Face liveness |
|----------|------------|---------------|
| Main purpose | Compare identity similarity | Detect whether the sample is live and genuine |
| Main output | similarity / match score | liveness score or live/spoof decision |
| Typical failure without the other | may accept a spoof of the right person | may confirm live presence but not identity |
| In eKYC | usually used with document/face comparison | usually used before or alongside final face decision |

A common mistake is to treat face match as enough. It is not.

---

## Main types of face liveness

### Passive liveness

**What it is**
Passive liveness tries to detect spoofing from one image or a short capture sequence without asking the user to do a challenge.

**How it works**
It looks for cues such as texture, lighting behavior, moire patterns, screen artifacts, face depth hints, motion consistency, or learned spoof signatures.

**Why teams like it**
- fast user flow
- lower friction
- easier for users with accessibility constraints

**Limitations**
- can be harder to defend against strong replay or injection attacks
- quality and device variation can affect reliability

### Active liveness

**What it is**
Active liveness asks the user to perform a challenge, such as turn the head, blink, smile, or follow an on-screen prompt.

**Why it helps**
It makes simple presentation attacks harder because the attacker must respond correctly in real time.

**Limitations**
- higher user friction
- can increase drop-off or retry rate
- challenge design matters a lot

### Hybrid liveness

**What it is**
Hybrid liveness combines passive and active signals.

**Why it is common**
It gives a better balance between security and user experience. Many real systems use passive checks first and invoke active challenge only when needed.

---

## Common attack groups

A simple way to understand attacks is to divide them into four groups.

### 1. Physical presentation attacks
Examples:
- printed photo
- cut-out eye photo
- photo on glossy paper
- replay on tablet or phone
- 2D or 3D mask

### 2. Digital and injection attacks
Examples:
- virtual camera feed
- emulator-based spoofing
- camera API tampering
- direct image or video injection into the pipeline

### 3. AI-assisted attacks
Examples:
- deepfake video
- face swap
- generative image spoof
- motion-driven avatar style attacks

### 4. Process and operational attacks
Examples:
- coached user behavior
- device compromise
- fraud rings using stolen media
- bypass via weak fallback flows

For the full breakdown, see [Appendix A2 — Attack Taxonomy](appendix/A2-attack-taxonomy.md).

---

## Input quality still matters

A strong model cannot fully save poor capture quality.

Common problems:
- low light or strong backlight
- blur due to hand movement
- face too small in frame
- face partially outside frame
- occlusion from glasses glare, mask, hair, cap, hand, or phone edge
- aggressive image compression
- old front camera or unstable browser capture

A good production system should check quality before or during liveness, not after a hard failure.

---

## Simple pipeline view

A practical face liveness pipeline usually looks like this:

1. Capture image or short video
2. Detect the face
3. Run quality checks
4. Extract liveness signals or features
5. Produce a liveness score
6. Apply threshold and policy
7. Pass, retry, escalate, or fail
8. Combine with face match and other risk signals if needed

In stronger systems, the final decision may also use:
- device risk
- document verification results
- fraud history
- geo / IP signals
- account risk policies

---

## Scores, thresholds, and decisions

A liveness score is not useful by itself unless it is connected to decision policy.

### Example policy
- **high score** → pass
- **medium score** → retry or active challenge
- **low score** → fail or manual review

Thresholds always involve trade-offs:

- a stricter threshold reduces spoof acceptance risk
- a stricter threshold can also increase false rejects for genuine users

This is why threshold tuning must be done on realistic data, not only on ideal lab samples.

---

## What to measure

The most useful practical measures are:

- spoof acceptance risk
- genuine user rejection risk
- retry rate
- completion rate
- latency
- device coverage
- environmental robustness

The detailed metric discussion is in [Appendix A3 — Metrics and Evaluation](appendix/A3-metrics-and-evaluation.md).

---

## Where teams usually make mistakes

Common mistakes include:

- using face match without liveness in remote onboarding
- evaluating only on easy datasets
- ignoring injection attacks
- assuming one good benchmark number proves production readiness
- testing only on flagship phones
- failing to separate retry logic from hard reject logic
- not monitoring drift after launch

---

## Practical takeaway

For most eKYC systems, a good face liveness approach is not just a model. It is a full control layer that includes:

- capture design
- input quality checks
- spoof detection
- threshold policy
- retry and fallback logic
- security hardening
- monitoring and periodic re-evaluation

Face liveness works best when it is treated as part of a broader trust pipeline, not as a single score in isolation.

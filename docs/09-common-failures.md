# 09. Common Failures

## Who should read this page

This page is useful for QA teams, ML engineers, product teams, support teams, and anyone trying to understand why a face liveness system behaves well in some cases and poorly in others.

---

## Why this page exists

The most important lessons in face liveness often come from failures.

If teams only study successful cases, they miss the exact situations that create friction, support tickets, and fraud risk in production.

---

## A simple way to think about failures

Most failures come from one or more of these groups:

- weak input quality
- attack sophistication
- device or platform limitations
- policy or threshold problems
- integration mistakes

---

## Failure group 1: Input quality problems

### Examples

- face too small in frame
- strong blur from hand motion
- low light or strong backlight
- partial face crop
- heavy occlusion from mask, glasses, or hair

### Typical result
The system may reject a genuine user or produce unstable scores.

### What helps

- better capture guidance
- quality checks before liveness
- limited guided retries
- minimum face size and framing rules

---

## Failure group 2: Replay and screen-based attacks

### Examples

- video replay on a phone screen
- replay on a bright tablet
- replay recorded in good lighting with high image quality

### Why these are tricky
A replay can look visually clean and still be fraudulent. Strong visual quality is not the same as strong liveness evidence.

### What helps

- evaluate specifically against replay attacks
- test different screens, brightness levels, and camera distances
- use stronger policy in high-risk flows

---

## Failure group 3: Injection and virtual camera attacks

### Examples

- injected image stream instead of live camera feed
- emulator or tampered app path
- virtual camera in browser or desktop workflow

### Why these are serious
These attacks may bypass many surface-level capture assumptions.

### What helps

- secure capture path controls
- client integrity checks where possible
- browser and app hardening
- environment-specific testing

---

## Failure group 4: AI-generated or manipulated content

### Examples

- deepfake video
- face swap overlay
- AI-enhanced replay
- synthetic identity media

### Why these matter
Attack quality is improving quickly. A system that was tested only against older print and replay attacks may not be ready for newer synthetic content.

### What helps

- include modern attack classes in evaluation
- monitor for new fraud patterns after launch
- retest regularly rather than assuming past results still hold

---

## Failure group 5: Threshold and policy mistakes

### Examples

- threshold too strict, causing too many genuine rejects
- threshold too weak, allowing spoof risk
- unlimited retries
- weak fallback path after repeated uncertain results

### What helps

- calibrate on local data
- document score bands clearly
- evaluate retry policy, not just model score
- review edge cases before go-live

---

## Failure group 6: Device and environment mismatch

| Problem | Why it matters |
|---------|----------------|
| low-end phone camera | noisier and less stable input |
| browser webcam | weaker consistency than app SDK in many cases |
| poor network | can affect video workflows and user patience |
| old OS or browser | may break expected capture behavior |

### What helps
Segment testing and monitoring by device, platform, browser, and app version.

---

## Failure group 7: Integration mistakes

### Examples

- frontend misreads the response payload
- backend treats `success=true` as automatic approve
- score scale changes after a model update but policy is not updated
- retryable quality failure is shown as a hard fraud reject

### What helps

- stable API envelope
- explicit decision layer after raw model response
- versioned model and policy
- integration tests that include bad-input and error cases

---

## Failure group 8: Human and operational issues

### Examples

- support team cannot explain a failure reason
- review team sees too many uncertain cases
- fraud team cannot trace which policy version was used
- monitoring dashboards hide segment-level spikes

### What helps

- better logging and diagnostics
- clear reason codes
- segment-level dashboards
- documented escalation paths

---

## Failure review template

When a failure happens, ask:

1. Was the input quality acceptable?
2. Was the attack type covered in testing?
3. Did the device or channel behave as expected?
4. Did policy handle uncertainty correctly?
5. Was the integration reading the model output correctly?
6. Can we explain the failure in logs and analytics?

This creates a better failure culture than blaming the model alone.

---

## Common examples by symptom

| Symptom | Possible causes |
|---------|-----------------|
| too many genuine rejects in dim rooms | threshold too strict, low-light weakness, poor guidance |
| spoof passes on web only | browser capture path weakness, virtual camera or injection risk |
| score unstable across retries | weak capture consistency, noisy quality conditions |
| manual review load too high | uncertain band too wide, poor quality gate, policy not tuned |
| support cannot explain failures | weak diagnostics and reason codes |

---

## Final takeaway

A strong face liveness program does not aim for zero failures. It aims for failures that are:

- understood
- measured
- limited in impact
- fixable by design, testing, or policy change

That is how systems improve over time.

---

## Related docs

- [06. API and Response Examples](06-api-and-response-examples.md)
- [07. Decision Logic](07-decision-logic.md)
- [08. Evaluation Playbook](08-evaluation-playbook.md)
- [Appendix A5 — Security and Privacy](appendix/A5-security-and-privacy.md)

## Read next

Go to [10. Product Guide](10-product-guide.md).

# 04. Best Practices

## Use this page as a practical checklist

This page summarizes the most important things teams should do when planning, evaluating, deploying, and maintaining a face liveness system for eKYC.

---

## Before choosing a model or vendor

### Be clear about the use case
A low-risk login flow and a high-risk remote onboarding flow do not need the same balance of security and friction.

### Define the threat model
List the attacks you care most about:
- print attacks
- replay attacks
- injection attacks
- mask attacks
- AI-generated media
- process abuse and weak fallback abuse

### Decide what “good enough” means
You should define acceptable targets for:
- spoof acceptance risk
- genuine user rejection risk
- latency
- completion rate
- retry rate

---

## During solution evaluation

### Test on realistic data
Do not rely only on clean benchmark samples.

Test across:
- phones and browsers
- low light and backlight
- blur and motion
- glasses and occlusion
- different skin tones, age groups, and face shapes
- different attack instruments and screen types

### Evaluate the full pipeline
A vendor demo may show only the model score. You need to understand:
- capture UX
- retry policy
- API behavior
- logging quality
- device support
- security hardening

### Separate product claims from evidence
Ask for clear evidence by attack type, device type, and evaluation setting.

---

## During system design

### Keep quality checks before expensive or decisive steps
Bad input should be handled early.

### Treat uncertain scores differently from hard fails
A three-way policy is usually better than a binary policy:
- pass
- retry / escalate
- fail

### Keep face match and liveness logically separate
Do not merge them so early that operators cannot reason about failure causes.

### Design fallback carefully
Fallback is necessary in some environments, but a weak fallback path can become the easiest fraud bypass.

---

## During deployment

### Start with controlled rollout
Pilot first. Measure behavior before full launch.

### Monitor by segment, not just overall average
Track by:
- device model
- OS version
- app version
- browser family
- region
- network quality

### Keep model version and policy version visible
When outcomes shift, you need to know what changed.

---

## After go-live

### Monitor drift continuously
Watch for changes in:
- score distribution
- retry rate
- fail rate
- manual review rate
- fraud outcomes

### Retest against new attacks
Attackers adapt. New screen technologies, generative media methods, and injection tools can change risk quickly.

### Review accessibility and fairness impact
A secure system that blocks too many genuine users creates operational and business problems.

---

## Common mistakes to avoid

### Mistake 1 — using only one benchmark number
A single summary metric hides too much.

### Mistake 2 — ignoring injection attacks
Strong photo defense is not enough if the pipeline accepts injected media.

### Mistake 3 — tuning only for best-case devices
Production traffic is not made of flagship phones only.

### Mistake 4 — unlimited retries
Too many retries can help attackers probe the system.

### Mistake 5 — weak incident response preparation
You need a plan for sudden attack waves, model regressions, or device-specific failures.

---

## Recommended production checklist

- [ ] clear threat model documented
- [ ] quality gate defined
- [ ] liveness thresholds defined
- [ ] uncertain band / retry band defined
- [ ] retry cap defined
- [ ] manual review policy defined
- [ ] device coverage tested
- [ ] low-light and edge cases tested
- [ ] injection risk reviewed
- [ ] logging and monitoring in place
- [ ] model and policy versioning in place
- [ ] rollback plan ready
- [ ] privacy and retention policy reviewed
- [ ] post-launch monitoring owner assigned

---

## Final takeaway

The best face liveness systems are not only accurate. They are also:

- understandable
- measurable
- operationally safe
- secure against realistic attacks
- manageable after launch

That is why successful teams treat face liveness as a product and platform capability, not just a model output.

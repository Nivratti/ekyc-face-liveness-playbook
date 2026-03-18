# Appendix A2 — Attack Taxonomy

## Purpose

This appendix groups the main attack types that matter for face liveness in eKYC.

The main guide keeps this topic short so it stays easy to read. This appendix provides a fuller map.

---

## 1. Physical presentation attacks

These attacks present something to the camera as if it were a live face.

### Common examples
- printed photo
- glossy photo with realistic lighting
- cut-out eye photo
- photo bent to simulate shape
- replayed video on phone, tablet, or laptop
- wearable mask or partial mask
- mannequin-style display

### Why they matter
These are often the first attacks teams test against, but they vary widely in realism and difficulty.

---

## 2. Digital and injection attacks

These attacks bypass normal physical capture and try to insert media directly into the pipeline.

### Common examples
- virtual camera feed
- emulator-generated camera stream
- hooked camera API
- direct upload injection where live capture was expected
- browser or app instrumentation bypass
- pre-recorded sequence inserted into the SDK or API flow

### Why they matter
A system that only focuses on physical spoofing may still be vulnerable if the media pipeline itself is weak.

---

## 3. AI-assisted attacks

These attacks use generative or manipulation methods to create more believable spoof media.

### Common examples
- generated face image made to resemble the target
- manipulated video with changed facial motion
- face swap on a live or recorded source
- deepfake-style synthesis
- expression transfer and lip-sync driven attacks

### Why they matter
These attacks continue to improve in quality and can reduce the usefulness of simple texture-only defenses.

---

## 4. Process and operational attacks

These attacks exploit workflow weaknesses rather than only the model.

### Common examples
- social engineering during assisted onboarding
- fraud agent coaching the user or operator
- abuse of manual review or fallback route
- device sharing or controlled capture environment
- repeated probing through unlimited retry logic

### Why they matter
A strong model can still fail inside a weak process.

---

## 5. Environment and capture manipulation

These do not always look like classic spoofing, but they can help an attacker or confuse the system.

### Examples
- extreme backlight
- low light noise
- intentional blur
- partial occlusion
- reflective glasses glare
- screen moire and aliasing artifacts used strategically

---

## Practical grouping for real deployments

A useful production grouping is:

| Group | Typical control focus |
|------|------------------------|
| Print / replay | passive + active PAD, capture guidance |
| Mask / advanced physical spoof | stronger challenge and multi-signal logic |
| Injection | SDK hardening, API validation, session security |
| AI-generated media | stronger model design, continuous retesting |
| Process abuse | policy design, operator training, auditability |

---

## Detailed topic pages in this repo

Use these original deep-dive pages for more detail:

- [Attack taxonomy overview](../03-attack-landscape/taxonomy-overview.md)
- [Physical attacks](../03-attack-landscape/physical-attacks.md)
- [Digital and injection attacks](../03-attack-landscape/digital-attacks.md)
- [AI and generative attacks](../03-attack-landscape/ai-generative-attacks.md)
- [Deepfakes](../03-attack-landscape/deepfakes.md)
- [Social engineering and process attacks](../03-attack-landscape/social-engineering.md)
- [Adversarial ML attacks](../03-attack-landscape/adversarial-ml.md)

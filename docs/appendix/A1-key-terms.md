# Appendix A1 — Key Terms

## Purpose

This glossary explains the most important face liveness terms in plain English.

| Term | Simple meaning |
|------|----------------|
| Face liveness | A check that tries to confirm a real person is physically present during capture |
| PAD | Presentation Attack Detection; the general term for detecting spoof presentation attempts |
| Bona fide presentation | A genuine, legitimate presentation from a real live user |
| Presentation attack | An attempt to fool the system with a fake presentation such as a photo, replay, mask, or injected stream |
| Passive liveness | Liveness detection without asking the user to perform a challenge |
| Active liveness | Liveness detection that asks the user to do something, such as blink or turn |
| Hybrid liveness | A combination of passive and active checks |
| Threshold | A decision cutoff used to turn a score into pass / retry / fail logic |
| Score fusion | Combining multiple model or signal outputs into one decision layer |
| Retry band / uncertain band | Score range where the system does not fully trust the result and asks for retry or escalation |
| APCER | Attack Presentation Classification Error Rate; how often attack samples are wrongly accepted |
| BPCER | Bona Fide Presentation Classification Error Rate; how often genuine users are wrongly rejected |
| ACER | Average of APCER and BPCER; a summary metric often used in PAD discussions |
| Injection attack | A digital bypass where fake media is inserted into the pipeline instead of being physically shown to the camera |
| Replay attack | Showing a previously recorded image or video of the target person on another screen |
| Challenge-response | An active liveness method that asks the user to perform a live action |
| Manual review | A human review path used when automated confidence is not strong enough |
| Drift | A change over time in input conditions or score behavior that affects production performance |

## Note

Definitions here are simplified for readability. For deeper standards-aligned terminology, see:

- [ISO 30107 notes](../05-standards-compliance/iso-30107.md)
- [NIST notes](../05-standards-compliance/nist.md)
---

## Main-guide links

- [Back to 01. Face Liveness Guide](../01-face-liveness-guide.md)
- [Back to 02. eKYC Integration](../02-ekyc-integration.md)
- [Back to 03. Deployment Guide](../03-deployment-guide.md)

## Read next

Go to [Appendix Attack Taxonomy](A2-attack-taxonomy.md).

# Appendix A4 — Standards and Compliance

## Purpose

This appendix provides a simple orientation to standards and compliance topics relevant to face liveness in eKYC.

The goal here is not to replace legal or certification advice. It is to help teams understand where these topics fit.

---

## Why standards matter

Standards and certifications help teams:

- use shared terminology
- compare vendors more consistently
- understand test scope and limitations
- align internal reviews with recognized frameworks

But a standards-aligned result is **not automatically the same as production security**. Real deployment context still matters.

---

## Common standards and frameworks teams look at

### ISO / PAD terminology
Useful for shared language around presentation attack detection.

### iBeta-style certification context
Often used by vendors as evidence for tested attack coverage in a defined setup.

### NIST-style evaluation context
Useful for understanding benchmark-style performance and comparative evaluation thinking.

### FIDO-related relevance
Can matter when the liveness system is connected to broader digital identity or authentication assurance programs.

---

## Compliance questions teams should ask

- What data is captured and retained?
- How is consent communicated?
- How are model decisions logged?
- What fallback path exists for genuine users?
- How does the system behave for accessibility constraints?
- Is cross-border transfer or retention relevant?
- What evidence exists for fairness and bias testing?

---

## Practical advice

Use standards as:
- a shared language
- a comparison tool
- a review framework

Do **not** use them as the only proof of production readiness.

---

## Related detailed pages in this repo

- [ISO 30107](../05-standards-compliance/iso-30107.md)
- [iBeta](../05-standards-compliance/ibeta.md)
- [NIST](../05-standards-compliance/nist.md)
- [FIDO](../05-standards-compliance/fido.md)
- [Regional regulations](../05-standards-compliance/regional-regulations.md)
- [Bias and fairness](../05-standards-compliance/bias-fairness.md)
- [Legal framework](../09-security-privacy/legal-framework.md)
---

## Main-guide links

- [Back to 01. Face Liveness Guide](../01-face-liveness-guide.md)
- [Back to 02. eKYC Integration](../02-ekyc-integration.md)
- [Back to 03. Deployment Guide](../03-deployment-guide.md)

## Read next

Go to [Appendix Security and Privacy](A5-security-and-privacy.md).

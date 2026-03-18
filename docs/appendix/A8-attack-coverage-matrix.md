# Appendix A8 — Attack Coverage Matrix

## Purpose

This appendix gives a practical matrix for thinking about attack coverage across models, controls, and policy.

It is not a universal truth table. It is a planning tool.

---

## How to use this matrix

For each attack family, ask:

- how common is this in our environment?
- how severe is it if accepted?
- which model or control is strongest against it?
- where is the residual risk?
- what extra mitigation is needed?

---

## Example coverage matrix

| Attack type | Example | Severity | Typical base-model strength | Fusion value | Extra mitigation | Residual risk note |
|-------------|---------|----------|-----------------------------|--------------|------------------|--------------------|
| print attack | photo on paper | medium | usually good for many passive models | low to medium | quality checks, challenge-response | weak print execution may be easy to stop |
| replay attack | video shown on phone | high | mixed, often harder than print | high | active challenge, replay heuristics, web policy | screen quality and brightness matter |
| injection | virtual camera or stream injection | very high | model-only defense often weak | medium | session binding, media-path controls, device signals | strong system control matters more than texture cues |
| deepfake or manipulated media | generated or swapped content | high | depends heavily on model and channel | high | security controls, challenge design, model diversity | fast-moving threat area |
| mask or 3D prop | partial or full mask | medium to high | depends on capture quality and attack realism | medium | challenge-response, depth or motion cues | attack rarity depends on use case |
| low-quality spoof | blurred replay or print | medium | may confuse both quality and liveness stages | medium | separate quality policy from spoof policy | easy to misclassify |

---

## Why severity and frequency both matter

A rare but severe attack may still deserve strong controls.

A common low-skill attack may deserve priority because it drives most field risk.

Both should be considered when choosing what to improve next.

---

## Useful columns to add for your own program

- attack prevalence estimate
- affected channels
- known incident history
- evaluation coverage status
- owner
- next mitigation milestone

---

## Final reminder

Attack coverage should be reviewed again after:

- major model updates
- fusion changes
- expansion to a new channel
- new fraud incidents

---

## Related docs

- [12. Fusion and Meta-Model](../12-fusion-and-meta-model.md)
- [15. Error Analysis](../15-error-analysis.md)
- [17. Security Hardening](../17-security-hardening.md)
- [Appendix A2 — Attack Taxonomy](A2-attack-taxonomy.md)

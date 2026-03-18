# Appendix A5 — Security and Privacy

## Purpose

This appendix summarizes the main security and privacy controls that should surround a face liveness system.

A face liveness model is only one part of the defense. Capture, transport, runtime integrity, storage, and operational response also matter.

---

## Security controls to think about

### Capture integrity
- reduce opportunity for media injection
- bind capture to session context where possible
- validate expected media properties

### Transport security
- encrypt media in transit
- secure API authentication and authorization
- prevent replay where practical

### Runtime hardening
- detect app or browser tampering where relevant
- use secure SDK design
- validate server-side assumptions rather than trusting client claims blindly

### Decision security
- separate score generation from final policy logic
- log policy version and model version
- cap retries and record suspicious patterns

### Operational security
- monitor for attack spikes
- support incident response escalation
- keep rollback and kill-switch options ready

---

## Privacy controls to think about

### Data minimization
Capture and retain only what is needed.

### Retention policy
Define how long media, metadata, and logs are retained.

### Consent and transparency
Users should understand what is being captured and why.

### Access control
Restrict access to media, scores, and logs.

### Auditability
Keep enough traceability for dispute handling, fraud review, and regulated workflows.

---

## Practical warning

A secure model inside an insecure pipeline is not a secure system.

Likewise, a privacy statement without real retention and access control discipline is not enough.

---

## Related detailed pages in this repo

- `docs/09-security-privacy/security-hardening.md`
- `docs/09-security-privacy/anti-fraud.md`
- `docs/09-security-privacy/privacy.md`
- `docs/09-security-privacy/incident-response.md`
- `docs/09-security-privacy/legal-framework.md`
- `docs/06-deployment-operations/error-handling.md`
- `docs/06-deployment-operations/monitoring.md`

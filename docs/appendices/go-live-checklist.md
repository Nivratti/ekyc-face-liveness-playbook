# Appendix E: Production Go-Live Checklist

---

## Security Readiness

- [ ] iBeta Level 1 certification verified (minimum)
- [ ] iBeta Level 2 certification verified (recommended for high-value)
- [ ] Internal PAD testing passed across all target PAI species
- [ ] Deepfake detection module enabled and tested
- [ ] Virtual camera / injection attack defense verified
- [ ] Device attestation (SafetyNet/Play Integrity/DeviceCheck) enabled
- [ ] Red team exercise completed — all findings addressed
- [ ] Adversarial testing performed — model robust
- [ ] Penetration test on API endpoints completed

## Performance Readiness

- [ ] APCER < 1% confirmed across all PAI species
- [ ] BPCER < 5% confirmed on target device mix
- [ ] End-to-end latency P95 < 2 seconds
- [ ] Drop-off rate < 10% in pilot testing
- [ ] Load testing passed at 2x expected peak volume
- [ ] Failover and disaster recovery tested

## Compliance Readiness

- [ ] Data Privacy Impact Assessment (DPIA) completed
- [ ] Biometric data consent flow implemented and tested
- [ ] Data residency requirements verified
- [ ] Audit logging verified — captures all required fields
- [ ] Data retention policies configured per regulation
- [ ] Regulatory documentation prepared (ISO 30107 compliance evidence)

## Operational Readiness

- [ ] Monitoring dashboards live (APCER, BPCER, latency, volume)
- [ ] Alerting configured for anomaly detection
- [ ] Manual review queue configured and staffed
- [ ] Fallback flows tested (liveness failure → alternative verification)
- [ ] Incident response playbook documented and rehearsed
- [ ] Support team trained on liveness-related customer issues
- [ ] Customer-facing FAQ and help documentation published

## Integration Readiness

- [ ] Face matching pipeline verified end-to-end with liveness
- [ ] Session integrity verified (same face used for liveness + matching)
- [ ] Anti-replay protection verified
- [ ] Frame encryption verified
- [ ] Model versioning and rollback capability tested
- [ ] A/B testing infrastructure ready for threshold tuning

## Business Readiness

- [ ] Vendor SLA signed with performance guarantees
- [ ] Escalation paths documented (vendor, internal, regulatory)
- [ ] Customer communication prepared (privacy notice, FAQ)
- [ ] Training completed for all stakeholders
- [ ] Success metrics defined and tracking enabled
- [ ] Post-launch review scheduled (30/60/90 days)

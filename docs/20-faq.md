# 20. FAQ

## Who should read this page

This page is for anyone who wants quick answers to common face liveness questions.

---

## Can face match replace face liveness?

No.

Face match checks identity similarity.
Face liveness checks whether the person is real and present during capture.

A system can match the correct face and still accept a spoof.

---

## Is passive liveness enough?

Sometimes, but not always.

Passive liveness can be strong for lower-friction journeys, but higher-risk flows may need stronger policy, better security controls, active challenge, or multi-signal fusion.

---

## Why can the same real user get different scores on different attempts?

Because score is affected by:

- lighting
- blur
- pose
- device quality
- browser behavior
- network or compression path in some systems

This is why thresholds and retry logic matter.

---

## Why do scores differ across devices?

Different devices have different cameras, frame rates, image pipelines, and performance limits.

That is why evaluation and monitoring should be segmented by platform and device class.

---

## Can a high face-match score make liveness unnecessary?

No.

A replayed video of the correct person can still produce a good face-match score.

---

## Should every low score be treated as spoof?

No.

A low score can come from:

- real spoof
- poor lighting
- blur
- bad framing
- weak browser capture

That is why many systems use pass / retry / fail bands instead of one hard threshold.

---

## When should fusion or a meta-model be added?

Usually after:

- base models are already measured well
- score calibration is understood
- metadata is being stored reliably
- error analysis shows where multi-signal combination can help

Do not add fusion only because it sounds advanced.

---

## What matters more: accuracy or user experience?

Both matter.

A very strict system can reduce fraud but also hurt completion and conversion.
A very lenient system can improve completion but increase attack exposure.

Good product design balances both.

---

## Can deepfakes bypass liveness?

Some can challenge weak systems, especially when media injection or replay controls are poor.

That is why liveness should be treated as a full system problem, not only a model problem.

---

## Do we need different thresholds for different use cases?

Often yes.

Account opening, login step-up, recovery, and transaction approval usually have different risk and friction requirements.

---

## What is more important than one benchmark number?

These are often more useful:

- segment-wise performance
- attack-type performance
- retry and completion rates
- platform stability
- post-release monitoring

---

## What should a first production version focus on?

A strong first version usually focuses on:

- clear scope
- strong top attack coverage
- good quality gating
- simple decision bands
- strong monitoring
- clean rollback path

---

## Related docs

- [01. Face Liveness Guide](01-face-liveness-guide.md)
- [07. Decision Logic](07-decision-logic.md)
- [12. Fusion and Meta-Model](12-fusion-and-meta-model.md)
- [21. Troubleshooting](21-troubleshooting.md)

## Read next

Go to [21. Troubleshooting](21-troubleshooting.md).

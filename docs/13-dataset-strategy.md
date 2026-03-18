# 13. Dataset Strategy

## Who should read this page

This page is mainly for ML engineers, data teams, QA teams, and technical leads planning training, validation, benchmarking, or fusion work.

---

## Why this page exists

Many liveness projects fail because the model is trained on data that does not match the real problem.

A good dataset strategy should answer questions like:

- Which attacks are we trying to stop?
- Which channels and devices do we support?
- How do we avoid train/test leakage?
- What extra data is needed for fusion and calibration?

---

## Start from the problem, not from the data you happen to have

A useful dataset strategy begins with the target deployment:

- onboarding, login, recovery, or transaction approval
- app, web, kiosk, or assisted flow
- passive, active, or hybrid liveness
- expected attack types
- expected device mix

A dataset that is perfect for mobile onboarding may still be weak for browser-based step-up authentication.

---

## Think in layers of data

A strong program often has more than one dataset.

| Dataset layer | Purpose |
|---------------|---------|
| training set | teach the base model or fusion layer |
| validation set | tune thresholds, hyperparameters, and policies |
| test set | final offline performance check |
| challenge set | stress test rare or hard attacks |
| monitoring sample | compare production drift later |

---

## What the core dataset should include

### Live data

Live data should include realistic variation in:

- age groups
- presentation styles
- lighting
- pose
- expression
- camera quality
- capture distance
- background complexity
- browser and app environments

### Spoof data

Spoof data should include the attacks relevant to your threat model, such as:

- print
- replay on screen
- partial replay or cropped replay
- mask or 3D props where relevant
- injection or virtual-camera attacks
- AI-generated or manipulated content where relevant

---

## Diversity matters more than raw count alone

A large dataset with only one clean device setup is weaker than a smaller dataset with realistic diversity.

Important diversity dimensions:

| Dimension | Examples |
|-----------|----------|
| device | low-end Android, flagship Android, iPhone, laptop webcam |
| channel | app, mobile web, desktop web |
| environment | bright indoor, dim indoor, outdoor mixed light |
| attack execution | different screen brightness, print sizes, attack distances |
| operational flow | onboarding, login step-up, recovery |

---

## Split strategy is critical

Leakage can make a weak model look excellent.

### Minimum split rules

- keep people disjoint across train, validation, and test when possible
- keep near-duplicate captures out of multiple splits
- keep attack sessions disjoint where practical
- keep calibration data separate from final test data

### Stronger split patterns

| Split style | Why it matters |
|-------------|----------------|
| person-disjoint | avoids memorizing users |
| device-aware split | checks generalization across devices |
| attack-scenario split | checks generalization to new spoof execution styles |
| time-based split | useful for drift and release simulation |

---

## Fusion dataset needs a tabular view

For a fusion or meta-model, the dataset should not be only image files plus labels.

It should also store the outputs of all upstream systems.

### Example fusion training schema

| Field | Description |
|-------|-------------|
| `sample_id` | capture or request identifier |
| `person_id` | identity grouping field |
| `session_id` | session grouping field |
| `label` | live or spoof |
| `attack_type` | print, replay, injection, deepfake, etc. |
| `flow_type` | onboarding, login, recovery, transaction |
| `platform` | android, ios, web |
| `device_class` | low, mid, high |
| `lighting_bucket` | bright, dim, backlit |
| `model_a_score` | base-model output |
| `model_b_score` | base-model output |
| `quality_score` | capture quality score |
| `blur_score` | blur measure |
| `brightness_score` | brightness measure |
| `challenge_passed` | active-challenge result |

This is the dataset a fusion layer actually learns from.

---

## Suggested data packaging

A practical repo layout often looks like this:

```text
captures/
  images_or_video/
labels/
  sample_labels.csv
metadata/
  capture_metadata.csv
model_outputs/
  passive_scores.parquet
  active_scores.parquet
  quality_scores.parquet
splits/
  train.csv
  val.csv
  test.csv
```

This makes it easier to rebuild experiments and audit mistakes.

---

## Labeling strategy

Useful labels usually include more than just `live` and `spoof`.

### Recommended labels

- final label: `live` / `spoof`
- attack type
- attack family
- capture quality bucket
- failure reason when known
- uncertain / ambiguous flag
- device and channel metadata

More detail is covered in [Appendix A9 — Data Collection and Labeling](appendix/A9-data-collection-and-labeling.md).

---

## Real vs synthetic data

Synthetic data can help, but it should not silently replace realistic evaluation.

| Data type | Good use | Main caution |
|-----------|----------|--------------|
| real live data | realistic capture variation | privacy and collection cost |
| real spoof data | realistic threat measurement | expensive to collect broadly |
| synthetic attack data | stress testing and scale | may not match real attacker behavior |
| synthetic quality degradation | robustness training | easy to overuse unrealistically |

A healthy program usually uses synthetic data to expand coverage, not to avoid collecting real examples.

---

## A practical minimum plan for a new team

If the program is early, a useful first plan is:

1. collect clean live data across target channels
2. collect the top three relevant attack types well
3. capture realistic device and lighting variation
4. enforce person-disjoint splits
5. store per-sample metadata and model outputs from the start

This is more valuable than collecting a huge but messy dataset.

---

## Common mistakes

| Mistake | Why it hurts |
|---------|--------------|
| same person appears in train and test | inflates results |
| only clean indoor data | poor field performance |
| no attack taxonomy | weak analysis later |
| no metadata storage | impossible to segment and debug |
| no uncertainty bucket | noisy labels pollute training |
| no versioned splits | results become hard to reproduce |

---

## Questions to answer before collecting more data

- Which attacks matter most in the next release?
- Which devices or channels are under-covered?
- Are low-quality failures hurting live users more than spoof attacks?
- Is the fusion layer blocked by missing metadata rather than missing images?
- Are we collecting data that helps the real problem, or just easy data?

---

## Final takeaway

A strong liveness dataset strategy is not just about more samples.

It is about:

- the right threat coverage
- the right channel and device coverage
- clean split rules
- useful metadata
- reproducible packaging

That is what turns data into a reliable engineering asset.

---

## Need term help?

If any technical terms on this page feel dense, use [Appendix A1 — Key Terms](appendix/A1-key-terms.md) first and then jump to the relevant appendix page for deeper detail.

---

## Related docs

- [08. Evaluation Playbook](08-evaluation-playbook.md)
- [12. Fusion and Meta-Model](12-fusion-and-meta-model.md)
- [15. Error Analysis](15-error-analysis.md)
- [Appendix A9 — Data Collection and Labeling](appendix/A9-data-collection-and-labeling.md)
- [Appendix A10 — Experiment Design](appendix/A10-experiment-design.md)

## Read next

Go to [14. Score Calibration and Thresholding](14-score-calibration-and-thresholding.md).

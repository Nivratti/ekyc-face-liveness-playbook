# 1.4 Core Terminology & Glossary

---

## Essential Terms

This glossary provides definitions for all key terms used throughout this guide. Terms are organized by category for easy reference.

---

## Biometric & Liveness Terms

| Term | Abbreviation | Definition |
|------|-------------|------------|
| **Presentation Attack** | PA | Any attempt to interfere with a biometric system by presenting an artifact (photo, mask, video, deepfake) to the sensor instead of a genuine live biometric |
| **Presentation Attack Detection** | PAD | The automated process of detecting presentation attacks; synonymous with "liveness detection" and "anti-spoofing" |
| **Presentation Attack Instrument** | PAI | The specific artifact used to carry out an attack — e.g., a printed photo, silicone mask, or deepfake video |
| **PAI Species** | — | A category of attack instrument sharing common characteristics (e.g., "printed photo on A4 paper" is one species; "silicone mask" is another) |
| **Bona Fide Presentation** | — | A genuine, non-attack presentation by a real, live person cooperating normally with the system |
| **Liveness Score** | — | A numerical confidence value (typically 0.0 to 1.0) indicating the probability that a presentation is bona fide (live). Higher = more likely live |
| **Face Anti-Spoofing** | FAS | Alternative term for face presentation attack detection; commonly used in academic literature |
| **Active Liveness** | — | Liveness detection requiring user interaction (head turns, blinks, expressions, speech) in response to system prompts |
| **Passive Liveness** | — | Liveness detection requiring no user interaction; analysis of a single image or short video clip |
| **Hybrid Liveness** | — | Combination of active and passive approaches, typically using passive as primary with active fallback |
| **Challenge-Response** | — | Active liveness paradigm where the system issues a random challenge and verifies the user's response |

---

## Performance Metrics

| Term | Abbreviation | Definition |
|------|-------------|------------|
| **Attack Presentation Classification Error Rate** | APCER | The proportion of **attack presentations** incorrectly classified as bona fide. *Lower is better.* A 0% APCER means no attacks got through. Measured **per PAI species** |
| **Bona Fide Presentation Classification Error Rate** | BPCER | The proportion of **genuine presentations** incorrectly classified as attacks (false rejections). *Lower is better.* A 0% BPCER means no real users were rejected |
| **Average Classification Error Rate** | ACER | Simple average of APCER and BPCER: `ACER = (APCER + BPCER) / 2`. Used as a single summary metric |
| **True Detection Rate** | TDR | Proportion of attacks correctly detected: `TDR = 1 - APCER`. Also called True Positive Rate for attacks |
| **False Rejection Rate** | FRR | Same as BPCER in liveness context — rate at which genuine users are falsely rejected |
| **False Acceptance Rate** | FAR | Same as APCER in liveness context — rate at which attacks are falsely accepted |
| **Equal Error Rate** | EER | The operating point where APCER equals BPCER. Lower EER indicates better overall system performance |
| **Detection Error Tradeoff** | DET | A curve plotting APCER vs BPCER at different thresholds; used to visualize the security-convenience tradeoff |
| **Receiver Operating Characteristic** | ROC | Curve plotting TDR vs APCER (or FAR); shows overall discriminative ability of the system |
| **Area Under Curve** | AUC | Area under the ROC curve; ranges from 0.5 (random) to 1.0 (perfect). Higher is better |
| **Half Total Error Rate** | HTER | Same as ACER; average of FAR and FRR. Common in academic literature |

!!! tip "Key Relationship"
    ```
    APCER + TDR = 1  (for attacks)
    BPCER + Genuine Acceptance Rate = 1  (for genuine users)
    ```
    
    When you tighten the threshold to reduce APCER (block more attacks), BPCER increases (more genuine users rejected). This is the **fundamental security-usability tradeoff**.

---

## Standards & Certifications

| Term | Definition |
|------|------------|
| **ISO/IEC 30107** | International standard series for biometric presentation attack detection. Part 1: Framework. Part 2: Data formats. Part 3: Testing and reporting. Part 4: Mobile profile |
| **ISO/IEC 19795** | Biometric performance testing framework; referenced by 30107-3 for statistical methods |
| **iBeta** | Independent biometric testing laboratory; most widely recognized for PAD conformance testing. Offers Level 1 (2D attacks) and Level 2 (2D + 3D attacks) certifications |
| **NIST FRVT** | NIST Face Recognition Vendor Test — ongoing evaluation of face recognition and PAD technology |
| **NIST FATE** | NIST Face Analysis Technology Evaluation — evaluates face analysis technologies including PAD |
| **FIDO Alliance** | Industry consortium for authentication standards; offers Biometric Component Certification Program |
| **NIST SP 800-63B** | Digital identity guidelines specifying Identity Assurance Levels (IAL) 1-3 with PAD requirements at IAL2+ |
| **Common Criteria** | International framework (ISO/IEC 15408) for IT security evaluation; applicable to biometric systems |

---

## Attack Types

| Term | Definition |
|------|------------|
| **Print Attack** | Presentation of a printed photograph (paper, cardstock, or high-quality photo paper) to the camera |
| **Screen Replay Attack** | Displaying a photo or video on a digital screen (phone, tablet, monitor) and presenting it to the camera |
| **Video Replay Attack** | Subtype of screen replay using pre-recorded video to simulate natural facial motion |
| **2D Mask Attack** | Printed face worn as a mask, often with eye/mouth cutouts for the attacker to see through and simulate blinking |
| **3D Rigid Mask** | Hard mask (resin, plaster, 3D-printed plastic) replicating the target's facial geometry |
| **3D Flexible Mask** | Soft mask (silicone, latex) that conforms to the attacker's face and simulates skin-like properties |
| **Deepfake** | AI-generated or AI-manipulated facial imagery; includes face swaps, face reenactment, lip sync, and full synthesis |
| **Face Swap** | Replacing one person's face with another's in video while maintaining head movements and expressions |
| **Face Reenactment** | Transferring facial expressions from a driving source to a target face identity in real-time |
| **Virtual Camera Injection** | Using software (OBS Virtual Cam, ManyCam) to feed pre-recorded or AI-generated content as a live camera feed |
| **Camera API Hooking** | Low-level interception of camera data using frameworks like Frida or Xposed to inject modified frames |
| **Adversarial Attack** | Specially crafted perturbations (often imperceptible to humans) designed to fool neural network classifiers |
| **Morphing Attack** | Blending two faces into a single face image that matches both identities; used for document fraud |
| **Relay Attack** | Legitimate person's live camera feed is remotely transmitted to another device for KYC at a different location |
| **Synthetic Identity** | A fabricated identity combining real and fictitious information with a GAN-generated or stolen face |

---

## Technical / Architecture Terms

| Term | Definition |
|------|------------|
| **rPPG** | Remote Photoplethysmography — technique to detect blood flow and heart rate from facial video by analyzing subtle color changes in skin |
| **FACS** | Facial Action Coding System — system for classifying facial expressions based on Action Units (AU), each corresponding to specific muscle movements |
| **Action Unit (AU)** | Individual facial muscle movement in FACS (e.g., AU1 = inner brow raise, AU12 = lip corner pull/smile) |
| **Moiré Pattern** | Interference pattern created when two regular patterns (like screen pixel grids) overlap; a strong indicator of screen-based attacks |
| **Halftone Pattern** | Dot pattern used in printing; visible under magnification and in frequency analysis; indicator of print attacks |
| **Subsurface Scattering** | Light transport phenomenon where light penetrates skin, scatters internally, and exits at a different point; unique to live skin |
| **Specular Highlight** | Bright spot of reflected light on a shiny surface; pattern differs between skin, paper, plastic, and screen glass |
| **Depth Map** | Per-pixel distance estimation from the camera; live faces produce characteristic 3D depth profiles |
| **Feature Embedding** | Fixed-length numerical vector representing a face's identity or liveness characteristics in learned feature space |
| **Score Fusion** | Combining multiple scores (passive liveness, active verification, deepfake detection) into a single decision |
| **Domain Generalization** | Training methodology aimed at producing models that perform well on unseen domains (new sensors, environments, attack types) |
| **SDK** | Software Development Kit — packaged library for integrating liveness detection into mobile or web applications |

---

## Regulatory & Compliance Terms

| Term | Definition |
|------|------------|
| **eKYC** | Electronic Know Your Customer — digital identity verification process for customer onboarding |
| **V-CIP** | Video-based Customer Identification Process — RBI-approved method for remote KYC using live video interaction |
| **CDD** | Customer Due Diligence — process of verifying customer identity and assessing risk; required by AML regulations |
| **EDD** | Enhanced Due Diligence — additional scrutiny for higher-risk customers (PEPs, high-value transactions, etc.) |
| **AML** | Anti-Money Laundering — regulations and processes to prevent money laundering through financial systems |
| **KYC** | Know Your Customer — the broader process of identifying and verifying customers' identities |
| **PEP** | Politically Exposed Person — individual holding prominent public position; subject to enhanced scrutiny |
| **STP** | Straight-Through Processing — fully automated processing without human intervention |
| **DPDPA** | Digital Personal Data Protection Act (India, 2023) — governs personal data processing including biometrics |
| **GDPR** | General Data Protection Regulation (EU) — classifies biometric data as special category requiring explicit consent |
| **BSA** | Bank Secrecy Act (US) — requires financial institutions to assist government agencies in detecting/preventing money laundering |
| **PSD2 SCA** | Payment Services Directive 2, Strong Customer Authentication — EU requirement for multi-factor authentication in payments |

---

## Acronym Quick Reference

| Acronym | Full Form |
|---------|-----------|
| APCER | Attack Presentation Classification Error Rate |
| BPCER | Bona Fide Presentation Classification Error Rate |
| ACER | Average Classification Error Rate |
| PAD | Presentation Attack Detection |
| PAI | Presentation Attack Instrument |
| rPPG | Remote Photoplethysmography |
| FACS | Facial Action Coding System |
| NIR | Near Infrared |
| ToF | Time of Flight |
| DG | Domain Generalization |
| GAN | Generative Adversarial Network |
| NeRF | Neural Radiance Field |
| ONNX | Open Neural Network Exchange |
| TFLite | TensorFlow Lite |
| FPS | Frames Per Second |
| DXA | Device Cross-Attestation |
| MRZ | Machine Readable Zone |
| NFC | Near Field Communication |
| OTP | One-Time Password |
| MFA | Multi-Factor Authentication |

---

*Next: [Part II — Active Liveness Detection →](../02-fundamentals/active-liveness.md)*

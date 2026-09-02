# MITRE SAFE-AI

**Tier:** 1 — Institutional or vendor-backed; citable in official work
**Catalog link:** atlas.mitre.org/pdf-files/SAFEAI_Full_Report.pdf
**Companion source:** [`mitre-atlas.md`](./mitre-atlas.md) — the ATLAS taxonomy this report maps onto NIST controls
**Date pulled:** 2026-09-02
**Note:** PDF was not directly downloadable from this environment (atlas.mitre.org not reachable); content below extracted via automated fetch/analysis of the PDF.

## What it contributes to this library

Maps AI/ATLAS threat techniques directly onto ~100 NIST SP 800-53 Rev 5 controls; includes assessor interview Q&A sets for planning Security Control Assessments. MITRE (FFRDC) work product, not a vendor.

## Bibliographic

- **Title:** SAFE-AI: A Framework for Securing AI-Enabled Systems
- **Sponsoring organization:** The MITRE Corporation
- **Authors:** J. Kressel, R. Perrella, E. Reed, N. Naik, J. Sidhu, Q. Hu, L. Booker, J. Cintron, L. Huffner
- **Publication:** April 2025 — MITRE Work Product MP250397

## Purpose and scope

Addresses a gap the document states directly: "NIST has yet to publish guidance for securing AI systems." SAFE-AI selects appropriate security controls for AI-enabled systems by identifying threats unique to AI technologies. Scope: "adversarial threats, concerns, security controls, and guidance associated with secure use of AI-enabled systems," covering LLMs, generative AI, and conventional ML. **Explicitly out of scope:** non-security topics like fairness, equity, and explainability.

## Four-element system decomposition

| Element | Covers |
|---|---|
| Environment | Infrastructure and network elements |
| AI Platform | Application software and operating systems |
| AI Model | Algorithms processing inputs to generate outputs |
| AI Data | Training and tuning datasets |

## Frameworks integrated

1. **MITRE ATLAS™** — adversarial tactics and techniques specific to AI (see [`mitre-atlas.md`](./mitre-atlas.md)).
2. **NIST SP 800-53 Rev 5** — baseline security controls.
3. **NIST RMF** — risk management structure across organizational levels.

## Structural coverage

- **~100 NIST controls** identified as potentially affected by AI-specific concerns.
- **35+ distinct AI threats** cataloged, including: model poisoning and loss; data poisoning and unauthorized access; supply-chain vulnerabilities; prompt injection attacks; identity spoofing via deepfakes; cost harvesting through denial-of-service.
- **Appendix A** demonstrates ATLAS-framework alignment — how each concern/threat is addressed by security controls across the four system elements, showing which techniques intersect with which control recommendations.

## Example mappings

**Loss of Models threat:** model-destruction concerns map to `AC-03-00` (Access Enforcement), `AC-06-00` (Least Privilege), and `CM-07-00` (Least Functionality) — different controls apply depending on whether the threat targets environment, platform, models, or data.

**Data Poisoning threat:** maps to `SC-07-00` (Boundary Protection), `SC-08-00` (Transmission Confidentiality), and `SI-04-00` (System Monitoring); residual risk acknowledged where validation baselines prove incomplete.

**Supply Chain Infiltration:** emphasizes SR-series controls (Supply Chain Risk Management), specifically SBOMs and model cards as mitigation mechanisms.

## Assessor interview Q&A sets (Appendix E)

Structured Q&A pairs enabling assessors to evaluate control implementation: question templates per system element, expected-answer frameworks describing what organizations should document, and parameterized placeholders (`[XYZ]`) for agency-specific detail. Organized by control ID and system element so assessors can customize per their own architecture.

Example (control `AC-03-00`, AI Platform context): *"How is access approved to the LLM chat to mitigate direct prompt injections?"* — expected responses identify specific approval mechanisms and mitigation methods.

## Integration with NIST RMF phases

- **Prepare:** identify AI subject-matter experts, reassess risk tolerance.
- **Select:** tailor controls for identified AI threats, document planned implementations.
- **Assess:** augment Security Assessment Plans with AI-specific evaluation criteria.

## Residual risk transparency

A distinctive feature: for each threat, the framework explicitly documents what its mitigations do *not* cover — e.g. a recurring note that "risks from insider threats are not addressed by mitigations focused on access control," directing practitioners toward supplemental personnel-focused controls rather than implying access control alone is sufficient.

## Practical framing

Grounds guidance in existing NIST frameworks rather than proposing novel standards, minimizing disruption to established assessment processes — organizations can fold AI-specific concerns into existing security-authorization packages. Explicitly recognizes AI's non-deterministic nature requires different assessment approaches than traditional systems, particularly regarding "hidden vulnerabilities or malicious code" in third-party models and frameworks.

---
*Extracted via automated fetch/analysis of the PDF (atlas.mitre.org/pdf-files/SAFEAI_Full_Report.pdf); the file itself could not be downloaded directly in this environment (domain not reachable), so no local PDF copy is archived here.*

# MITRE ATLAS

**Tier:** 1 — Institutional or vendor-backed; citable in official work
**Catalog link:** atlas.mitre.org
**Companion source:** [`mitre-safe-ai.md`](./mitre-safe-ai.md) — SAFE-AI maps ATLAS techniques onto NIST SP 800-53 Rev 5 controls
**Date pulled:** 2026-09-02
**Sources used:** MITRE ATLAS Fact Sheet (atlas.mitre.org/pdf-files/MITRE_ATLAS_Fact_Sheet.pdf), the `mitre-atlas/atlas-data` GitHub repo (structured data), and web search corroborating the Center for Threat-Informed Defense partnership.

## What it contributes to this library

Adversarial threat-tactic/technique knowledge base for AI systems; the taxonomy SAFE-AI maps onto. Ongoing "Secure AI" partnership with the Center for Threat-Informed Defense for incident sharing.

## What it is

"A globally accessible, living knowledge base of adversary tactics and techniques based on real-world attack observations," focused specifically on AI systems. Used to inform security professionals about realistic threats, enable threat assessments and red-team exercises, clarify adversarial behaviors and defenses, and document actual attacks on AI infrastructure. Developed and maintained by MITRE through public-private partnerships (e.g. Microsoft is listed as an "ATLAS and Arsenal Collaborator").

**Relationship to MITRE ATT&CK:** "ATLAS is modeled after the MITRE ATT&CK® framework and its tactics, techniques, and procedures (TTPs) are complementary to those in ATT&CK." Each ATLAS tactic links to a corresponding ATT&CK tactic reference (e.g. `AML.TA0002 Reconnaissance` → ATT&CK `TA0043`).

## Structure (per the `atlas-data` repository, content version 2026.08, format v6.0.0)

Top-level data shape: `collection` → `matrix` → `tactics` → `techniques` → `mitigations` → `case-studies` → `relationships`.

At the pulled version: **16 tactics**, **197 techniques** (including sub-techniques), **72 case studies**, and a full relationship graph linking techniques to the tactics they achieve and the mitigations that address them.

## The 16 ATLAS tactics (in `AML.TA` ID order)

| ID | Tactic |
|---|---|
| AML.TA0000 | AI Model Access |
| AML.TA0001 | AI Attack Adaptation |
| AML.TA0002 | Reconnaissance |
| AML.TA0003 | Resource Development |
| AML.TA0004 | Initial Access |
| AML.TA0005 | Execution |
| AML.TA0006 | Persistence |
| AML.TA0007 | Defense Evasion |
| AML.TA0008 | Discovery |
| AML.TA0009 | Collection |
| AML.TA0010 | Exfiltration |
| AML.TA0011 | Impact |
| AML.TA0012 | Privilege Escalation |
| AML.TA0013 | Credential Access |
| AML.TA0014 | Command and Control |
| AML.TA0015 | Lateral Movement |

Example tactic description (AI Model Access, `AML.TA0000`): the adversary is trying to gain some level of access to an AI model, ranging from full internal knowledge to physical access to the environment where training/inference data is collected — access may be direct (system housing the model), via a public API, or indirect (through a product/service that uses AI internally).

Example (AI Attack Adaptation, `AML.TA0001`, added in a more recent version than the original ATT&CK-mirrored set): adversaries transform reusable capabilities, general attack methods, target knowledge, and objectives into attack-ready, target-specific outputs — proxy/manipulated models, adversarial data, crafted prompts/retrieval content, deepfakes, malicious generated code, or **agent tasking, high-level objectives, action sequences, and tool instructions for an autonomous agent**. This tactic is explicitly agent-relevant.

## Incident documentation

Case studies document real-world attacks with measured impact — one cited example: a $77M loss via an adversarial attack on a facial recognition system (per the ATLAS Fact Sheet).

## "Secure AI" partnership (Center for Threat-Informed Defense)

MITRE's Center for Threat-Informed Defense (CTID) runs a "Secure AI" project, launched via an October 2024 press release ("MITRE Launches AI Incident Sharing Initiative") as a structured mechanism for organizations to share AI-related security incidents, feeding real-world observations back into frameworks like ATLAS. Project page: `ctid.mitre.org/projects/secure-ai`. *(This partnership was not directly documented inside the ATLAS Fact Sheet PDF pulled for this entry — confirmed via a separate web search against MITRE's own press release and the CTID project page; not independently re-verified in full here.)*

## Data access

- Structured YAML/data distribution: `github.com/mitre-atlas/atlas-data` (`dist/ATLAS-latest.yaml` always points to the latest content in the latest format; also available as STIX, Navigator layers, and Excel via repo tooling).
- Versioning: content version follows `YYYY.MM.N` (e.g. `2026.08`); format version follows semantic versioning (e.g. `6.0.0`), tracked separately as of the 2026.05 / 6.0.0 release.

---
*Extracted via automated fetch of the ATLAS Fact Sheet PDF and direct read of the `mitre-atlas/atlas-data` GitHub repository's structured YAML and README (both reachable directly; `atlas.mitre.org`'s own site is a JS single-page app not reachable via automated fetch from this environment). The Secure AI/CTID partnership claim was corroborated via web search, not pulled from a single primary document.*

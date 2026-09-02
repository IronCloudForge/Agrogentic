> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# ASR-022: Any agentic AI system, built internally or procured, must be evaluable against a standard set of governance questions before authorization

**Status:** Draft
**Date:** 2026-09-02
**Driver:** [Family: CROSS-CUTTING] NIST SP 800-53 Rev 5 (CA-2 control assessments, generalized to pre-authorization evaluation regardless of system origin); FedRAMP/OSCAL discipline of standardized, machine-checkable control assessment

## Requirement statement
Any agentic AI system — whether built internally or procured from a vendor — must be evaluable against a standard, consistent set of governance questions before it is authorized for use. The evaluation criteria must not differ based on whether the system was built or bought.

## Architectural significance
Without a standard evaluation set applied uniformly, an internally built system and a procured system can end up held to different bars — typically with the procured system receiving less scrutiny precisely because its internals are not directly visible to the evaluator, which is exactly the case where independent evaluation against explicit, external criteria matters most.

## Corpus evidence
An AI controls matrix built by a cloud-security industry body defines 243 vendor-agnostic control objectives across 18 domains specifically so that systems can be assessed by the same criteria regardless of vendor origin (CSA AI Controls Matrix; cloudsecurityalliance.org). A separate open-source governance toolkit operationalizes this kind of standard evaluation as a repeatable tool — a CLI command that checks a deployed agent system against a named threat-taxonomy's coverage and can fail a CI pipeline on weak evidence, applied the same way regardless of whether the system under evaluation was built in-house (Microsoft Agent Governance Toolkit; github.com/microsoft/agent-governance-toolkit).

## Related ADRs
None yet — open requirement. (ADR-018, adoption of a specific evaluation checklist, is deliberately not drafted in this pass — see `ASR-ADR-Outline-Catalog.md`.)

> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# ASR-020: An agent must not be granted higher-order reasoning or action authority until the foundational layer it depends on has independently validated accuracy

**Status:** Draft
**Date:** 2026-09-02
**Driver:** [Family: AI, CROSS-CUTTING] NIST SP 800-53 Rev 5 (SA-11 developer testing and evaluation, generalized to layered agentic architecture); NIST AI RMF (Measure function, applied per architectural layer)

## Requirement statement
A capability that depends on a lower architectural layer — the underlying model, an identity/credentialing layer, a guardrail/policy-enforcement layer, or an audit layer — must not be granted higher-order reasoning or action authority until that lower layer's accuracy or integrity has been independently validated. Validating the higher-order capability alone, without validating what it depends on, does not satisfy this requirement.

## Architectural significance
Layered agentic architectures compound risk upward: a capability that reasons or acts on top of an unvalidated foundation inherits that foundation's errors without ever having had the opportunity to catch them at the source. Validating only the highest, most visible layer creates the appearance of rigor while leaving the layers underneath — which every higher-order decision actually depends on — unverified. Without an explicit requirement that validation happen at each dependency layer, an architecture's actual reliability is only as strong as its least-validated layer, regardless of how much scrutiny its top layer received.

## Corpus evidence
An open-source agent-governance toolkit structures its own release process around exactly this layering principle: each major architectural component — identity and trust, execution control, audit and compliance, and others — has its own formal specification and its own dedicated conformance-test suite (992 tests in total across 10 specifications), so that a component is only relied upon by the rest of the system once it has independently passed its own layer's validation (Microsoft Agent Governance Toolkit; github.com/microsoft/agent-governance-toolkit).

## Related ADRs
ADR-016 (staged-validation gate model for autonomy grants) addresses this requirement directly.

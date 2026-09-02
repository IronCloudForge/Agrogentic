> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# ASR-003: Agentic AI policy must specify architecture explicitly enough that written-policy compliance and architectural compliance cannot diverge

**Status:** Draft
**Date:** 2026-08-31
**Driver:** [Family: CROSS-CUTTING] NIST SP 800-207 (Zero Trust Architecture); general Zero Trust architectural-intent principles

## Requirement statement
Agentic AI policy must specify architectural requirements — identity separation, scoped credentials, audit-log immutability, data-store and inference-location placement — explicitly enough that a system can be verified against the architecture itself, not only against the literal text of the policy. Written-policy compliance and architectural compliance must not be permitted to diverge.

## Architectural significance
A system can satisfy the literal text of a policy while violating the architectural intent that policy was written to enforce, whenever the policy does not specify the underlying architecture explicitly enough to close that gap. This divergence is not detectable by a policy-text compliance review alone — it requires an independent architectural assessment against the policy's intent, not just its wording. For an agentic system capable of autonomous action, this gap is materially more consequential than for a human-mediated system, because there is no human decision point where the divergence would naturally surface before an action is taken.

## Corpus evidence
An open-source agent governance toolkit states this exact principle as its core design rationale — that prompt-level or policy-text-level instruction to a model is "not a control surface," citing a published adaptive-attack study reporting a 100% policy-violation success rate against multiple current frontier models under adversarial input (Andriushchenko et al., ICLR 2025, evaluated on JailbreakBench). Its architectural response is to enforce every tool call in deterministic application code before the model's output reaches execution, so a denied action is structurally impossible rather than merely discouraged — a concrete illustration of closing the written-policy-versus-architecture gap this requirement addresses (Microsoft Agent Governance Toolkit; github.com/microsoft/agent-governance-toolkit).

## Related ADRs
None yet — open requirement.

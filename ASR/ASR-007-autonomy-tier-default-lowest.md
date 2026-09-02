> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# ASR-007: A capability's autonomy tier must default to the lowest tier until explicitly raised

**Status:** Draft
**Date:** 2026-09-02
**Driver:** [Family: CROSS-CUTTING] NIST SP 800-207 (Zero Trust — default-deny, "never trust, always verify"); NIST SP 800-53 Rev 5 least-privilege principle (AC-6, generalized to autonomy-tier assignment)

## Requirement statement
Every agentic capability must be provisioned at Tier 1 (Advisory only, per ADR-001) by default. A capability may operate at a higher autonomy tier only after that tier has been explicitly and affirmatively granted through the process defined in ADR-002. The absence of a recorded, explicit grant must never be interpreted as authorization to act at a higher tier, regardless of how the capability was deployed or how it behaves in practice.

## Architectural significance
A default-allow posture at the autonomy layer reproduces, one layer up, the exact failure mode Zero Trust architecture was built to eliminate at the network and identity layers: an unconfigured, ambiguous, or lost case resolving toward more access rather than less. Without a default-lowest requirement, a capability introduced without a documented tier determination — or one whose tier record is lost, contested, or ambiguous during a later review — has no architecturally safe fallback. In that absence, whatever the capability's deployment context happens to permit, rather than a deliberate governance decision, ends up determining how much unsupervised authority it holds.

## Corpus evidence
An independent agent-governance specification's maturity model implements this default directly: every agent enters at its lowest maturity level ("Intern" — observe and report only, under continuous oversight) and autonomy is earned upward against explicit promotion gates rather than assumed; a critical incident triggers immediate demotion back to that same lowest level as the safe fallback state (Agentic Trust Framework v0.9.1; github.com/massivescale-ai/agentic-trust-framework).

## Related ADRs
ADR-002 (autonomy tier promotion and demotion process) defines the explicit-grant mechanism this requirement depends on.

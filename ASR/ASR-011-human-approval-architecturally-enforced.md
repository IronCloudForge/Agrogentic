> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# ASR-011: A human-approval checkpoint must be architecturally enforced by the orchestrator, not left to the underlying model's judgment

**Status:** Draft
**Date:** 2026-09-02
**Driver:** [Family: CROSS-CUTTING] NIST SP 800-53 Rev 5 (CM-3/AC-3 enforced access control at the system boundary, generalized); general Zero Trust architectural-intent principle — a policy decision must not be delegated to the resource being governed

## Requirement statement
Where a capability's tier requires human approval before an action executes (Tier 2, per ADR-001), that gate must be enforced by the orchestrator as a structural precondition to execution — never implemented as an instruction to the underlying model to ask permission first, and never satisfiable by the model choosing to proceed on its own judgment that approval is unnecessary.

## Architectural significance
A model instructed to "ask before acting" is a request made to a stochastic system, not an enforced control — the same distinction ASR-003 draws between written-policy and architectural compliance generally, applied here specifically to the approval gate. Without architectural enforcement, a capability's actual behavior at the approval boundary depends on the model correctly following an instruction under whatever conditions it encounters, rather than on a control the model cannot bypass regardless of its own reasoning.

## Corpus evidence
An open-source agent-governance toolkit's core design stance rejects prompt-level safety as a control surface entirely — citing published adversarial research showing a 100% attack success rate against instructed safety behavior across multiple production model families — and instead intercepts every tool call in deterministic application code before a model's intent reaches execution, making a denied or gated action "structurally impossible" rather than merely discouraged (Microsoft Agent Governance Toolkit, citing Andriushchenko et al., ICLR 2025; github.com/microsoft/agent-governance-toolkit). Separately, production deployment findings describe "approval fatigue" and unsandboxed "YOLO mode" as the practical failure mode when an approval step exists but is not structurally enforced — users approving 50 or more actions per session without meaningful review, characterized by the deploying team as producing no real human oversight in practice (Uber ADR, MLSys 2026 Industry Track slides; mlsys.org/media/mlsys-2026/Slides/3853_k9cXWDE.pdf).

## Related ADRs
ADR-007 (human-approval gate design for Tier 2 capabilities) addresses this requirement directly.

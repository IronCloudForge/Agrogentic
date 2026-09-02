> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# ASR-001: Governance model must support accelerated AI adoption without loss of risk management

**Status:** Draft
**Date:** 2026-08-31
**Driver:** [Family: AI] OMB M-25-21 ("Accelerating Federal Use of AI through Innovation, Governance, and Public Trust"); EO 14179

## Requirement statement
Agentic AI governance must enable calibrated, per-capability autonomy decisions rather than a single, uniform, department-wide risk posture, so that adoption can proceed at the pace current federal AI policy requires while risk management remains measurable, defensible, and visible to oversight.

## Architectural significance
A governance model built around one uniform posture — cautious or permissive, applied identically across every system — cannot satisfy a policy direction that calls for both faster adoption and continued public trust at the same time. Setting a single department-wide dial toward "permissive" reads as an abandonment of risk management; leaving it at "cautious" fails to reflect the adoption mandate at all. Without a mechanism that varies autonomy by capability and by measured accuracy, any governance model will be structurally out of step with its own policy driver in one direction or the other.

## Corpus evidence
A production enterprise deployment of agentic AI detection and response tooling documented growth from roughly 10,000 to over 200,000 agent sessions per day within about a year, illustrating that adoption at this pace is already occurring in comparable enterprise environments and that a governance model calibrated to a slower adoption curve will fall behind the actual rate of use (Uber ADR, MLSys 2026 Industry Track; github.com/uber/ADR; arXiv:2605.17380). A separately published open-source agent governance toolkit implements calibrated, per-action policy enforcement — distinct privilege tiers, deterministic allow/deny/require-approval rules evaluated per tool call — as a working reference pattern for exactly this kind of graduated autonomy, rather than a single uniform posture (Microsoft Agent Governance Toolkit; github.com/microsoft/agent-governance-toolkit).

## Related ADRs
ADR-001

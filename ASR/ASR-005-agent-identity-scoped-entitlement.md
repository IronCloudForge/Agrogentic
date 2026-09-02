> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# ASR-005: Agent identity must be its own scoped entity, never inherited from an invoking user, service account, or integrated system

**Status:** Draft
**Date:** 2026-08-31
**Driver:** [Family: CROSS-CUTTING] NIST SP 800-207 (Zero Trust); AC-17 boundary-consistency principle (generalized)

## Requirement statement
Every agent must be provisioned its own identity and entitlement set, scoped to the minimum required for its task. An agent must never inherit the full privilege set of its invoking user, its service account, or any system it integrates with.

## Architectural significance
When agent identity is not treated as its own first-class entity, an agent operating across multiple systems inherits the union of whatever entitlement ambiguity exists across every system it touches — reproducing the least well-governed access boundary among them, at the agent layer, and at whatever speed the agent operates. Controls satisfied within one system's authorization boundary cannot be assumed to satisfy an equivalent requirement in a different boundary the same agent also operates within. Without an explicit, scoped, agent-level entitlement model, "agent sharing" across systems or mission areas defaults to broad inheritance rather than a deliberate, minimum-necessary grant.

## Corpus evidence
A production enterprise agentic-security system's own benchmark results show Permission Abuse as its weakest-detected threat tactic — one of five tactics, detected at roughly 20% versus 56-100% for other tactics — indicating that entitlement-boundary failures are difficult to catch even with dedicated detection tooling once they occur, and are therefore a stronger case for prevention through scoped provisioning than for reliance on detection alone (Uber ADR, MLSys 2026 Industry Track; arXiv:2605.17380). An open-source agent governance toolkit implements this requirement as a working reference pattern, issuing each agent its own identity credential (via SPIFFE/DID-based identity, distinct from any invoking user or service account) as a first-class part of its architecture rather than an added control (Microsoft Agent Governance Toolkit; github.com/microsoft/agent-governance-toolkit). A published security taxonomy for agent-executable "skills" separately documents over 280 real-world instances of API-key and PII exposure attributed specifically to over-privileged, non-scoped skill permissions (Snyk, Feb 2026; cited in OWASP Agentic Skills Top 10, risk AST03, github.com/OWASP/www-project-agentic-skills-top-10).

## Related ADRs
None yet — open requirement.

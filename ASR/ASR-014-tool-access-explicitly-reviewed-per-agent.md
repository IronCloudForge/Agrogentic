> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# ASR-014: Tool and capability access must be explicitly reviewed and approved per agent, not inherited from accumulated user or team access

**Status:** Draft
**Date:** 2026-09-02
**Driver:** [Family: CROSS-CUTTING] NIST SP 800-53 Rev 5 (AC-6 least privilege; AC-2 account management, generalized to agent tool/capability grants)

## Requirement statement
An agent's access to a specific tool or capability must be explicitly reviewed and granted for that agent. It must never be inherited automatically from the accumulated tool or capability access of the user, team, or service account associated with the agent.

## Architectural significance
A user's or team's accumulated access typically reflects years of accreted, rarely-audited permissions built for human-paced work — far broader than any single agent task requires. Without an explicit per-agent review, an agent's actual access surface defaults to that accumulated breadth rather than to what its task needs, reproducing at the tool layer the same inheritance failure ASR-005 addresses at the identity layer.

## Corpus evidence
An open-source agent-governance toolkit frames tool-level access as its own governance question distinct from broader identity or account access, noting that "OAuth scopes/IAM roles control which services an agent can reach, not what it does once connected" — the toolkit's core justification for treating tool/capability grants as a separate, explicitly reviewed layer rather than something inherited from a connection-level credential (Microsoft Agent Governance Toolkit; github.com/microsoft/agent-governance-toolkit).

## Related ADRs
ADR-010 (tool and capability registry and approval workflow) addresses this requirement directly.

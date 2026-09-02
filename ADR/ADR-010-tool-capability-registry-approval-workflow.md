> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# ADR-010: Tool and capability registry and approval workflow

**Status:** Draft
**Date:** 2026-09-02
**Traces to:** ASR-014

## Context
ASR-014 requires that an agent's tool and capability access be explicitly reviewed and granted per agent, never inherited from a user's or team's accumulated access. This decision defines the registry and workflow mechanism that satisfies it.

## Decision
| Stage | Requirement |
|---|---|
| Registration | Every tool or capability an agent may call is registered in a central registry before any agent can be granted access to it — no direct, unregistered tool access. |
| Per-agent grant | Access to a registered tool is granted per agent, explicitly, as a discrete decision — never inherited from a user's or team's broader access. |
| Periodic review | Grants are reviewed on a defined cadence rather than left standing indefinitely once issued. |
| Drift/poisoning detection | The registry is monitored for tool poisoning, typosquatting, and drift from a tool's registered definition; a registered tool that silently changes behavior is treated as requiring re-review before continued use. |

## Corpus reference
An open-source agent-governance toolkit ships this pattern as working infrastructure: its Agent Marketplace component handles plugin governance and trust scoring, and its MCP Security Gateway performs tool-poisoning detection, drift monitoring, typosquatting detection, and hidden-instruction scanning against registered tools (Microsoft Agent Governance Toolkit; github.com/microsoft/agent-governance-toolkit). Cited as precedent that a registry-plus-monitoring pattern of this kind is buildable, not as authority for the specific review cadence adopted here.

## Consequences
- Gives ASR-014 an enforceable mechanism.
- Does not itself set the review cadence or name who is authorized to grant or review access — an organizational-ownership question deferred to ADR-015 (backlog, currently undrafted).
- A capability that calls an unregistered tool, or one granted through inherited rather than explicit access, does not satisfy ASR-014 regardless of how the tool itself behaves.

## Amendment log
- 2026-09-02 — Initial version.

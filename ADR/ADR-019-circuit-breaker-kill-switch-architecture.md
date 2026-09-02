> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# ADR-019: Circuit-breaker and kill-switch architecture for autonomous workflows

**Status:** Draft
**Date:** 2026-09-02
**Traces to:** ASR-013, ASR-023

## Context
ASR-013 requires that a break in the chain of custody halt autonomous action. ASR-023 requires a deprecated or invalidated architecture to be quarantined rather than deleted. Both presuppose a mechanism that can actually stop an autonomous workflow immediately and isolate its state, rather than deprecation being enforced only through future code changes and redeployment. This decision defines that mechanism.

## Decision
- Every autonomous workflow at Tier 3 or above (per ADR-001) is wired to a circuit-breaker that can halt it immediately, independent of the orchestrator's normal control flow — a kill switch that functions even if the orchestrator's own policy-enforcement logic is itself the thing malfunctioning.
- The circuit-breaker is triggered automatically by: a chain-of-custody break (ASR-013), a demotion event (ADR-002 Step 5), or a manual trigger by an authorized human.
- On trigger, the affected capability's in-flight actions are halted, its tier reverts to Tier 1 (per ADR-002), and its configuration and state at the moment of triggering are quarantined (per ASR-023) rather than discarded.
- The circuit-breaker itself is tested on a defined cadence, per ASR-010's adversarial-testing requirement, rather than assumed functional because it has not yet been needed.

## Corpus reference
An open-source agent-governance toolkit ships this exact mechanism as a named, working component — its Agent SRE package provides "kill switch, SLO monitoring, chaos testing" as a first-class part of its architecture, explicitly designed to be exercised via chaos engineering rather than trusted untested (Microsoft Agent Governance Toolkit; github.com/microsoft/agent-governance-toolkit).

## Consequences
- Gives ASR-013's halt requirement and ASR-023's quarantine requirement a concrete, shared mechanism rather than two separately implemented behaviors.
- Does not itself define automatic triggers beyond the three listed — a future ADR may add triggers as new failure classes are identified.
- Depends on ADR-002's tier model and ASR-023's quarantine requirement both already being in place.

## Amendment log
- 2026-09-02 — Initial version. Absorbs the outline catalog's ADR-003 ("Kill-switch / interrupt authority at defined checkpoints in an agent's action chain," Section 1) — the same architectural decision, drafted here from the incident-response angle rather than as a separate document. `ASR-ADR-Outline-Catalog.md` marks ADR-003 accordingly rather than leaving it Proposed.

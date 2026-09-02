> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# ADR-002: Autonomy tier promotion and demotion process

**Status:** Draft
**Date:** 2026-09-02
**Traces to:** ASR-006, ASR-007

## Context
ADR-001 established a four-tier autonomy model assigned per capability, and set the general rule that a tier "may only be raised, not assumed by default," with promotion requiring independently measured accuracy. It did not define the mechanics of that process. ASR-006 requires promotion to rest on measured accuracy rather than elapsed time or plausible-looking output; ASR-007 requires every capability to default to Tier 1 until a promotion is explicitly and affirmatively granted. Neither requirement is enforceable without a defined process for how a measurement is taken, who takes it, what triggers a demotion, and how a grant or a demotion is recorded. This ADR defines that process.

## Decision
Tier promotion and demotion for any agentic capability follows the sequence below. No step may be skipped, and no capability may hold a tier above Tier 1 without having completed it.

| Step | Requirement |
|---|---|
| 1. Baseline measurement | Accuracy is measured against a human-reviewed sample drawn from the capability's actual production-representative input distribution — not a curated evaluation set alone, and not the capability's own self-reported confidence (see ASR-021, backlog). |
| 2. Threshold set in advance | The accuracy threshold required for the target tier is documented before the measurement is taken, never selected after seeing the result. |
| 3. Independent measurement | The measurement is performed or verified by someone other than the capability's own developer or owner. |
| 4. Explicit, dated grant | The promotion takes effect only when recorded as an explicit, dated decision — an amendment to this ADR's log, or a successor decision record it points to. A grant is never inferred from elapsed time at the current tier, from silence, or from an absent objection. |
| 5. Demotion trigger | Any of the following returns a capability immediately to Tier 1, pending re-review, regardless of how long it has held its current tier: a measured accuracy regression below the threshold set for its tier; failure of the control required for its tier under ADR-001; or a disclosed incident within the capability's operating scope. |
| 6. Re-promotion | A demoted capability re-enters at Step 1. Its prior measurement history does not by itself justify skipping the baseline-measurement step on re-review. |

Absent a completed Step 4 grant on record, a capability's tier is Tier 1 — this is the operational mechanism that satisfies ASR-007's default-lowest requirement, not a separate control.

## Corpus reference
An independent agent-governance specification's maturity model implements a structurally comparable pattern already in production use elsewhere: agents are promoted against documented gates and demoted immediately — to the lowest maturity level — on a critical incident, independent of how long the higher level had been held (Agentic Trust Framework v0.9.1; github.com/massivescale-ai/agentic-trust-framework). Cited as precedent that a measured-promotion / immediate-demotion process of this shape is buildable and already adopted elsewhere, not as authority for this decision. A separate open-source governance toolkit ships working infrastructure — SLO monitoring, circuit breakers, and a kill-switch component — that a Step 5 demotion trigger could plausibly be wired into, as illustrative precedent that the enforcement mechanics this process assumes already exist as a reference implementation (Microsoft Agent Governance Toolkit, Agent SRE package; github.com/microsoft/agent-governance-toolkit).

## Consequences
- This ADR is what makes ASR-006 and ASR-007 operational; a future ASR/ADR governing a specific capability's tier should invoke this process rather than define a new one.
- This ADR does not itself set the numeric accuracy threshold for any tier, nor does it name the role or body authorized to perform Step 3's independent measurement or Step 4's grant — organizational ownership placement is deferred to the policy-coordination section of the backlog (ADR-015).
- This ADR does not itself define the audit-trail schema that Step 4 and Step 5 decisions must be recorded in to remain independently inspectable — that is deferred to ADR-008 (backlog), which this decision presumes will exist.
- A capability that has never completed Step 1 through Step 4 has no valid path to any tier above Tier 1, including through informal or undocumented practice.

## Amendment log
- 2026-09-02 — Initial version.
- 2026-09-02 — Status corrected from Accepted to Draft. No Layer 1 authorizing instrument has signed off on this decision yet; "Accepted" in the Status field is reserved for that, per Layer-Model.md's directionality. No change to the decision itself.

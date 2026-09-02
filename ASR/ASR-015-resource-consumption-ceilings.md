> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# ASR-015: Agent tasks must operate within defined ceilings on compute time, request rate, and data-store load

**Status:** Draft
**Date:** 2026-09-02
**Driver:** [Family: CROSS-CUTTING] NIST SP 800-53 Rev 5 (SC-5 denial-of-service protection, generalized to agent resource consumption)

## Requirement statement
Every agentic capability must operate within explicit, defined ceilings on compute time, request rate against any downstream system, and load placed on any data store it accesses. These ceilings must be enforced by the architecture, not left as an assumption about how the agent will behave.

## Architectural significance
An agent operates at machine speed and can repeat an action far faster and more persistently than a human operator performing the same task — a bounded mistake for a human (a slow, manual retry loop) becomes an unbounded one for an agent absent an explicit ceiling. Without defined limits, a single malfunctioning or looping agent task can degrade shared infrastructure or amplify cost at a scale disproportionate to the task's actual value, and nothing in the architecture would stop it before the ceiling is reached rather than after damage occurs.

## Related ADRs
None yet — open requirement. (ADR-011, the resource and consumption guardrail decision this requirement calls for, remains undrafted pending clearer corpus precedent; see `ASR-ADR-Outline-Catalog.md`.)

> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# ASR-024: A systematic defect in an agent's foundational input pipeline must trigger rebuild from trusted source, not patching of downstream artifacts

**Status:** Draft
**Date:** 2026-09-02
**Driver:** [Family: CROSS-CUTTING] NIST SP 800-53 Rev 5 (SI-7 information integrity, generalized); general data-integrity principle established by ASR-004

## Requirement statement
If a systematic defect is found in the input pipeline a capability's foundational layer depends on — the ingestion, extraction, or preprocessing step ASR-004 requires structural-fidelity verification of — the architecture must rebuild affected downstream artifacts from the original trusted source. Patching the already-produced downstream artifacts to compensate for the defect is not an acceptable substitute.

## Architectural significance
Patching downstream artifacts to compensate for an upstream defect leaves the defect itself unresolved and creates two divergent lineages — the corrected artifacts and whatever the same flawed pipeline continues to produce — that a later reviewer cannot reconcile without separately tracking which patch applied to which output. Rebuilding from trusted source instead produces a single, traceable lineage and directly addresses the defect ASR-004 was written to catch, rather than working around it after the fact.

## Related ADRs
None yet — open requirement. (ADR-020, backlog, covers related quarantine/remediation ground but is not drafted this round.)

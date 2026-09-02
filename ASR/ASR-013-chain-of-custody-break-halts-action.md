> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# ASR-013: A break in the chain of custody must halt autonomous action; a disclosed, bounded quality miss must not

**Status:** Draft
**Date:** 2026-09-02
**Driver:** [Family: CROSS-CUTTING] NIST SP 800-53 Rev 5 (SI-7 software, firmware, and information integrity, generalized to agent evidentiary chains); general data-provenance principle established by ASR-004

## Requirement statement
If the chain connecting an agent's action back to its source evidence and authorization (per ASR-012) is broken, missing, or cannot be verified, the architecture must halt further autonomous action pending review — the break itself, not any judgment about the action's likely correctness, is what triggers the halt. A disclosed, bounded quality limitation in the underlying evidence that does not break the chain — its provenance and limitation are both known and recorded — must not, by itself, trigger the same halt.

## Architectural significance
Treating every quality limitation identically to a broken chain of custody creates an incentive to under-disclose known limitations rather than record them, since disclosure and total failure would carry the same consequence — undermining ASR-004's structural-fidelity verification requirement, which depends on limitations being surfaced rather than hidden. Conversely, treating a broken chain as anything less than an automatic halt allows autonomous action to continue on the basis of evidence whose actual origin or integrity can no longer be verified, which is a materially different and more severe condition than a disclosed, bounded gap.

## Related ADRs
None yet — open requirement. The hard-stop-versus-logged-limitation criteria this requirement calls for (catalog entry ADR-009) remains undrafted pending clearer corpus precedent; see `ASR-ADR-Outline-Catalog.md`.

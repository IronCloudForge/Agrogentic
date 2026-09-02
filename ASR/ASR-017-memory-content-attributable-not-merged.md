> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# ASR-017: Content an agent retrieves from memory must remain attributable to its originating session, never silently merged across users

**Status:** Draft
**Date:** 2026-09-02
**Driver:** [Family: CROSS-CUTTING] NIST SP 800-53 Rev 5 (AC-4 information flow enforcement, generalized to cross-session/cross-user memory segregation)

## Requirement statement
Any content an agent retrieves from a long-term memory store must remain attributable to the session, user, or context that originally produced it. Memory content from different users or sessions must never be silently merged into a single undifferentiated context an agent draws from without attribution.

## Architectural significance
Without per-origin attribution, a memory store that pools content across users or sessions creates a path for one user's context to surface in another's interaction without either party's awareness — a form of cross-boundary data exposure that would be treated as a clear violation if it occurred through a conventional data store, but can occur silently through memory retrieval if attribution is not preserved. Attribution is also the precondition for any later access-control or deletion request to be honored correctly: content that cannot be traced to its origin cannot be selectively removed or restricted without affecting unrelated content.

## Related ADRs
None yet — open requirement. (ADR-012, the memory architecture and cross-session isolation decision this requirement calls for, remains undrafted pending clearer corpus precedent; see `ASR-ADR-Outline-Catalog.md`.)

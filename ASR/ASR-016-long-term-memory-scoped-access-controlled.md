> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# ASR-016: Long-term agent memory stores must be scoped and access-controlled with the same rigor as any other sensitive data store

**Status:** Draft
**Date:** 2026-09-02
**Driver:** [Family: CROSS-CUTTING] NIST SP 800-53 Rev 5 (AC-3 access enforcement; AC-4 information flow enforcement, generalized to agent memory as a data store)

## Requirement statement
A long-term memory store an agent writes to or reads from must be scoped and access-controlled to the same standard as any other data store holding comparably sensitive content — never treated as an internal implementation detail exempt from the access controls that would apply if the same content were held in a conventional database.

## Architectural significance
Agent memory accumulates context across sessions and tasks, often drawing from multiple upstream sources with different sensitivity levels and different original access controls. If memory itself is not independently scoped and access-controlled, it becomes an under-governed side channel: content that was properly access-controlled at its source can end up readable through the memory store by anything with access to the agent, regardless of whether that access matches the original control.

## Related ADRs
None yet — open requirement. (ADR-012, the memory architecture and isolation decision this requirement calls for, remains undrafted pending clearer corpus precedent; see `ASR-ADR-Outline-Catalog.md`.)

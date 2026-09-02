# Crosswalk: research practice ↔ ASR/ADR governance

Two vocabularies, one method. Every row maps a concept the research-science working group already uses to its architecture-governance counterpart — because the underlying discipline is the same in both worlds: don't trust a claim until it's on the record, tested, and traceable.

This crosswalk operates within the four-layer documentation model described in `Layer-Model.md`. In that model's terms: an ASR's `Driver` field is the equivalent of citing the standard or authority a hypothesis must ultimately answer to (Layer 4), while its `Corpus evidence` section is the equivalent of citing prior published work that corroborates a hypothesis without itself being the authority for it (Layer 3) — see the added row below.

| Research language | CIO / architecture language | Why they're the same idea |
|---|---|---|
| Hypothesis / research question | ASR (architecturally-significant requirement) | A claim that needs to be justified and tested before anyone acts on it — not yet a conclusion, just something on the record |
| Lab notebook entry | ASR draft | Dated, attributed to a condition or driver, logged the moment you notice it — doesn't need to be resolved yet, just captured |
| Methods section | ADR (architecture decision record) | The choice you made, written so it's reproducible: what you did, why, and what it rules out |
| Citing prior published work | Corpus evidence citation (Layer 3) | Grounding a claim in independently reproducible external work — a benchmark, a production deployment, a reference implementation — without treating that work as the authority obligating the claim |
| Peer review | Independent verification before an autonomy grant | Neither discipline lets a system, or a researcher, certify its own result — a separate check is required before the claim is trusted |
| Reproducibility | Provenance / audit trail | A finding — or a decision — is only as good as your ability to trace it back to its source evidence |
| Literature review | The ASR Log | A shared record of what's already known and already open, so no one has to reconstruct context from memory or reinvent it independently |
| Pre-registration | Filing the ASR before the ADR | The requirement goes on record before the decision is made, so the decision can't be quietly reshaped afterward to fit a preferred outcome |
| Control / baseline condition | Tier 1 — advisory-only autonomy | The default you compare against before granting anything more — the floor, not a judgment on the capability |
| Null result | An open ASR with no ADR yet | A real, useful, disclosed finding — not something to hide or treat as a failure |
| Retraction / erratum | ADR amendment log, or a superseded ADR | Corrections happen by dated addition or by a new ADR that formally supersedes the old one — never a silent rewrite of the original |
| Principal investigator sign-off | ADR status: Accepted | Someone with standing formally attests the record is sound enough to build on |
| Meta-analysis | Cross-ADR pattern review | Synthesizing decisions already on record to surface a higher-order requirement none of the individual entries captured alone |
| Instrument / dataset provenance | ASR driver citation | Where the requirement's authority actually comes from — a standard, a policy, a measured condition — never just an assertion |

## The point

Nothing here is a new discipline being imposed on the working group. It's the same standard of rigor — hypothesis before conclusion, method before result, review before trust, correction by addition rather than erasure — expressed in the vocabulary a different field already uses for exactly the same reasons.

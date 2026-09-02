# USDA Agentic AI Governance Architecture

This is an independent, volunteer-run open-source research project. It is not sponsored, reviewed, sanctioned, or endorsed by the U.S. Department of Agriculture or any federal agency. Nothing in this repository represents official USDA policy, guidance, or an authorized architecture. It is published in the hope that governance patterns developed here may be useful to the broader public-sector and open-source community.

## Start here

If you're new to this repository, read in this order:

1. **`Layer-Model.md`** — the four-layer model everything else in this repo is organized around. Read this first; every other document assumes it.
2. **`ASR/ASR-Log.md`** and **`ADR/ADR-Log.md`** — the current, authoritative index of every accepted requirement and decision. These are the source of truth; everything else supports them.
3. **`Knowledge-Source-References.md`** — the standing, tiered catalog of Layer 3 external sources (OWASP, MITRE, Uber, Microsoft, CSA, and others) that ASRs cite as `Corpus evidence`. Every such citation in this repo traces back to an entry here. Local archives of the cataloged sources themselves live in `Knowledge-Sources/`, organized by the same tiers.
4. **`Research-to-Governance-Crosswalk.md`** — if you're coming from a research or scientific background rather than a governance/architecture one, this maps the vocabulary you already know onto the vocabulary this repo uses.
5. **`ASR-ADR-Outline-Catalog.md`** — the backlog. Titled but undrafted ASRs and ADRs, organized by architecture layer, for anyone looking for where to contribute next.

## The four-layer model, briefly

| Layer | What it is | Authoritative? |
|---|---|---|
| **1 — Authority** | The signed instrument — whatever the AI CIO or authorizing OCIO SES formally signs. A compiled, dated snapshot of Layer 2. | Yes — the only layer with authorizing weight |
| **2 — Architecture requirements & decisions** | This repository: the ASR Log, ADR Log, and individual ASR/ADR documents | No — this is the working layer that Layer 1 draws from |
| **3 — Knowledge sources** | The external industry corpus — published research, production case studies, open-source reference implementations | No — evidentiary only, cited as `Corpus evidence` / `Corpus reference` |
| **4 — Federal Standards** | NIST SP 800-53, 800-207, 800-128, 800-137, FIPS 199, FedRAMP/OSCAL, OMB memoranda, CISA ZTMM, NIST AI RMF, and all AI-specific overlays — cloud, on-prem, and AI standards alike | Yes — this is what actually obligates the architecture |

Full detail, including the Driver family-tag definitions (`AI`, `CLOUD`, `ON-PREM`, `CROSS-CUTTING`), is in `Layer-Model.md`.

## What an ASR is

An **Architecturally-Significant Requirement**: a short, dated, forward-stated claim that the architecture must satisfy some condition. Every ASR's `Driver` field cites the Layer-4 federal standard or policy that obligates it, tagged with a Family. An ASR may optionally include `Corpus evidence` — direct, linkable citations to Layer-3 sources that corroborate the requirement empirically, without serving as its authority.

## What an ADR is

An **Architecture Decision Record**: a dated record of one specific decision made in response to one or more ASRs — the context that necessitated it, the decision itself, and its consequences. ADRs are never edited to remove or alter prior content; corrections are recorded as dated additions to the amendment log, or as a new ADR that formally supersedes the old one.

## Repository contents

```
Layer-Model.md                                         Four-layer model and Family tag reference — read first
ASR-ADR-Outline-Catalog.md                              Backlog of titled-but-undrafted ASRs/ADRs, by architecture layer
Research-to-Governance-Crosswalk.md                     Research-vocabulary <-> governance-vocabulary crosswalk
Knowledge-Source-References.md                          Tiered catalog of Layer 3 external sources cited as Corpus evidence

ASR/                                                    Architecturally-Significant Requirements
  ASR-Log.md                                              Index of all accepted ASRs
  ASR-Template.md                                         Template for drafting a new ASR
  ASR-001-accelerated-adoption-requires-tiered-governance.md
  ASR-002-baseline-directive-specificity.md
  ASR-003-architectural-intent-compliance-alignment.md
  ASR-004-structural-fidelity-verification.md
  ASR-005-agent-identity-scoped-entitlement.md

ADR/                                                    Architecture Decision Records
  ADR-Log.md                                              Index of all accepted ADRs
  ADR-Template.md                                         Template for drafting a new ADR
  ADR-001-autonomy-tiering.md

Knowledge-Sources/                                      Local archives of the cataloged Layer 3 sources, by tier
  Tier-1/                                                  Institutional or vendor-backed sources
  Tier-2/                                                  Credible research or production evidence
  Tier-3/                                                  Reserved — not yet built out

.github/                                                 Issue/PR templates for proposing ASRs and ADRs
```

## How to contribute

1. **Read the Logs.** Check `ASR/ASR-Log.md` and `ADR/ADR-Log.md` for what's already accepted, and `ASR-ADR-Outline-Catalog.md` for what's titled but open.
2. **Notice a requirement? Draft an ASR.** Copy `ASR/ASR-Template.md`. State the requirement, not the story behind it — one page, forward-framed, no reference to who found it or what went wrong. Tag the `Driver` field with at least one Layer-4 Family (`AI`, `CLOUD`, `ON-PREM`, or `CROSS-CUTTING`). Add `Corpus evidence` only if a genuine, linkable Layer-3 source corroborates it.
3. **Have a decision? Draft an ADR.** Copy `ADR/ADR-Template.md`. Trace it to the ASR(s) it answers. State context, decision, and consequences plainly; use a table for anything tiered or multi-option.
4. **Never silently edit an accepted ASR or ADR.** Corrections are dated additions to the amendment log (ADRs) or a formally superseding entry (either type), with the old entry's status updated and retained — not rewritten in place.

See `CONTRIBUTING.md` for the full contribution workflow, and `CODE_OF_CONDUCT.md` for how discussion here is expected to go.

## A note on sourcing discipline

Every claim in this library should be traceable: a Layer-4 citation for authority, and where applicable, a direct link to a Layer-3 source for corroboration — a GitHub repository, a paper, a standards-body publication — rather than an unlinked assertion. The goal is that any entry in this library can be independently verified by a reader with no prior context on this project, tracing every claim back to either a federal standard or a reproducible external source.

---
*This README reflects the state of the library as of 2026-09-02.*

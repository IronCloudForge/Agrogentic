# Contributing

This repository is an independent, volunteer-run research library, not an official USDA channel. See `README.md` for the project's scope and the four-layer documentation model in `Layer-Model.md` before reading further — everything below assumes both.

## Ways to contribute

- **Propose a new ASR (Architecturally-Significant Requirement).** Use the [Propose an ASR](.github/ISSUE_TEMPLATE/propose-asr.md) issue template, or copy `ASR/ASR-Template.md` directly into a pull request.
- **Propose a new ADR (Architecture Decision Record).** Use the [Propose an ADR](.github/ISSUE_TEMPLATE/propose-adr.md) issue template, or copy `ADR/ADR-Template.md` directly into a pull request.
- **Draft an entry from the backlog.** `ASR-ADR-Outline-Catalog.md` lists titled-but-undrafted ASRs and ADRs by architecture layer — pick one up, split it, merge it, or drop it, as makes sense once you're drafting.
- **Add a Layer 3 source.** New sources go into `Knowledge-Source-References.md` following its own "How to add a source" section, and (ideally) get archived under `Knowledge-Sources/<Tier>/` alongside the catalog entry.
- **Flag an error.** Factual errors, broken corpus citations, or drift between an ASR/ADR and the standard it cites are welcome as issues even if you're not proposing a fix yourself.

## Drafting standards

- **State the requirement, not the story.** An ASR is a short, dated, forward-stated claim the architecture must satisfy — not a narrative of who found the gap or what went wrong.
- **Every ASR's `Driver` field needs at least one Layer-4 Family tag** (`AI`, `CLOUD`, `ON-PREM`, or `CROSS-CUTTING`) — see `Layer-Model.md` for the tag definitions. This is what ties the requirement to an actual obligating standard rather than an opinion.
- **`Corpus evidence` is optional and evidentiary only.** Add it only when a genuine, linkable Layer-3 source corroborates the requirement — and only from an entry already vetted in `Knowledge-Source-References.md` (or a new one you're adding in the same contribution, tiered honestly per that document's own tiering guidance).
- **Every ADR traces to the ASR(s) it answers.** State context, decision, and consequences plainly; use a table for anything tiered or multi-option.
- **Never silently edit an accepted ASR or ADR.** Corrections are dated additions to the amendment log (ADRs), or a new entry that formally supersedes the old one with the old entry's status updated and retained — never a rewrite in place. This applies to typo-level fixes too, unless they are genuinely non-substantive (e.g. a broken markdown link).

## Pull request checklist

1. Does your ASR/ADR ID follow the next unused number in `ASR-Log.md` / `ADR-Log.md`?
2. Did you add the corresponding row to the Log table, in ID order?
3. If drafting from the outline catalog, did you update that entry's status in `ASR-ADR-Outline-Catalog.md`?
4. Does every `Driver` citation resolve to a real, checkable Layer-4 standard?
5. Does every `Corpus evidence` link resolve to a real, independently reproducible Layer-3 source — and does that source have an entry in `Knowledge-Source-References.md`?

## Code of conduct

This project follows the guidelines in `CODE_OF_CONDUCT.md`. By participating, you're expected to uphold it.

## Reporting a security or sensitive-content issue

See `SECURITY.md` — do not open a public issue for anything that shouldn't be public before it's addressed.

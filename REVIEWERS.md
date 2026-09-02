> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# Start Here — For Reviewers

If you're a USDA (or broader public-sector) domain volunteer landing here to look at agentic AI governance content — not to write code — this page is for you. Read it before `CONTRIBUTING.md`.

## What you're looking at

This repository is soil and wood, not a finished frame. Every ASR and ADR here was drafted by an independent volunteer effort, using AI to organize research faster than a person could alone — not authorized, not USDA-reviewed, not final. Every document says so at the top, and every one's `Status` field reads `Draft`. Read `README.md`'s disclaimer and `Layer-Model.md`'s four-layer model before anything else — that model is what tells you these documents are Layer 2 (working requirements and decisions), never Layer 1 (actual authority). Nothing in this repository becomes policy by being read, agreed with, or left unchallenged.

## What a review actually means here

Reading a document and reviewing it are different things. To review one:

1. **Check the `Driver` field.** Does it cite a real, checkable federal standard — a NIST SP, an OMB memo, a FIPS? If the citation is vague, generic, or doesn't hold up when you look it up yourself, that's a genuine finding. Say so.
2. **Check `Corpus evidence`, where present.** It's evidentiary only, never authority — does the cited source (OWASP, MITRE, Uber, Microsoft, CSA, and others) actually say what the ASR claims it says? Every citation should trace to an entry in `Knowledge-Source-References.md`; if it doesn't, that's a defect worth flagging.
3. **Judge fit, not just correctness.** The corpus can show a requirement is real somewhere in industry. It cannot tell you whether it's *right for USDA's actual environment* — mission-area structure, existing ICAM, existing risk tolerance, procurement reality. That judgment is the part no amount of research replaces, and it's the reason this work needs you specifically, not just more sources.
4. **Flag, don't silently fix.** Open an issue or a PR per `CONTRIBUTING.md`. Nothing here is precious — every document is a Draft, and every one can be revised, merged, or dropped.

## Where the real gaps are

- `ASR-ADR-Outline-Catalog.md` — anything still marked `Proposed` is a title and nothing else. That's the most direct way to contribute: pick one up.
- Several ADRs were deliberately **not drafted**, because no genuine precedent existed in the current 12-source corpus to ground a decision on rather than architectural opinion alone — each has a note explaining why in the catalog and in its corresponding ASR's own "Related ADRs" field. If you know of real precedent, or hold the standing to make the call from judgment alone, that is exactly the kind of contribution this project needs.
- `ADR-018` ("adoption of the USDA agent developer/vendor evaluation checklist") is explicitly unresolved — it names an artifact this project has no access to and can't verify. If you know whether that checklist exists and what it contains, that's a fast, high-value contribution.

## What this is not

Not policy. Not USDA-endorsed. Not something to cite as if it were either — to anyone, for any purpose. See the disclaimer on this page, and on every page, for why.

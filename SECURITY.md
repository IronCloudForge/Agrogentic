# Security Policy

## What this repository is — and isn't

This is an independent, volunteer-run open-source research library of governance documentation (ASRs, ADRs, and a supporting knowledge base). It is **not sponsored, reviewed, sanctioned, or endorsed by the U.S. Department of Agriculture or any federal agency**, and it is not an official reporting channel for USDA or federal systems.

**If you've found a security vulnerability in an actual USDA system, application, or service, do not report it here.** Report it through USDA's own official channels, or through CISA at [cisa.gov/report](https://www.cisa.gov/report) if no USDA-specific channel is available.

This repository contains no deployable code — it is markdown documentation and archived reference material. The categories below are what "security" actually means in this specific repo's context.

## What to report here

- **A factual error that could mislead a security-relevant governance decision** — e.g. a `Driver` field citing a NIST control that doesn't say what the ASR claims it says, a `Corpus evidence` citation that misrepresents its source, or a source in `Knowledge-Source-References.md` / `Knowledge-Sources/` that turns out to be inaccurately characterized, retracted, or was mis-tiered in a way that overstates its credibility.
- **A sensitive-content or safety concern** with something published in this repository.
- **A conduct issue** under `CODE_OF_CONDUCT.md` that you'd prefer not to raise in a public issue.

None of the above are software vulnerabilities in the traditional sense, but they can matter just as much in a repository whose stated goal (see the README's "note on sourcing discipline") is that every claim be independently verifiable.

## How to report

Prefer a private report over a public issue when the report itself could be sensitive (e.g., it names a real, unpatched flaw in a third-party tool referenced in `Knowledge-Sources/`, or involves a conduct concern). Use this repository's GitHub **Security** tab → **Report a vulnerability**, which opens a private advisory visible only to the maintainers.

If private advisories aren't enabled on this repository at the time you're reading this, open a regular issue but omit any sensitive specifics, and note that you have a private report to make — a maintainer will follow up to arrange a private channel.

For anything that doesn't need privacy — a factual correction, a stale link, a mis-cited control — a normal public issue or pull request is the faster path; see `CONTRIBUTING.md`.

## Response expectations

This is a volunteer project with no dedicated security team and no SLA. Reports will be acknowledged as promptly as maintainer availability allows.

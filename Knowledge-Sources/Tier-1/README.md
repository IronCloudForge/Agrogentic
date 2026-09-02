# Tier 1 Knowledge Sources

Local archive of the Tier 1 sources catalogued in `Knowledge-Source-References.md` (institutional or vendor-backed; citable in official work). Where the source's own hosting made a direct file download possible (GitHub-hosted repos and files), the content was captured directly; where the primary domain wasn't reachable from this environment (genai.owasp.org, atlas.mitre.org, cloudsecurityalliance.org), content was extracted via automated fetch instead — see each file's footer note for its specific method.

| Catalog entry | File | Format |
|---|---|---|
| OWASP Agentic Skills Top 10 (AST10) | `owasp-agentic-skills-top-10.md` | Markdown notes (README + incident timeline) |
| OWASP Top 10 for Agentic Applications (2026) | `owasp-top-10-agentic-applications-2026.md` | Markdown, full ASI01–ASI10 list from the primary PDF |
| Microsoft Agent Governance Toolkit (AGT) | `microsoft-agent-governance-toolkit.md` | Markdown notes (README + spec/conformance-test summary) |
| MITRE SAFE-AI | `mitre-safe-ai.md` | Markdown, full-text extraction (PDF not directly downloadable) |
| MITRE ATLAS | `mitre-atlas.md` | Markdown (Fact Sheet + structured YAML data from `mitre-atlas/atlas-data`) |
| CSA AI Controls Matrix (AICM) | `csa-ai-controls-matrix.md` | Markdown (CSA artifact page + announcement blog) |
| IBM AI Atlas Nexus | `ibm-ai-atlas-nexus.md` | Markdown notes (README + repo metadata) |

All pulled 2026-09-02. No PDFs were archivable for this tier — none of the three non-GitHub sources (OWASP genai.owasp.org, MITRE atlas.mitre.org, CSA cloudsecurityalliance.org) were reachable for direct binary download from this environment, only via the WebFetch tool's own routing. See each file for its specific extraction method and caveats.

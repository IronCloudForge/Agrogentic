# OWASP Agentic Skills Top 10 (AST10)

**Tier:** 1 — Institutional or vendor-backed; citable in official work
**Catalog link:** github.com/OWASP/www-project-agentic-skills-top-10
**Date pulled:** 2026-09-02
**Repo stats at pull time:** 192 stars · 59 forks · 31 open issues · created 2026-03-21 · last pushed 2026-08-12 · License: CC BY-SA 4.0 · Version 1.0-2026 (Public Review v1 draft)
**Status:** OWASP Incubator project, led by Ken Huang (OWASP AIVSS Lead)

## What it contributes to this library

Skill/behavior-layer threat taxonomy (AST01–AST10); incident timeline (ClawHavoc, ToxicSkills, ClawJacked); the "lethal trifecta" risk heuristic; Universal Skill Format proposal.

## Overview

The first comprehensive security framework for AI agent skills, covering OpenClaw (SKILL.md YAML), Claude Code (skill.json), Cursor/Codex (manifest.json), and VS Code (package.json) ecosystems. Positions skills as the **behavior layer** — distinct from both the model layer (LLM security) and the tool layer (MCP security): *"MCP = how the model talks to tools; AST10 = what those tools actually do."* Cross-references CSA's 7-layer MAESTRO threat model.

## The lethal trifecta

An agent skill is especially dangerous when it combines all three:
1. **Access to private data** (SSH keys, API credentials, wallet files)
2. **Exposure to untrusted content** (skill instructions, memory files, email)
3. **Ability to communicate externally** (network egress, webhook calls)

Most production agent deployments satisfy all three conditions simultaneously.

## Scale of the problem (2026 statistics)

| Metric | Figure | Source |
|---|---|---|
| Skills scanned | 3,984 | Snyk ToxicSkills (Feb 2026) |
| Skills with security flaws | 1,467 (36.82%) | Snyk ToxicSkills (Feb 2026) |
| Skills with critical issues | 534 (13.4%) | Snyk ToxicSkills (Feb 2026) |
| Confirmed malicious payloads | 76+ | Snyk ToxicSkills (Feb 2026) |
| ClawHavoc campaign malicious skills | 1,184 | Antiy CERT (Feb 2026) |
| OpenClaw instances internet-exposed | 135,000+ | SecurityScorecard (Feb 2026) |
| CVEs disclosed (OpenClaw alone) | 9 (3 with public exploits) | Endor Labs (Feb 2026) |
| Skills analyzed across all registries | 30,000+ | National CIO Review / Cisco (2026) |
| Skills with ≥1 vulnerability (all registries) | >25% | National CIO Review (2026) |

## Incident timeline (2026)

- **Feb 25, 2026** — Check Point Research ("Caught in the Hook") discloses **CVE-2025-59536** (CVSS 8.7) and **CVE-2026-21852** (CVSS 5.3) in Claude Code: repository-controlled configuration files can silently execute arbitrary shell commands and exfiltrate API keys at project-open time, before any trust dialog. Both were patched months prior to disclosure.
- **Feb 26, 2026** — **ClawJacked** disclosed by Oasis Security (**CVE-2026-28363, CVSS 9.9**): malicious websites can brute-force localhost WebSocket connections (no rate limiting) to silently hijack local OpenClaw instances, register new devices without user prompts, and exfiltrate data through existing agent integrations. OpenClaw patched within 24 hours (v2026.2.25).
- **Feb 2026** — Antiy CERT publishes the **ClawHavoc Campaign Analysis**, classifying the malware as `Trojan/OpenClaw.PolySkill`: 1,184 malicious skills across 12 publisher accounts. Hudson Rock separately identifies Vidar infostealer variants specifically targeting OpenClaw agent identity files (`openclaw.json`, `device.json`, `soul.md`, `memory.md`).
- **Feb 5, 2026** — Snyk: **280+ leaky skills** — API key and PII exposure across the ClawHub registry.

## The AST01–AST10 risk taxonomy

| # | Risk | Severity | Key mitigation | Evidence |
|---|---|---|---|---|
| AST01 | Malicious Skills | Critical | Cryptographic signing, behavioral scanning | ClawHavoc campaign |
| AST02 | Supply Chain Compromise | Critical | Transparency logs, dependency pinning | — |
| AST03 | Over-Privileged Skills | High | Least-privilege manifests, runtime enforcement | *(cited directly in this library's `ASR-005-agent-identity-scoped-entitlement.md` as "risk AST03")* |
| AST04 | Insecure Metadata | High | Schema validation, safe parsers, sandboxed loading | — |
| AST05 | Untrusted External Instructions | High | Source inventory, content pinning/inlining, continuous rescanning | Anthropic docs warn fetched URLs "may contain malicious instructions"; Air's "Story of Skills" PoC bypassed all scanners, proved possible takeover of 26,000 agents |
| AST06 | Weak Isolation | High | Containerization, Docker sandboxing | OpenClaw host-mode execution, 135K exposed instances |
| AST07 | Update Drift | Medium | Immutable pinning, hash verification | ClawJacked (CVE-2026-28363), patch-lag exploitation |
| AST08 | Poor Scanning | Medium | Semantic + behavioral multi-tool pipeline | Pattern-matcher bypass via natural-language injection |
| AST09 | No Governance | Medium | Skill inventories, agentic identity controls, audit logging | 53K exposed instances with no SOC visibility |
| AST10 | Cross-Platform Reuse | Medium | Universal Skill Format, platform validation | — |

## Universal Skill Format proposal

A cross-platform skill-security standard intended to let skill signing, permission manifests, and scanning results travel consistently across OpenClaw, Claude Code, Cursor/Codex, and VS Code, rather than each platform maintaining incompatible metadata formats.

## Getting-started guidance (as structured in the repo)

- **Security teams:** assess posture via the Security Assessment Checklist → review the 10 AST files for platform-specific guidance → implement controls → monitor threat intelligence.
- **Skill developers:** least-privilege + secure coding → adopt Universal Format → cryptographically sign skills → test in isolated environments.
- **Platform developers:** registry scanning/provenance tracking → default to sandboxed runtime isolation → comprehensive audit logging → require explicit confirmation for privileged operations.

## Companion documents in the repo (not individually mirrored here)

`checklist.md` (Security Assessment Checklist) · `universal-skill-format.md` · `case-studies.md` · `threat-intelligence.md` · `risk-assessment.md` · `skill-scanner-integration.md` · `api-documentation.md` · `skill-development-guide.md` · `platform-comparison.md` · `incident-response.md` · `metrics-monitoring.md` · individual `ast01.md`–`ast10.md` risk detail pages.

## License

CC BY-SA 4.0.

---
*Extracted via direct read of the repository's README, index.md, and GitHub API metadata (github.com/OWASP/www-project-agentic-skills-top-10, `main` branch). The ten individual AST0x detail pages and listed companion documents were not individually pulled.*

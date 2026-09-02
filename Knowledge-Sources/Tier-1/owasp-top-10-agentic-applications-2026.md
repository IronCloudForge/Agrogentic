# OWASP Top 10 for Agentic Applications (2026)

**Tier:** 1 — Institutional or vendor-backed; citable in official work
**Catalog link:** genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026
**Primary document:** genai.owasp.org/download/52117 (PDF, linked from the resource page)
**Date pulled:** 2026-09-02

## What it contributes to this library

Model/reasoning-layer agentic risk taxonomy; the sibling project to AST10 (OWASP Agentic Skills Top 10), which extends downward into the skill layer.

## Publication details

- **Version:** 2026 (published December 2025)
- **License:** CC BY-SA 4.0
- **Project:** OWASP Gen AI Security Project — Agentic Security Initiative
- **Leadership:** Chair — John Sotiropoulos (Deep Cyber); Lead — Keren Katz (Tenable); Core Team Member & Co-lead — Ron F. Del Rosario (SAP)
- **Authorship:** Developed through collaboration with 100+ industry experts, researchers, and practitioners; globally peer-reviewed.

## The ten Agentic Security Items (ASI01–ASI10)

### ASI01 — Agent Goal Hijack
Attackers manipulate agent objectives through prompt injection, deceptive tool outputs, or poisoned data — redirecting goals, planning, and multi-step behavior across autonomous workflows (not just a single response).
*Mitigations:* treat all natural-language input as untrusted; define and lock agent system prompts; validate user/agent intent before high-impact actions; sanitize connected data sources (RAG, email, APIs); maintain logging and behavioral baselines.

### ASI02 — Tool Misuse and Exploitation
Agents misuse legitimate tools via prompt injection or unsafe delegation — data exfiltration, tool-output manipulation, or workflow hijacking, despite operating within authorized privileges.
*Mitigations:* least-privilege profiles per tool; explicit auth + human approval for high-impact actions; isolated sandboxes for tool execution; policy-enforcement middleware ("Intent Gate"); monitor for anomalous tool-chaining.

### ASI03 — Identity and Privilege Abuse
Attackers exploit dynamic trust/delegation chains to escalate access and bypass controls by manipulating delegation chains, role inheritance, and cached credentials across interconnected systems.
*Mitigations:* task-scoped, time-bound permissions with short-lived tokens; isolate agent identities/contexts per session; per-action authorization via a centralized policy engine; human approval for privilege escalation; bind OAuth tokens to signed intent.

### ASI04 — Agentic Supply Chain Vulnerabilities
Third-party agents, tools, and artifacts — including MCP servers and dynamically loaded components — may be malicious, compromised, or tampered with in transit, introducing unsafe code and hidden instructions.
*Mitigations:* sign/attest manifests, require and operationalize SBOMs/AIBOMs; allowlist and pin dependencies, scan for typosquats; sandboxed containers for sensitive agents; mutual authentication/attestation via PKI and mTLS; re-check signatures/hashes at runtime.

### ASI05 — Unexpected Code Execution (RCE)
Agents generate and execute code exploitable via prompt injection or unsafe serialization — host/container compromise, persistence, or sandbox escape.
*Mitigations:* sanitize agent-generated code (input validation, output encoding); no direct agent-to-production paths, operationalize pre-production checks; ban `eval()` in production, require safe interpreters; never run as root, sandboxed containers with strict limits; human approval for elevated runs; maintain allowlists.

### ASI06 — Memory & Context Poisoning
Adversaries corrupt stored agent context — conversation history, summaries, embeddings, RAG stores — biasing or endangering future reasoning, planning, or tool use, or aiding exfiltration.
*Mitigations:* encrypt data in transit/at rest, least-privilege access; scan all memory writes for malicious/sensitive content before commit; isolate user sessions and domain contexts; require source attribution, detect suspicious update patterns/frequencies; prevent automatic re-ingestion of agent-generated outputs into trusted memory.

### ASI07 — Insecure Inter-Agent Communication
Multi-agent systems with weak authentication, integrity, or semantic validation let attackers intercept, manipulate, spoof, or block messages between coordinating agents.
*Mitigations:* end-to-end encryption with per-agent credentials and mutual authentication; digitally sign messages, validate for hidden/modified natural-language instructions; nonces/session identifiers/timestamps; disable weak communication modes, enforce version/capability policies; secure directories with access controls and verified reputations.

### ASI08 — Cascading Failures
A single fault — hallucination, malicious input, corrupted tool — propagates across autonomous agents, compounding into system-wide harm as agents persist state and delegate autonomously.
*Mitigations:* design for fault tolerance assuming component failure/exploitation; sandbox agents with least privilege and network segmentation; short-lived, task-scoped credentials, validate high-impact tool invocations; separate planning and execution via an external policy engine; detect fast-spreading commands, throttle/pause on anomalies; tamper-evident, cryptographically-bound logs of inter-agent messages.

### ASI09 — Human-Agent Trust Exploitation
Agents build strong user trust through fluency and apparent expertise; adversaries exploit this — automation bias, anthropomorphic cues — to influence decisions, extract sensitive information, or steer outcomes.
*Mitigations:* multi-step approval before sensitive data access/risky actions; tamper-proof audit records of queries and agent actions; monitor sensitive-data exposure and risky-action execution; plain-language risk summaries (not model-generated rationales); visually differentiate high-risk recommendations, remind users of limitations; compare action sequences against approved workflow baselines.

### ASI10 — Rogue Agents
Malicious or compromised agents deviate from intended function or authorized scope, acting harmfully, deceptively, or parasitically within multi-agent ecosystems — includes emergent harmful behavior.
*Mitigations:* immutable, signed audit logs of all agent actions and inter-agent communication; trust zones with strict inter-zone rules; behavioral detection and watchdog agents; rapid kill-switches and credential revocation; cryptographic identity attestation and behavioral integrity baselines; fresh attestation + human approval before reintegration.

## Relationship to the OWASP LLM Top 10 (2025)

The document states agentic risks "amplify existing vulnerabilities" from the LLM Top 10, rather than replacing them:

| LLM Top 10 (2025) item | Extends into |
|---|---|
| LLM01:2025 Prompt Injection | ASI01, ASI05 |
| LLM06:2025 Excessive Agency | ASI02, ASI03 |
| LLM04:2025 Data & Model Poisoning | ASI06, ASI08 |
| LLM03:2025 Supply Chain | ASI04 (runtime focus) |

Explicit framing: "Our focus is on Agentic Apps, but these will not exist in isolation" — agentic apps remain "part of developing an LLM App." ASI entries also cross-reference CycloneDX and the Non-Human Identities Top 10.

## Methodology

Built on "open collaboration, peer review, and evidence from research, exploits, incidents, and challenges from real-world deployments." Includes an "ASI Agentic Exploits & Incidents Tracker" (Appendix D) mapping real-world incidents to vulnerabilities, with entries spanning February 2025 through October 2025.

---
*Extracted via automated fetch of the primary OWASP PDF (genai.owasp.org/download/52117, linked from the official resource page). The resource page itself does not enumerate the list — only the PDF does.*

# Uber ADR (paper) — An Agentic Detection System for Enterprise Agentic AI Security

**Tier:** 2 — Credible research or production evidence; cite as evidence, not as a standard
**Catalog link:** arxiv.org/abs/2605.17380
**Local copy:** [`uber-adr-paper-mlsys2026.pdf`](./uber-adr-paper-mlsys2026.pdf) (downloaded from `github.com/uber/ADR/docs/adr-paper.pdf`, the repo's own hosted copy of the accepted paper)
**Date pulled:** 2026-09-02

## Bibliographic

- **Title:** ADR: An Agentic Detection System for Enterprise Agentic AI Security
- **Authors:** Chenning Li, Pan Hu, Justin Xu, Baris Ozbas, Olivia Liu, Caroline Van, Manxue Li, Wei Zhou, Mohammad Alizadeh, Pengyu Zhang, KK Sriramadhesikan, Ming Zhang
- **Venue:** MLSys 2026 (Industry Track)
- **Citation (BibTeX):**
  ```bibtex
  @inproceedings{li2026adr,
    title={ADR: An Agentic Detection System for Enterprise Agentic AI Security},
    author={Li, Chenning and Hu, Pan and Xu, Justin and Ozbas, Baris and Liu, Olivia and Van, Caroline and Li, Manxue and Zhou, Wei and Alizadeh, Mohammad and Zhang, Pengyu and Sriramadhesikan, KK and Zhang, Ming},
    booktitle={Proceedings of the Ninth Conference on Machine Learning and Systems},
    year={2026}
  }
  ```

## Abstract

Enterprise framework for protecting AI agents using the Model Context Protocol (MCP). Addresses three limitations: inadequate visibility into agent decision-making, rigid defenses that fail across varied attack scenarios, and expensive LLM-based detection at enterprise scale. Solution comprises a sensor for agent telemetry, an explorer for pre-deployment adversarial discovery, and a two-stage detector ("fast triage with context-aware reasoning"). Deployed at Uber 10+ months across 7,200+ hosts, 10,000+ daily agent sessions: 97.2% precision detecting 206 credentials across 26 categories; on a custom benchmark (302 tasks, 17 attack techniques), zero false positives while detecting 67% of attacks.

## System architecture

- **ADR Sensor (observability):** reconstructs the full causal chain of agentic activity — user prompts, agent reasoning, MCP tool invocations (args + results), environmental context. Hourly schedule, 0.182s average overhead, parses SQLite/JSONL caches from Cursor, Cline, etc.
- **ADR Detector (two-tier online detection):**
  - *Tier 1 — Triage:* lightweight LLM screening for high recall (prompt-injection phrases, credential/permission requests, risky step combinations).
  - *Tier 2 — Reasoning:* deep semantic analysis with three MCP context providers — source code inspection, threat intelligence lookup, policy verification. Threat intel entries tagged `[EAS]` (Explorer-discovered) or `[CURATED]` (analyst-added).
- **ADR Explorer (offline red-teaming):** three collaborative agents (Red-Teaming, Eval, Threat Intelligence) using an evolutionary algorithm, fitness function F = ε × σ × τ^α (execution depth, semantic naturalness, impact); convergence guaranteed by ρ × µ < 1.0.

## Deployment scale

7,200+ corporate MacBook endpoints (Intel + ARM), 10+ months, growing to 10,000+ agent sessions/day by October 2025. Privacy controls: automated secret redaction, 13-month retention, TLS encryption, least-privilege access.

## Evaluation — ADR-Bench (302 tasks)

133 MCP servers, 729 distinct tools, 17 attack techniques across 5 tactics. 42 malicious tasks (13.9%), 260 benign (86.1%), avg. 28.5 tool calls/task.

- Precision: 1.000 (zero false positives) · Recall: 0.667 (28/42) · F1: 0.800 — outperforms baselines 2–4× in F1.

**Detection rate by threat tactic:**
| Tactic | Detection rate |
|---|---|
| Initial Access & Execution | 68% (13/19) |
| **Permission Abuse** | **20% (1/5) — weakest area** |
| Security Control Bypass | 100% (5/5) |
| Reasoning & Data Manipulation | 56% (5/9) |
| Operational Impact | 100% (4/4) |

*This Permission Abuse figure is the corpus evidence cited directly in `ASR-005-agent-identity-scoped-entitlement.md`.*

**AgentDojo (prompt-injection benchmark):** Recall 1.000 (38/38) · Precision 0.927 (3 FP/93 tasks) · F1 0.962, best among baselines.

**Efficiency:** $0.024/task on ADR-Bench ($0.012 on AgentDojo); avg. latency 18.5s; 40.7% of tasks resolved by Tier 1 alone at $0.017/task, 2.3s.

## Ablation studies

- Removing the triage tier: recall 0.667→0.805, F1 0.800→0.868, but +2 false positives and +29% cost — validates the hierarchical design.
- Removing MCP context providers:
  - Source code inspection removed: recall −14%, F1 −15.5% (largest single impact).
  - Threat intelligence removed: recall 0.667→0.585, F1 0.800→0.716.
  - Policy verification removed: minimal impact (F1 0.800→0.806).

## Credential exposure findings

Detection phase found hundreds of high-severity credential exposures across 26 categories inadvertently shared outside the enterprise network. Prevention layer (regex + entropy-threshold pre-prompt hooks in Cursor/Claude Code): 97.2% precision, 206 true positives, only 6 false positives out of 212 unique credentials, evaluated across hundreds of thousands of MCP sessions.

## Notable attack scenarios tested

- **Internal CTF:** detected a two-stage attack — custom shell tool integration plus deceptive prompts coercing remote code execution.
- **Agent Flayer emulation:** reconstructed an indirect prompt-injection chain (malicious Jira ticket embeds hidden instructions → credential exfiltration via compromised MCP integration); ADR flagged the injection, the credential access, and the outbound transfer.

## Limitations & discussion

1. Benchmark vs. deployment divergence — ADR-Bench gives broad systematic coverage; production shows a skewed real-world distribution (credential leakage common, other attack types rare).
2. Permission Abuse detection (20%) trails every other tactic — flagged as an open problem, not solved by the paper.
3. 49% of escalated alerts in deployment were false positives — mostly conservative escalations on complex-but-benign sessions requiring analyst triage.
4. Precision-first vs. recall-maximizing operating points trade off cost/latency; enterprises must choose.
5. Robustness risks: brittle prompts, model drift, adversarial adaptation — mitigated via prompt/version pinning and regression testing.

## Conclusion

First production-proven enterprise MCP agent-security framework, sustained 10+ months at 7,200+ hosts. Permission Abuse detection remains an open challenge; future work points toward multi-agent coordination protocols and real-time MCP gateway prevention layers (not just detection).

---
*Extracted via automated fetch of the arXiv abstract page and the paper's full text (arxiv.org/pdf/2605.17380 render); PDF file archived locally from the paper's canonical host, `github.com/uber/ADR`.*

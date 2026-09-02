# Microsoft Agent Governance Toolkit (AGT)

**Tier:** 1 — Institutional or vendor-backed; citable in official work
**Catalog link:** github.com/microsoft/agent-governance-toolkit
**Date pulled:** 2026-09-02
**Repo stats at pull time:** 6,175 stars · 1,104 forks · 264 open issues · created 2026-03-02 · last pushed 2026-09-01 · License: MIT · Status: Public Preview (production-quality, may have breaking changes before GA)

## What it contributes to this library

Working, MIT-licensed reference implementation of deterministic policy enforcement, per-agent identity (SPIFFE/DID), execution sandboxing (privilege rings), and kill-switch/SRE controls. 29 architecture decision records; 992 conformance tests against 10 formal specs.

## The problem it targets (as framed in the README)

Three questions any agent deployment must answer:
1. **Is this action allowed?** OAuth scopes/IAM roles control which services an agent can reach, not *what it does* once connected.
2. **Which agent did this?** In multi-agent systems, several agents may share one API key — "an agent did it" is not an incident response.
3. **Can you prove what happened?** Auditors need tamper-evident records of every decision: active policy, what was requested, why it was allowed/denied.

**Core design stance:** prompt-level safety ("please follow the rules") is not a control surface — it's a request to a stochastic system. Cites OWASP LLM01:2025 ("it is unclear if there are fool-proof methods of prevention for prompt injection") and Andriushchenko et al. (ICLR 2025), who report a 100% attack success rate on GPT-4o/GPT-3.5/Claude 3/Llama-3 via adaptive attacks against JailbreakBench. AGT's answer: intercept every tool call, message send, and delegation in deterministic application code *before* the model's intent reaches the wire, so denied actions are "structurally impossible," not merely "unlikely."

## Architecture (as diagrammed in the README)

```
Agent -> Policy Engine -> Identity -> Audit Log
          (YAML/OPA/Cedar)  (SPIFFE/DID/mTLS)  (Tamper-evident)
               |                                      |
               |-- Allowed --> Tool executes           |
               `-- Denied  --> GovernanceDenied        v
                                                 Decision Record
```
Every layer is optional; most teams run policy enforcement + audit logging without the full stack.

## Packages

| Package | Description |
|---|---|
| Agent OS | Policy engine, agent lifecycle, governance gate |
| Agent Control Specification | Stateless, deterministic, fail-closed policy decision runtime (Rust core) backing the AGT policy layer |
| Agent Mesh | Agent discovery, routing, and trust mesh |
| Agent Runtime | Execution sandboxing with **four privilege rings** |
| Agent SRE | **Kill switch**, SLO monitoring, chaos testing |
| Agent Compliance | OWASP verification, policy linting, integrity checks |
| Agent Marketplace | Plugin governance and trust scoring |
| Agent Lightning | RL training governance with violation penalties |
| Agent Hypervisor | Execution audit, delta engine, in-memory commitment tracking, command denylist enforcement |

**Additional capabilities:** MCP Security Gateway (tool poisoning detection, drift monitoring, typosquatting, hidden-instruction scanning); Shadow AI Discovery (finds unregistered agents across processes/configs/repos); Governance Dashboard (real-time fleet health/trust/compliance); PromptDefense Evaluator (12-vector prompt-injection audit); Contributor Reputation (PR/issue author screening, reusable GitHub Action).

## Formal specifications and conformance testing

Every major component has a formal RFC 2119 specification (MUST/SHOULD/MAY) with conformance tests:

| Specification | Scope | Tests |
|---|---|---|
| Agent OS Policy Engine | Native runtime integration, fail-closed semantics | — |
| Agent Control Specification | Stateless intervention-point policy runtime, verdicts, transform, fail-closed | — |
| AgentMesh Identity and Trust | Credentials, trust scoring, delegation chains | 135 |
| Agent Hypervisor Execution Control | Privilege rings, saga orchestration, kill switch | 80 |
| AgentMesh Trust and Coordination | Peer trust negotiation, mesh-wide policy | 62 |
| Agent SRE Governance | SLOs, error budgets, chaos, circuit breakers | 111 |
| MCP Security Gateway | Tool poisoning, drift detection, hidden instructions | 127 |
| Agent Lightning Fast-Path | RL training governance, violation penalties | 100 |
| Framework Adapter Contract | Native framework mediation contract | — |
| Audit and Compliance | Merkle audit, compliance mapping, Decision BOM | 157 |
| AgentMesh Wire Protocol | Message format, routing, serialization | — |

**992 conformance tests** total, keeping code aligned to specs. **29 Architecture Decision Records** (`docs/adr/`) document the reasoning behind them.

## Identity model

Agent identity uses **SPIFFE/DID/mTLS** — e.g. `kernel.EvaluateToolCall("did:mesh:agent-1", "web_search", ...)` in the .NET example — giving each agent its own credential rather than sharing a service account's API key across a multi-agent system. Directly relevant to this library's `ASR-005-agent-identity-scoped-entitlement.md`, which cites AGT as the working reference pattern for issuing each agent its own identity credential as a first-class part of the architecture.

## Example policy (YAML)

```yaml
apiVersion: governance.toolkit/v1
name: production-policy
default_action: allow
rules:
  - name: block-destructive
    condition: "action.type in ['drop', 'delete', 'truncate']"
    action: deny
    description: "Destructive operations require human approval"
  - name: require-approval-for-send
    condition: "action.type == 'send_email'"
    action: require_approval
    approvers: ["security-team"]
```

## CLI tools

```bash
agt doctor                                        # check installation
agt verify                                        # OWASP compliance check
agt verify --evidence ./agt-evidence.json --strict # fail CI on weak evidence
agt red-team scan ./prompts/ --min-grade B         # prompt injection audit
agt lint-policy policies/                          # validate policy files
```

## Language/framework coverage

Five language SDKs (Python, TypeScript, .NET, Rust, Go) implement core governance (policy, identity, trust, audit); Python has the full stack. First-party developer surfaces: Copilot CLI and Claude Code (built on the TypeScript SDK). Native/adapter/middleware integration listed for Microsoft Agent Framework, Semantic Kernel, AutoGen, LangGraph/LangChain, CrewAI, OpenAI Agents SDK, Claude Code, Google ADK, LlamaIndex, Haystack, Mastra, Dify.

Distribution note (v4.1.0): 45 packages consolidated into 5 top-level distributions (`agent-governance-toolkit-core`, `-runtime`, `-sre`, `-cli`, and the `[full]` meta-package); older package names remain installable as redirect stubs.

## Standards/compliance badges claimed

OWASP Agentic Top 10: 10/10 covered · AARM Extended (R1–R9) · ATF (Agentic Trust Framework): All 5 Elements · OpenSSF Scorecard and Best Practices badges present.

## License

MIT.

---
*Extracted via direct read of the repository's README and GitHub API metadata (github.com/microsoft/agent-governance-toolkit, `main` branch). The individual spec documents, 29 ADRs, and threat model were not individually pulled — only the README's own summary of them.*

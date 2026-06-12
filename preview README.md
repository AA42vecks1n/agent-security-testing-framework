# AI Agent Security Testing Framework

An enterprise-grade methodology and test-case taxonomy for security-assessing
LLM-based **AI agents** — systems that don't just generate text, but call tools,
retrieve from knowledge bases, maintain memory, run code, and coordinate with
other agents.

> **Why this exists.** Most "LLM security" work stops at content safety: does the
> model say something harmful? That misses the larger attack surface that appears
> the moment a model is given *agency*. An agent that can read a document, call an
> API, write to memory, and trigger another agent has an attack surface closer to
> a distributed system than to a chatbot. This framework targets that gap.

---

## The core idea: four dimensions, not one

Classic LLM red-teaming optimizes for **content safety** alone. Testing a *regulated*
or *production* agent requires four orthogonal dimensions:

| Dimension | Question it answers |
|---|---|
| **Content safety** | Will the agent produce harmful / disallowed output? |
| **Decision correctness** | Are the agent's *actions and recommendations* correct, especially in high-stakes domains? |
| **Compliance boundaries** | Does the agent stay inside legal / regulatory limits (data residency, labeling, scope of practice)? |
| **Irreversible-action safety** | Can the agent be induced to take an unsafe action that cannot be undone (delete, transfer, send, publish)? |

A jailbreak that only produces bad *text* is a content-safety finding. A prompt
injection that makes the agent *wire money* or *exfiltrate a tenant's data* is a
different and usually more severe class of finding. The framework keeps these
separate by design.

---

## Structure: 8 risk domains × 3 architecture layers

Every test case is classified along two axes.

### Risk domains

| Domain | Scope |
|---|---|
| **Model-Intrinsic Risks** | Prompt injection, jailbreak, indirect/multimodal injection, MCP tool poisoning, RAG poisoning, reward hacking, hallucination, model backdoors, model extraction. |
| **Agent System Risks** | Agent-framework vulnerabilities, insecure sandboxes, unsafe model loading, supply-chain poisoning, compute-environment and platform flaws. |
| **Data Security Risks** | System-prompt leakage, multi-tenant isolation failure, membership inference, insecure storage/cache, transit encryption, memory-data leakage, privacy. |
| **Content, Abuse & Compliance Risks** | Harmful content generation, synthetic-content risks, malicious abuse, loss of behavioral control. |
| **Observability Risks** | Missing or bypassable behavioral monitoring, auditability gaps. |
| **Runtime Security Risks** | Resource abuse, denial of service at the runtime layer. |
| **Governance & Compliance Risks** | Data residency / cross-border transfer, regulatory governance. |
| **Traditional Application Risks** | Classic web/infra (IDOR, SSRF, auth, file upload). *Tracked but out of scope for this AI-security writeup.* |

### Architecture layers

```
┌─────────────────────────────────────────────┐
│  AI Application Layer                         │  prompts, dialogue, output,
│   prompt injection · jailbreak · content      │  user-facing APIs
├─────────────────────────────────────────────┤
│  Agent Core Layer                             │  tool calls, MCP, RAG, memory,
│   MCP poisoning · RAG · memory · sandbox       │  orchestration, code execution
│   escape · multi-agent · observability         │
├─────────────────────────────────────────────┤
│  AI Infrastructure Layer                      │  model serving, containers,
│   model loading · supply chain · isolation     │  storage, network, multi-tenancy
└─────────────────────────────────────────────┘
```

The **Agent Core Layer** is the part missing from most "LLM security" checklists,
and it is where the highest-severity agent-specific findings concentrate.

---

## Standards alignment

The taxonomy is mapped to, rather than replacing, the major standards:

- **OWASP Top 10 for LLM Applications (2025)** — LLM01 Prompt Injection … LLM10 Unbounded Consumption
- **OWASP Agentic AI — Threats & Mitigations (T1–T15)** — memory poisoning, tool misuse, privilege compromise, multi-agent threats
- **MITRE ATLAS** — adversarial ML tactics & techniques
- **CWE** — concrete weakness mapping (e.g. CWE-441 Confused Deputy, CWE-770 Unbounded Resources)
- **GB/T 45654-2025** — generative AI service security (network-security national standard)
- **GB/T 45656-2025** — labeling of AI-generated / synthetic content

Each test case carries its standard reference inline, so a finding can be traced
straight to OWASP / CWE / ATLAS for the client report.

---

## Specialized testing dimensions

Beyond the flat catalog, nine deep-dive modules expand the highest-risk areas.
These are where the framework goes past generic checklists:

| Module | Focus | Notable / less-common coverage |
|---|---|---|
| **Prompt Injection & Jailbreak** | Direct, indirect, multimodal | Policy Puppetry, Skeleton Key, ASCII/Unicode-tag smuggling, Best-of-N, agentic self-jailbreak |
| **MCP Tool Poisoning** | Model Context Protocol attack surface | Rug-pull, shadow tools, OAuth/PKCE abuse, Streamable-HTTP transport, sampling/elicitation reverse-abuse |
| **RAG Security** | Retrieval pipeline | Embedding-space attacks, chunk-boundary injection, citation spoofing, semantic-cache pollution |
| **Agent Sandbox & Code Execution** | Code-interpreter isolation | Container escape (gVisor/Firecracker), syscall-allowlist bypass, GPU/CUDA boundary, init race conditions |
| **Multi-Tenancy & Memory Poisoning** | Cross-tenant integrity | Memory-store cross-tenant reads, cache-layer isolation, persistent poisoning |
| **Skill / Plugin Security** | Agent skills & marketplaces | Ghost instructions in skill manifests, conditional backdoors, dependency confusion, HITL bypass |
| **Multi-Agent Collaboration** | A2A / orchestration | Orchestrator confused-deputy, message-bus poisoning, cascading hallucination, AgentCard spoofing, collusive exfiltration |
| **Unbounded Consumption & Denial-of-Wallet** | Cost & resource | Recursive tool-call explosion, token amplification, economic DoS |
| **Synthetic-Content Labeling** | Compliance | Explicit/implicit watermark integrity, robustness, label stripping, cross-modal consistency |

The **Multi-Agent Collaboration** module deserves special mention: as deployments
move from a single agent to orchestrated fleets (AutoGen, CrewAI, LangGraph, A2A),
the trust boundary moves *between* agents. An orchestrator running with aggregated
privileges becomes a new kind of confused deputy — a high-severity class that
single-agent test suites cannot detect.

---

## Severity & execution model

- **Severity:** Critical / High / Medium / Low (CVSS-aligned).
- **Execution method** is recorded per case across automated and manual paths —
  scanner-based, jailbreak/red-team frameworks (e.g. Garak, Promptfoo, PyRIT),
  conventional pentest tooling, and structured manual probing. Agent-core findings
  (confused deputy, cross-agent trust) remain the most manual and the most
  productive.

---

## Repository contents

| File | What it is |
|---|---|
| [`README.md`](./README.md) | This writeup |
| [`docs/TAXONOMY.md`](./docs/TAXONOMY.md) | Full 8×3 matrix, domain definitions, layer definitions |
| [`docs/TEST-CATALOG.md`](./docs/TEST-CATALOG.md) | English catalog of the AI-security test cases (titles, domain, layer, severity, standard) |

> **Scope note.** This public writeup publishes the *framework, taxonomy, and case
> catalog*. Detailed step-by-step exploitation procedures from the full commercial
> library are intentionally not included here.

---

## Status

This is an actively maintained framework used for enterprise AI-agent security
assessments. Contributions, corrections, and standard-mapping suggestions are
welcome via issues and pull requests.

## Author

**AA42vecks1n**

## License

Licensed under the **Apache License, Version 2.0**. See [`LICENSE`](./LICENSE).

```
Copyright 2026 AA42vecks1n

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0
```

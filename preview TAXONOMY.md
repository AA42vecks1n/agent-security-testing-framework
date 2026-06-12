# Taxonomy — Risk Domains × Architecture Layers

Every AI-security test case is classified by **one risk domain** and **one
architecture layer**. This document defines both axes and gives the case
distribution.

## Architecture layers

| Layer | What lives here | Representative threats |
|---|---|---|
| **AI Application Layer** | User-facing surface: prompts, dialogue, output rendering, application APIs | Prompt injection, jailbreak, harmful content, sensitive-info leakage in output |
| **Agent Core Layer** | The agent's "nervous system": tool calling, MCP, RAG, memory, orchestration, code execution | MCP poisoning, RAG poisoning, memory poisoning, sandbox escape, multi-agent trust, observability gaps |
| **AI Infrastructure Layer** | Model serving, containers, GPU, storage, network, multi-tenancy | Unsafe model loading, supply-chain poisoning, tenant isolation, transit encryption, cache flaws |

## Risk domains

### Model-Intrinsic Risks
Risks rooted in the model's own behavior and reasoning. Prompt injection (direct /
indirect / multimodal), jailbreak, reward hacking, hallucination / factuality
failure, model backdoors, on-device model extraction & reversing, MCP tool
poisoning, RAG poisoning & source hijacking, memory poisoning, training-data
backdoors.

### Agent System Risks
Risks in the agent's software/system stack rather than the model weights.
Agent-framework vulnerabilities, AI-framework component flaws, insecure sandboxes,
unsafe model loading, supply-chain poisoning, compute-environment and
critical-platform vulnerabilities, hardware flaws.

### Data Security Risks
Confidentiality and integrity of data the agent touches. System-prompt leakage,
multi-tenant isolation failure, membership inference, insecure storage, cache-layer
flaws, improper transit encryption, memory-data leakage, insider exfiltration,
privacy and data-minimization failures.

### Content, Abuse & Compliance Risks
Output-level harm and misuse. Harmful content generation, synthetic-content risks,
malicious abuse, loss of behavioral control.

### Observability Risks
Gaps in the ability to see and audit what the agent did. Missing or bypassable
behavioral monitoring, audit-trail integrity.

### Runtime Security Risks
Availability and resource integrity at runtime. Resource abuse, denial of service.

### Governance & Compliance Risks
Regulatory and governance boundaries. Cross-border / data-residency violations.

### Traditional Application Risks *(tracked, out of AI-security scope)*
Classic web/infra weaknesses present in the agent's surrounding application: IDOR /
broken access control, SSRF, authentication flaws, session management, file upload,
host-header injection, open redirect, clickjacking, SQL injection.

## Distribution (AI-security subset)

> The traditional-application domain is excluded from the figures below; this is the
> AI-specific portion of the library.

### By risk domain

| Risk domain | Cases |
|---|---:|
| Data Security Risks | 36 |
| Model-Intrinsic Risks | 35 |
| Agent System Risks | 28 |
| Content, Abuse & Compliance Risks | 17 |
| Observability Risks | 8 |
| Governance & Compliance Risks | 3 |
| Runtime Security Risks | 3 |

### By architecture layer (full library)

| Architecture layer | Cases |
|---|---:|
| AI Application Layer | 92 |
| AI Infrastructure Layer | 58 |
| Agent Core Layer | 26 |

Plus **119** cases across the nine specialized deep-dive modules
(see [`TEST-CATALOG.md`](./TEST-CATALOG.md)), which expand individual base rows
into detailed sub-cases.

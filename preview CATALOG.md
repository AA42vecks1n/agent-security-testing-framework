# Test Catalog — Specialized Modules (English)

Case titles and severity for the nine specialized deep-dive modules. Severity:
**Critical / High / Medium / Low**. Detailed exploitation steps are not published
here.

---

## Prompt Injection & Jailbreak

| ID | Technique | Severity |
|---|---|---|
| TC-PI-01 | Direct Injection | High |
| TC-PI-02 | Indirect Injection (via document) | High |
| TC-PI-03 | Multimodal Injection | High |
| TC-PI-04 | Classic Jailbreak Templates | High |
| TC-PI-05 | Crescendo (progressive) Attack | High |
| TC-PI-06 | Many-Shot Jailbreaking | High |
| TC-PI-07 | Encoding Bypass | High |
| TC-PI-08 | Language Mixing | Medium |
| TC-PI-09 | Automated Attacks (GCG / PAIR / TAP) | High |
| TC-PI-10 | Role-Play Jailbreak | High |
| TC-PI-11 | Prompt-Template Leakage | High |
| TC-PI-12 | Token Smuggling | High |
| TC-PI-13 | Context Overflow | Medium |
| TC-PI-14 | Morality Inversion | High |
| TC-PI-15 | Tool-Use Hijacking | High |
| TC-PI-16 | Policy Puppetry | High |
| TC-PI-17 | Skeleton Key (progressive policy erosion) | High |
| TC-PI-18 | ASCII Smuggling / Unicode-Tag Hidden Injection | High |
| TC-PI-19 | Best-of-N Jailbreak | Medium |
| TC-PI-20 | Multimodal Jailbreak (image / audio embedded instructions) | High |
| TC-PI-21 | Agentic Self-Jailbreak (via planning) | High |
| TC-PI-22 | Crescendo + Translation-Converter Chain | High |

## MCP Tool Poisoning

| ID | Technique | Severity |
|---|---|---|
| TC-MCP-01 | Tool Description Injection | High |
| TC-MCP-02 | Rug Pull Attack | High |
| TC-MCP-03 | Shadow Tool (same-name override) | High |
| TC-MCP-04 | Parameter Injection via Tool Response | High |
| TC-MCP-05 | Cross-Tool Data Exfiltration | High |
| TC-MCP-06 | MCP Server Impersonation | High |
| TC-MCP-07 | Tool-Chain Confused Deputy | High |
| TC-MCP-08 | MCP Auth Bypass | High |
| TC-MCP-09 | Supply-Chain Poisoning (MCP package) | High |
| TC-MCP-10 | Tool Parameter-Schema Poisoning | Medium |
| TC-MCP-11 | Capability Escalation via Prompt | High |
| TC-MCP-12 | Unencrypted MCP Channel | High |
| TC-MCP-13 | MCP Auth / OAuth Flow Abuse | High |
| TC-MCP-14 | Streamable-HTTP / SSE Transport Hijack | High |
| TC-MCP-15 | Tool-Chaining Privilege Escalation | High |
| TC-MCP-16 | Sampling / Elicitation Reverse-Abuse | High |

## RAG Security

| ID | Technique | Severity |
|---|---|---|
| TC-RAG-01 | Direct Document Poisoning | High |
| TC-RAG-02 | Embedding-Space Attack | High |
| TC-RAG-03 | Cross-Tenant Retrieval | High |
| TC-RAG-04 | Chunk-Boundary Injection | High |
| TC-RAG-05 | Metadata Manipulation | Medium |
| TC-RAG-06 | Citation Spoofing | Medium |
| TC-RAG-07 | Retrieval Denial of Service | Medium |
| TC-RAG-08 | Vector Collision | Medium |
| TC-RAG-09 | RAG Prompt-Template Injection | High |
| TC-RAG-10 | Knowledge-Base Permission Bypass | High |
| TC-RAG-11 | Persistent Poisoning | High |
| TC-RAG-12 | Semantic-Cache Pollution | Medium |

## Agent Sandbox & Code Execution

| ID | Technique | Severity |
|---|---|---|
| TC-SBX-01 | Python Code-Interpreter Escape | High |
| TC-SBX-02 | Container Escape (Docker / gVisor / Firecracker) | High |
| TC-SBX-03 | Filesystem Out-of-Bounds Access | High |
| TC-SBX-04 | Network-Egress Control Bypass | High |
| TC-SBX-05 | Process Creation & Resource Exhaustion | Medium |
| TC-SBX-06 | Environment-Variable & Credential Leakage | High |
| TC-SBX-07 | Python eval/exec Sandbox Bypass | High |
| TC-SBX-08 | GPU / CUDA Resource Boundary | Medium |
| TC-SBX-09 | Syscall-Allowlist Bypass | High |
| TC-SBX-10 | Sandbox Initialization Race | Medium |

## Multi-Tenancy & Memory Poisoning

| ID | Technique | Severity |
|---|---|---|
| TC-MT-01 | Session Isolation Bypass | High |
| TC-MT-02 | Memory-Store Cross-Tenant Access | High |
| TC-MT-03 | RAG Knowledge-Base Isolation | High |
| TC-MT-04 | Model-Instance Isolation | Medium |
| TC-MT-05 | Cache-Layer Isolation | Medium |
| TC-MT-06 | Memory-Pollution Attack | High |
| TC-MT-07 | Resource-Quota Bypass | Medium |
| TC-MT-08 | Tenant-Metadata Manipulation | Medium |
| TC-MT-09 | Shared Agent-Configuration Leak | High |
| TC-MT-10 | Log & Monitoring Isolation | Medium |

## Skill / Plugin Security

| ID | Technique | Severity |
|---|---|---|
| TC-SK-01 | Skill Description Injection | High |
| TC-SK-02 | Skill Metadata Poisoning | High |
| TC-SK-03 | Skill Rug Pull (version swap) | High |
| TC-SK-04 | Trigger-Keyword Hijacking | Medium |
| TC-SK-05 | Ghost Instruction in Skill Manifest | High |
| TC-SK-06 | Conditional Backdoor | High |
| TC-SK-07 | Obfuscated-Code Backdoor | High |
| TC-SK-08 | Dependency Confusion | High |
| TC-SK-09 | Excessive Permission Declaration | Medium |
| TC-SK-10 | Path Traversal via system.run | High |
| TC-SK-11 | Unauthorized Network Egress | High |
| TC-SK-12 | Unauthorized Action without HITL | High |
| TC-SK-13 | Marketplace Typosquatting | High |
| TC-SK-14 | Integrity-Verification Bypass | High |
| TC-SK-15 | Third-Party Permission Scope Creep | Medium |
| TC-SK-16 | Embedded Tracking | High |
| TC-SK-17 | Cross-Session Data Leakage | High |
| TC-SK-18 | Skill Output Injection | High |
| TC-SK-19 | Credential Exposure in Output | High |
| TC-SK-20 | Report Tampering | Medium |
| TC-SK-21 | Prompt-Injection Resistance | High |
| TC-SK-22 | Tool-Call Command Injection | High |
| TC-SK-23 | Audit-Log Integrity | Medium |
| TC-SK-24 | Isolation Between Concurrent Executions | Medium |

## Multi-Agent Collaboration Security

| ID | Technique | Severity |
|---|---|---|
| TC-MA-01 | Inter-Agent Trust-Boundary Bypass | High |
| TC-MA-02 | Orchestrator Confused Deputy | **Critical** |
| TC-MA-03 | Message-Bus / Blackboard Poisoning | High |
| TC-MA-04 | Cascading Hallucination | High |
| TC-MA-05 | A2A Identity Spoofing / AgentCard Forgery | High |
| TC-MA-06 | Sub-Agent Return Injection | High |
| TC-MA-07 | Cross-Agent Privilege Escalation | **Critical** |
| TC-MA-08 | Orchestration Loop / Token Explosion | Medium |
| TC-MA-09 | Overwhelming Human-in-the-Loop | Medium |
| TC-MA-10 | Collusive Data Exfiltration | High |
| TC-MA-11 | Shared-Tool Race / State Pollution | Medium |
| TC-MA-12 | Orchestration-Routing Tampering | High |

## Unbounded Consumption & Denial-of-Wallet

| ID | Technique | Severity |
|---|---|---|
| TC-RC-01 | Recursive Tool-Call Explosion | High |
| TC-RC-02 | Token Amplification | Medium |
| TC-RC-03 | Denial-of-Wallet | High |
| TC-RC-04 | Context-Window Flooding | Medium |
| TC-RC-05 | Embedding Flood | Medium |
| TC-RC-06 | Session & Memory Exhaustion | Medium |
| TC-RC-07 | Non-Terminating Task | Medium |
| TC-RC-08 | Missing Rate-Limit / Quota | High |

## Synthetic-Content Labeling & Compliance

| ID | Technique | Severity |
|---|---|---|
| TC-ID-01 | Explicit-Label Integrity | High |
| TC-ID-02 | Implicit Watermark / Metadata Presence | Medium |
| TC-ID-03 | Watermark Robustness | Medium |
| TC-ID-04 | Label Stripping / Bypass | High |
| TC-ID-05 | Cross-Modal Label Consistency | Medium |

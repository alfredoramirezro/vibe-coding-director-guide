# Design Doc: IVC-OS Director Field Guide & Leadership Operating Method
> **Date:** 2026-09-11  
> **Status:** Approved / Completed  
> **Target:** Platform Directors, Lead Architects, and SaaS Operators for Intelligent Vibe Coding Platforms (`IVC-OS`)

---

## 1. Context & Motivation
The IVC-OS repository contains a 459-page architectural transcript (`chatgpt.com-Intelligent Vibe Coding Operating System.pdf`) defining a multi-agent system (13 phases, 30 agent dimensions, RAG cognitive infrastructure, execution sandbox, monorepo architecture, and a 36-atomic-prompt pack).

However, a critical gap was identified: the document specifies the *software* and *agent-to-agent contracts*, but lacks a formal **Operating Method for the Human Director/Leader** who operates and governs the vibe coding platform. Without a structured leadership method, AI-assisted development suffers from severe anti-patterns:
- *Prompt-and-Pray:* issuing vague prompts and accepting code blindly without tests or contracts.
- *Synthetic Proof Hallucination:* inventing fake social proof, fictional user metrics, and stock testimonials on day-0 landing pages.
- *The Self-Approval Trap:* trusting the code-generating agent to review and approve its own code.
- *Context Rot & Amnesia:* overwhelming the context window with unparsed logs.
- *Runaway Tokenomics & Infinite Debugging Loops:* agents burning compute without progress.

---

## 2. Architectural Design & Deliverable
The resulting deliverable is the **IVC-OS Director's Field Guide** (`IVC_OS_GUIA_DE_CAMPO_DIRECTOR.md`), designed following the proven, battle-tested operational format of `vibecoder-skills`:

### 2.1 Three-Layer Triad
1. **Layer I: Strategic Direction & Intent Governance (CPO / Founder):**
   - Protocol 1.1: Intent Framing & Negative Boundary Setting (defining what NOT to build).
   - Protocol 1.2: Tokenomics Budgeting & 80% Burn Rate Early Warning.
   - Protocol 1.3: Intellectual Property & Licensing Shield (whitelisting MIT/Apache 2.0; blocking GPL/AGPL).
   - Protocol 1.4: Anti-Feature Creep & Ruthless YAGNI.

2. **Layer II: Technical Engineering & Operational Hardening Triad (Lead Architect):**
   - **Spec-Driven Development (SDD):** Freezing Zod/Pydantic schemas and OpenAPI contracts before any implementation code is authored.
   - **Context Engineering:** Structured memory (`PROJECT_SPEC.md`, `CONTEXT.md`, `SESSION_PRIMER.md`) and active context pruning.
   - **Harness Engineering:** Confinement in ephemeral Docker sandboxes with strict outbound network egress guardrails and deterministic mocks.
   - **Veracity & Anti-Slop (The 7 Golden Rules):** Zero fabricated proof, Proof of Mechanism over fake social proof, empty-state first, zero placeholders (`// TODO`), zero dead-ends (`href="#"`), the Benefit Test, and pre-flight veracity audits.
   - **Agentic TDD & Verification Before Completion:** Red-Green-Refactor with mandatory literal CLI terminal test output.
   - **Doubt-Driven Development & Adversarial Review:** Strict No-Self-Approval rule, clean-context reviewer agents, and micro-diffs capped at 150-200 lines.

3. **Layer III: SaaS Platform Operations & Disposable Fleet Governance (Platform Operator):**
   - Protocol 3.1: Strict Multi-Tenant Boundary Isolation with PostgreSQL Row-Level Security (RLS) and tenant-scoped `pgvector` collections.
   - Protocol 3.2: Disposable Agent Fleet Pattern (agents are single-use disposable workers; repos and contracts are permanent).
   - Protocol 3.3: Risk-Tiered Tool Gateway (Tier 0 local read to Tier 3 production/destructive requiring mandatory 2FA human sign-off).
   - Protocol 3.4: Distributed Observability (OpenTelemetry `TraceId` linking intent -> spec -> agents -> tool calls -> commits).

4. **Emergency Runbook & Lethal Anti-Patterns:**
   - Cold shutdown, hard git rollback (`git reset --hard HEAD`), and memory purge for architectural drift.
   - Immediate container pause, secret rotation, and Semgrep static analysis for sandbox egress violations.
   - 3-strike circuit breaker and root-cause analyzer invocation for infinite debug loops.

5. **Binary Decision Matrix (Hard Gates 1 to 6):**
   - Non-negotiable Go / No-Go evaluation criteria covering Spec, Veracity, Test Harness, Diff Size, Adversarial Review, and Hardening.

---

## 3. File Map
- Document: `C:\.Proyectos\Vibecoder\IVC-OS\IVC_OS_GUIA_DE_CAMPO_DIRECTOR.md`
- Design Specification: `C:\.Proyectos\Vibecoder\docs\superpowers\specs\2026-09-11-ivc-os-director-field-guide-design.md`
- Foundation Context: `C:\.Proyectos\Vibecoder\IVC-OS\chatgpt.com-Intelligent Vibe Coding Operating System.pdf`
- Reference Precedent: `C:\.Proyectos\Vibecoder\vibecoder-skills\vibecoder-skills\README.md`

---

## 4. Next Milestone
With the Director's Field Guide established, the project is cleared for **Phase 2: IVC-OS Web App Architecture & Implementation Planning**, which will translate these human-in-the-loop workflows, hard gates, and fleet controls into an interactive, accessible, zero-popup web application.

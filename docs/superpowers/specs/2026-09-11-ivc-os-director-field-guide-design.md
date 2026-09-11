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

4. **Layer IV: Specialized Operational Runbooks (The Director's Battle-Tested Procedures):**
   - Protocol 7.1: The 5-layer "Bug-Sweep" for mature projects (Invariants/Types, Concurrency/Async, Routes, Fuzzing, Secrets -> `BUG_REGISTRY.md`).
   - Protocol 7.2: "Are We Ready to Launch?" 10-Dimension Go-Live Audit (Security, Resilience/404/500, SEO/OG, a11y, Performance/LCP, Legal, Telemetry, Migrations, Responsiveness, Critical User Journey).
   - Protocol 7.3: Graceful Payment Staging & Frictionless Beta Checkout (testing traction and intent without live payment credentials).
   - Protocol 7.4: 16:9 Slide Decks in standalone HTML (Syne + JetBrains Mono; Investor Pitch Deck 10 slides & Founding Customer Cohort 6 slides).
   - Protocol 7.5: SaaS RBAC Multi-Role Governance (Superadmin `/superadmin` with audited impersonation, Tenant Admin, End User).

5. **Layer V: Sensorial Design, Human Language, Global Accessibility & GEO/SEO Optimization:**
   - Protocol 8.1: Bespoke Inline SVG Illustrations & Zero Stock Imagery (no external hotlinks).
   - Protocol 8.2: Plain Language for Target Market (clean Mexican/Hispanic Spanish, minimal acronyms, preserving only essential industry terms).
   - Protocol 8.3: Zero Sales Friction UX (self-explanatory interface, guided 3-step `/como-funciona`, `/glosario` subpage).
   - Protocol 8.4: International Accessibility & Inclusivity (WCAG 2.1/2.2 AA/AAA, >4.5:1 / 7:1 contrast, 100% keyboard navigation, ADHD/Dyslexia motion-reduction, Zero-Popup mandate).
   - Protocol 8.5: Post-Launch Discovery & Indexing (SEO technical hierarchy, SEM conversion landing parity, GEO optimization via `llms.txt`, `llms-full.txt`, `ai.txt` and Schema.org JSON-LD).

6. **Layer VI: Data Sovereignty, Live Operations & Developer Maintainability:**
   - Protocol 9.1: Zero-Training Contractual Shield (`data_retention: 0`, `X-No-Train: true`).
   - Protocol 9.2: Global Agent Kill-Switch (sub-500ms emergency pause, token revocation, read-only maintenance mode).
   - Protocol 9.3: Zero-Downtime Database Migrations (Expand, Migrate in background, Contract).
   - Protocol 9.4: Feature Flags & Dark Launching (Superadmin -> Founding Cohort -> General Availability).
   - Protocol 9.5: Zero Vendor Lock-in 1-Click .ZIP Data Export (code, schemas, specs, SVG assets).
   - Protocol 9.6: Silent Watchdog Bot to Telegram/Discord (alerts on 500 errors, new checkouts, 80% token burn, agent circuit breaker).
   - Protocol 9.7: Local-First Auto-Draft Resilience (`localStorage`/`IndexedDB` auto-restore on closed tabs/network flickers).
   - Protocol 9.8: Shadow Mode Model Evaluation (10% traffic blind testing before model migration).
   - Protocol 9.9: Living Documentation, Strict Anti-God-Files (<250-300 lines per file), and Immutable Bidirectional Spec Synchronization (Zero Spec Drift, 2-minute comprehension test).
   - Protocol 9.10: Account Deletion with Statutory Tax Hold (PII dissociation & soft-delete + 5-year immutable fiscal ledger retention for tax audits).

7. **Emergency Runbook & Lethal Anti-Patterns:**
   - Cold shutdown, hard git rollback (`git reset --hard HEAD`), and memory purge for architectural drift.
   - Immediate container pause, secret rotation, and Semgrep static analysis for sandbox egress violations.
   - 3-strike circuit breaker and root-cause analyzer invocation for infinite debug loops.

8. **Binary Decision Matrix (Hard Gates 1 to 6):**
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

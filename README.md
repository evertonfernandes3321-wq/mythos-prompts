<div align="center">

# 🜂 Mythos Prompts

**English** · [Português (pt-BR)](./README.pt-BR.md)

### **44 engineering superprompts** in pure markdown — _Mythos_ tier

Paste into any LLM (Claude · ChatGPT · Gemini · …) and point it at your code/context.

**Sub-atomic rigor · Stack-agnostic · Defensive · Fixed output format**

![Stars](https://img.shields.io/github/stars/evertonfernandes3321-wq/mythos-prompts?style=social)
[![License: MIT](https://img.shields.io/github/license/evertonfernandes3321-wq/mythos-prompts)](./LICENSE)
![Release](https://img.shields.io/github/v/release/evertonfernandes3321-wq/mythos-prompts)
![Last commit](https://img.shields.io/github/last-commit/evertonfernandes3321-wq/mythos-prompts)
![Prompts](https://img.shields.io/badge/prompts-44-6366f1)
![Stack](https://img.shields.io/badge/stack-agnostic-0ea5e9.svg)

</div>

> ⭐ If this saves you time, a star helps others find it.

---

## What this is

Every `.md` file is a ready-to-use **operational superprompt**. The content is identical to the skills in the sibling repo [**mythos-skills**](https://github.com/evertonfernandes3321-wq/mythos-skills) — here, stripped of the skill frontmatter so you can **copy and paste** into any AI assistant.

What makes them **Mythos tier**:

- **Sub-atomic rigor** — happy path _and_ error path, edge cases, defaults, concurrency, roles, and environments.
- **Stack-agnostic** — they work in any language/framework, with parallel examples (JS/TS, Python, Go, Java/Kotlin, C#/.NET, Ruby, PHP, Rust, mobile; Postgres/MySQL/Mongo; Stripe/Square; PostHog/Mixpanel…). Two are specialized in **Flutter**.
- **Empirical verification** — validate via non-falsifiable output (hash/count/exit-code), never "looks like it worked."
- **Defensive** — sensitive topics are strictly defensive/authorized; secrets are always masked.
- **Fixed output format** — executive summary → findings with location + fix + test → table → phased plan → final checklist.

> 🌐 **Language note:** Skill bodies/prompts are written in PT-BR (Portuguese); names, README, and structure are English. PRs translating bodies to EN welcome.

## How to use

1. Open the `.md` for your goal.
2. Copy the **entire** contents.
3. Paste it into your AI assistant, attaching or pointing it at the code/context to analyze.

> 🧩 Want them as **native Claude Code skills** (automatic discovery and routing, with `references/assets/scripts`)? Use the sibling repo [**mythos-skills**](https://github.com/evertonfernandes3321-wq/mythos-skills).

> ⚡ **Run them all at once:** the sibling repo ships a **[RUN-ALL.md](https://github.com/evertonfernandes3321-wq/mythos-skills/blob/main/RUN-ALL.md)** playbook — run every skill against a single repository and get **one report per skill**. See **[examples/](https://github.com/evertonfernandes3321-wq/mythos-skills/tree/main/examples)** for a sample report.

---

## Table of contents

| Category | Prompts |
|-----------|---------|
| [🔒 Security](#-security) | 9 |
| [🗄️ Database & Data](#️-database--data) | 4 |
| [📊 Observability & Operations](#-observability--operations) | 5 |
| [⚙️ Operational Rigor & Coordination](#️-operational-rigor--coordination) | 4 |
| [🐛 Debugging, Testing & Quality](#-debugging-testing--quality) | 8 |
| [🎨 Frontend & UI Architecture](#-frontend--ui-architecture) | 4 |
| [🔌 Integrations, Billing & Privacy](#-integrations-billing--privacy) | 3 |
| [🏗️ Process, Design & Documentation](#️-process-design--documentation) | 4 |
| [📱 Mobile / Flutter](#-mobile--flutter) | 2 |
| [💼 Business](#-business) | 1 |

🏅 = **master** prompt (the most comprehensive in its category).

---

## 🔒 Security

### [`security-audit-full`](./security-audit-full.md) 🏅
**End-to-end** defensive security audit at the sub-atomic level.
**When to use:** authorized defensive pentest, pre-deploy review, or comprehensive hardening.
**Covers:** auth · authorization/IDOR · injections · XSS · SSRF · CSRF · uploads · secrets · crypto · supply chain · CI/CD · cloud/IaC · privacy · business logic · concurrency · AI/LLM.

### [`auth-authorization-audit`](./auth-authorization-audit.md)
Authentication and authorization, with a **permission matrix** by resource/role.
**When to use:** validate who can do what; find unprotected routes and missing checks.
**Covers:** tokens/session/JWT (signature, expiration, revocation, logout, inactivity) · RBAC/ABAC · IDOR/BOLA · multi-tenant isolation · admin endpoints · least privilege · identity never trusted from the client.

### [`auth-token-refresh-safety`](./auth-token-refresh-safety.md)
Refresh token rotation that is **safe under concurrency** (the mechanism, not RBAC).
**When to use:** implementing/reviewing persistent login on mobile/SPA.
**Covers:** single-flight mutex · anti-loop flag on 401 · PUBLIC_PATHS · reactive 401 interceptor · error taxonomy · backend rotation.

### [`secrets-and-config-exposure-audit`](./secrets-and-config-exposure-audit.md)
Hunt for exposed secrets and configuration before publishing/deploying.
**When to use:** before making a repo public or before a deploy.
**Covers:** hardcoded keys/tokens/credentials (client and server) · internal endpoints leaked in the frontend · committed `.gitignore`/`.env` · migration to env vars and secret managers · config validation at startup.

### [`injection-xss-csrf-audit`](./injection-xss-csrf-audit.md)
Classic web vulnerabilities with concrete, ecosystem-specific fixes.
**When to use:** reviewing user input, templates, forms, and headers.
**Covers:** injections (SQL/NoSQL/OS/template) · **context-aware** escaping (HTML/attribute/URL/JS/CSS) · CSRF tokens · backend validation · headers (CSP, X-Frame-Options, HSTS).

### [`file-upload-security-audit`](./file-upload-security-audit.md)
File upload and handling security, end to end.
**When to use:** any endpoint that accepts files.
**Covers:** real MIME + extension (allowlist) · magic bytes · limits · sanitization against path traversal · private storage · blocking executables/SVG-script/polyglots/zip-bombs · signed URLs · sandbox · per-tenant isolation.

### [`password-credential-security`](./password-credential-security.md)
Passwords and credentials with hash migration **without breaking logins**.
**When to use:** you've detected plaintext/weak hashes, or you're hardening authentication.
**Covers:** detecting MD5/SHA1/raw-SHA256 · salt/pepper · Argon2id/bcrypt/scrypt with cost factor · zero-knowledge · constant-time comparison · secure reset · transparent re-hash on next login.

### [`production-readiness-audit`](./production-readiness-audit.md)
DevSecOps production-readiness audit (go/no-go).
**When to use:** before the final release/deploy.
**Covers:** vulnerable dependencies/CVEs (npm/pip/go/maven/cargo/composer/bundler) · hunt for _leftovers_ (test routes, mocks, fake data, hardcoded credentials, auth bypass) · removal plan + safe upgrade + go/no-go checklist.

### [`https-security-headers-audit`](./https-security-headers-audit.md)
Secure transport (HTTPS/TLS) and the complete suite of **security headers**.
**When to use:** ensure nothing travels in the clear and block protocol downgrade.
**Covers:** mixed content (scripts/images/API/websocket over HTTP) · forced 301 redirect HTTP→HTTPS · HSTS (includeSubDomains/preload) · CSP (nonce/hash, upgrade-insecure-requests) · X-Frame-Options/frame-ancestors · X-Content-Type-Options · Referrer-Policy · Permissions-Policy · Secure/HttpOnly/SameSite cookies · TLS 1.2+ anti-downgrade · config for Nginx/Apache/Caddy/IIS/Traefik/CDN/framework · `curl -I`/Observatory validation.

---

## 🗄️ Database & Data

### [`database-tenant-isolation-audit`](./database-tenant-isolation-audit.md) 🏅
Guarantees that **one tenant never sees another's data**.
**When to use:** multi-tenant SaaS; reviewing RLS/isolation.
**Covers:** RLS vs schema-per-tenant and trade-offs · tenant context propagation · FORCE RLS · matrix testing (users × tables × operations) · leak detection (views/triggers/SECURITY DEFINER/service-role) · least privilege.

### [`database-performance-audit`](./database-performance-audit.md)
Database and data-access-layer performance.
**When to use:** the bottleneck is the query, the ORM, an inline policy, or data access.
**Covers:** slow RLS (per-row auth-function → cache/SELECT/helpers/indexes) · N+1 and batching (DataLoader) · missing indexes (FK without index, full scan) · EXPLAIN/ANALYZE · keyset/cursor pagination · pooling · transactions.

### [`data-integrity-and-ledger-audit`](./data-integrity-and-ledger-audit.md)
Invariants and ledger for **critical-state** systems.
**When to use:** before/after touching balances; PR, incident, or audit (finance, wallet, escrow, inventory, credits).
**Covers:** Golden Formula (SUM=constant) · ledger closure and per-entry closure · balance-cache coherence · double-entry · atomic transactions with meta-validation · money never in float · append-only with reversals · reconciliation · forensic snapshots (SHA-256).

### [`cache-and-server-state-architecture`](./cache-and-server-state-architecture.md)
Cache and server-state coherence, from the client to the database.
**When to use:** stale data, sync bugs, inconsistent invalidation.
**Covers:** query key factory · invalidation by tags/entities · optimistic update with rollback · flush→refresh→invalidate after trigger-generated columns · React Query/RTK/SWR/Apollo/Riverpod + Hibernate/Prisma/SQLAlchemy/EF + Redis/CDN/HTTP.

---

## 📊 Observability & Operations

### [`observability-logging-audit`](./observability-logging-audit.md) 🏅
Makes the system **debuggable, auditable, and secure** in production.
**When to use:** poor logs, silent failures, hard-to-diagnose incidents.
**Covers:** structured JSON logs · requestId/traceId correlation · elimination of silent failures · redaction/masking · log levels · metrics · tracing · health checks · alerts.

### [`production-monitoring-standards`](./production-monitoring-standards.md)
**Rules for building** monitorable systems (designing, not auditing).
**When to use:** when designing or hardening the operability of a service.
**Covers:** request ID · stack trace with context · JSON logs · health checks · query/cache tracking · performance metrics · regression tests · alerts · deploy with automatic rollback.

### [`error-handling-audit`](./error-handling-audit.md)
Error handling and failure UX, frontend and backend.
**When to use:** swallowed errors, app freezes with no feedback, empty `catch`.
**Covers:** unhandled async operations · silent failures · loss of stack/cause · error/retry/fallback states · error boundaries · global handlers · expected vs unexpected errors.

### [`product-analytics-architecture`](./product-analytics-architecture.md)
Event-driven **product** analytics (distinct from logging).
**When to use:** measure activation, retention, and conversion.
**Covers:** event catalog as constants · instrumentation with first-ever detection (funnel) · auto-tracking via route observer · privacy-first init with toggle · PostHog/Mixpanel/Amplitude.

### [`backup-disaster-recovery-audit`](./backup-disaster-recovery-audit.md)
Data resilience and **disaster recovery** — before the incident happens.
**When to use:** auditing/building the backup/DR strategy (SRE/DBA lens).
**Covers:** automated backups (dumps, cron/scheduler/K8s CronJob) · 3-2-1 rule with off-site isolation (the app's credential must never be able to delete the backup) · encryption + retention · RPO/RTO · DR plan/runbook · **restore test** (an untested backup is not a backup) · multi-stack scripts (pg_dump/xtrabackup/mongodump/restic → S3/GCS/Azure/B2/R2/MinIO) with hash verification and alerts.

---

## ⚙️ Operational Rigor & Coordination

### [`paranoid-execution-mode`](./paranoid-execution-mode.md) 🏅
Paranoid execution for **irreversible** operations.
**When to use:** touching database/deploy/infra/migration/auth/billing where wrong state causes damage.
**Covers:** non-falsifiable output (hash/count/exit-code) · memory-vs-reality reconciliation · atomic transactions with meta-validation · backup-first + explicit rollback · anti-workaround discipline.

### [`multi-phase-operation-coordination`](./multi-phase-operation-coordination.md)
Complex operations in **phases with mandatory pause points**.
**When to use:** migration/refactor/rollout/deploy/backfill/upgrade where "run it all at once" is dangerous.
**Covers:** executor reports, orchestrator validates before authorizing · waves only with disjoint scope (ALLOWED/FORBIDDEN files) · database never in parallel · state via artifacts (PLAN/SUMMARY/VERIFICATION), resumable.

### [`gotchas-knowledge-transfer`](./gotchas-knowledge-transfer.md)
Turns pitfalls into transferable knowledge.
**When to use:** building and maintaining a lessons-learned base.
**Covers:** template Symptom → Antipattern → Fix → Root Cause → Empirical Validation → Lesson · "gotcha" catalog · severity · transfer across sessions/agents.

### [`pre-ship-smoke-checklist`](./pre-ship-smoke-checklist.md)
Pre/post-deploy smoke test with **nailed-down observable criteria**.
**When to use:** right before and right after shipping something to production.
**Covers:** scenario matrix (T1..Tn) with steps/expected/precondition · commands to force edge cases · post-deploy checklist (build/auth logs, DNS, cert, incognito window) · reproducible report.

---

## 🐛 Debugging, Testing & Quality

### [`ai-code-review`](./ai-code-review.md) 🏅
Rigorous code review of AI code, **explained for non-developers**.
**When to use:** reviewing AI-generated code before production.
**Covers:** security · bugs · architecture · performance · typing · tests · maintainability · scalability · risk-based prioritization · before/after · reviewed code.

### [`scientific-debugging-protocol`](./scientific-debugging-protocol.md)
Scientific debugging — investigate **without jumping to the fix**.
**When to use:** hard, intermittent, or unknown-cause bugs.
**Covers:** gated pipeline (Reproduce → Trace → Propose → Verify → Report) · 5-Whys · data-flow tracing · error classification (UI/API-network/Build) · hypothesis with checkpoint · forensics.

### [`conversational-uat`](./conversational-uat.md)
Conversational UAT with **auto-diagnosis** of failures.
**When to use:** validate features with a non-technical user, without an interrogation.
**Covers:** one test at a time in plain text · automatic root-cause hypothesis · fix plan that re-runs only the gaps · `{phase}-UAT.md` artifact.

### [`test-coverage-audit`](./test-coverage-audit.md)
Finds critical untested areas and proposes the right tests.
**When to use:** prioritize where to test first.
**Covers:** unit, integration, and error cases · risk-based priority (auth, payments, user data, business logic) · behavior focus · the right framework for the project.

### [`e2e-test-architecture`](./e2e-test-architecture.md)
**Resilient** E2E tests (reliability and maintainability).
**When to use:** a _flaky_ or hard-to-maintain E2E suite.
**Covers:** Page Object Model · role/accessibility selectors · resilient waits without fixed timeouts · locator chaining/filtering · state isolation · Playwright/Cypress/Selenium/WebdriverIO/Appium/Detox.

### [`dead-code-elimination`](./dead-code-elimination.md)
**Safe** removal of dead code.
**When to use:** cleaning up the project without breaking anything.
**Covers:** dead components/functions/imports/state/branches · fossilized feature flags · unused deps · cautions (reflection, DI, dynamic entrypoints, public APIs/SDKs, i18n, code splitting) · tools (knip, ts-prune, vulture, cargo-udeps…).

### [`type-safety-audit`](./type-safety-audit.md)
Type safety without overengineering.
**When to use:** too much `any`, external data without validation, loose types.
**Covers:** abuse of `any`/escape hatches · untyped parameters/returns · runtime validation at the boundary (schemas) · types that reflect the domain · TS/Python typing/Go/Java/Kotlin/C#/Rust.

### [`performance-optimization-audit`](./performance-optimization-audit.md)
Performance with **mandatory measurement**.
**When to use:** real slowness, frontend or backend.
**Covers:** re-renders and justified memoization · computation in render · list virtualization · images/bundles · N+1 · pagination/indexes/cache · blocking operations · timeouts.

---

## 🎨 Frontend & UI Architecture

### [`state-management-audit`](./state-management-audit.md) 🏅
UI state in the right place, with no duplication or needless global state.
**When to use:** prop drilling, inconsistent state, context for everything.
**Covers:** prop drilling · state at the wrong level · duplicated/derived · misuse of context/global store · colocation · server-state vs client-state · React/Vue/Svelte/Solid/Angular.

### [`reactive-hooks-audit`](./reactive-hooks-audit.md)
Predictable, testable reactive hooks/primitives.
**When to use:** re-render bugs, stale closures, infinite loops; reviewing custom hooks.
**Covers:** rules of hooks · correct effect dependencies · extraction into hooks/composables · simple state vs reducer/state machine · React/Vue/Svelte/Solid/Angular.

### [`component-architecture-audit`](./component-architecture-audit.md)
Separation between **logic and presentation** (no overengineering).
**When to use:** components that do too much, business rules in the view.
**Covers:** logic leaked into the UI · data-fetching in presentational components · container/presentational vs hooks/composables · refactoring into reusable, testable units.

### [`frontend-design-distinctiveness`](./frontend-design-distinctiveness.md)
Kills visual **"AI slop"** and demands an aesthetic identity.
**When to use:** generic/AI-generated UI; defining an identity before building.
**Covers:** rejects clichés (purple gradient, Inter/Space Grotesk, bento boxes, orbs, centered hero, generic copy) · demands bold typography, an intentional palette, a layout that breaks the grid · anti-pattern checklist.

---

## 🔌 Integrations, Billing & Privacy

### [`third-party-integration-playbook`](./third-party-integration-playbook.md) 🏅
**Robust** integration with external services.
**When to use:** integrating/hardening gateways/SaaS (payments, CRM, analytics, email, messaging).
**Covers:** idempotent webhooks (deterministic id via hash) · retry/replay · event state machine · async fire-and-forget sync that doesn't block the transaction · header-secret webhook auth · typed API client · transactional email by template.

### [`saas-billing-and-quota-enforcement`](./saas-billing-and-quota-enforcement.md)
Billing and **quotas the app can't bypass**.
**When to use:** building/auditing paid plans, usage limits, and trials.
**Covers:** two-tier quota (database + UX) · plan catalog · usage metrics · subscription state machines (trialing/active/past_due/canceled) via scheduled jobs · RLS WITH CHECK, pg_cron, billing_events, Stripe/Asaas.

### [`privacy-consent-lgpd-gdpr-compliance`](./privacy-consent-lgpd-gdpr-compliance.md)
**Operational** privacy compliance (not a vuln scan).
**When to use:** any system with personal data — critical for health/PII and finance.
**Covers:** dual-layer consent (provider + immutable local log) · versioned policies with a blocking gate · _erase_ ceremony (pseudonymization/soft-delete, token revocation) · DSAR within the legal deadline · forensic preservation of the audit trail.

---

## 🏗️ Process, Design & Documentation

### [`architecture-design-blueprint`](./architecture-design-blueprint.md) 🏅
Architecture blueprint via **multi-phase interview with gates**.
**When to use:** designing a new app/service (technical focus).
**Covers:** Phase 1 discovery (goal + scale) · Phase 2 constraints (frontend/backend/data/integration) · Phase 3 synthesis (patterns + performance checklist, template, validation) · layers, contracts, decisions, and proportional trade-offs.

### [`skill-authoring`](./skill-authoring.md)
Meta-prompt: **create and review** high-quality skills.
**When to use:** authoring a new skill, standardizing a family, auditing before publishing.
**Covers:** pattern selector (Tool Wrapper/Pipeline/Generator/Reviewer/Inversion) · correct frontmatter · progressive disclosure with references · Mythos style · testing with fresh context.

### [`doc-coauthoring-reader-testing`](./doc-coauthoring-reader-testing.md)
Doc co-authoring in **3 stages with reader testing**.
**When to use:** specs, RFCs, proposals, design docs, READMEs, ADRs, runbooks.
**Covers:** multi-turn context gathering · section-by-section refinement with incremental edits · reader testing with fresh context (anticipate questions, hunt ambiguity) before publishing.

### [`git-workflow-standards`](./git-workflow-standards.md)
Standardizes commits, branches, and PR/MR operations.
**When to use:** bringing consistency to a team's Git flow.
**Covers:** branch names (feature/fix/hotfix/chore) · Conventional Commits · PR babysitting (CI, fixup, never amend a published commit) · workflow gates · history compliance audit.

---

## 📱 Mobile / Flutter
> Specialized in Flutter, with a **cross-stack principles** section (CSS, React Native, SwiftUI, Compose). _The skill version (sibling repo) ships `references/assets/scripts`._

### [`flutter-overflow-guard`](./flutter-overflow-guard.md)
Prevents, diagnoses, and **proves** the absence of layout overflow.
**When to use:** RenderFlex overflowed, breaking layout, text that doesn't fit, keyboard covering a button.
**Covers:** constraints model · symptom→fix table · Expanded/Flexible/Wrap/SingleChildScrollView/FittedBox · heuristic scanner · multi-device widget-test harness · checklist (multi-size, textScaler, RTL, dark, SafeArea, keyboard) · cross-stack principles.

### [`flutter-pro-polish`](./flutter-pro-polish.md)
Removes the **"Flutter/vibecoding look"** via design tokens.
**When to use:** make the app professional/custom; escape the default Material 3/Roboto/lavender.
**Covers:** _tells_ table · design tokens (color/typography/spacing/radius/elevation/motion) · re-theming default widgets · defaults scanner · designed dark mode · accessibility (AA, ≥48dp) · cross-stack principles.

---

## 💼 Business

### [`business-deep-dive-consultant`](./business-deep-dive-consultant.md)
A senior consultant who runs a **Socratic diagnosis** of your business.
**When to use:** understand the business in depth and find where you make/lose money.
**Covers:** one question at a time with follow-ups · business model, unit economics, funnel, retention, margin, bottlenecks · delivers 3 hidden forces + 3 quantified improvements + 2 high-ROI 30-day actions.

---

## License

[MIT](./LICENSE) © 2026 Everton Fernandes — use, copy, modify, and distribute freely.

## Sibling repository

🧩 [**mythos-skills**](https://github.com/evertonfernandes3321-wq/mythos-skills) — the same 44 as **native Claude Code skills** (with frontmatter, automatic discovery, and `references/assets/scripts`).

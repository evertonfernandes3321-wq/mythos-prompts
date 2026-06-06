# Mythos Prompts — Biblioteca de Superprompts de Engenharia

**42 superprompts** operacionais (auditoria, engenharia, operação, consultoria) em **markdown puro**, prontos para colar em qualquer LLM (Claude, ChatGPT, Gemini, etc.).

Todos em **nível Mythos** (rigor sub-atômico); 40 são **100% agnósticos de stack** e 2 são especializados em **Flutter** (com princípios transferíveis para qualquer UI). São o conteúdo idêntico das skills do repositório irmão **SKILLS** (aqui sem o frontmatter de skill).

Origem: uma biblioteca própria de prompts de engenharia, destilados e generalizados a partir de padrões de produção do mundo real, cobrindo múltiplas stacks.

---

## Como usar
Abra o `.md`, copie tudo e cole no seu assistente de IA, apontando para o código/contexto a analisar.

---

## Catálogo (40)

### 🔒 Segurança
- [`security-audit-full`](./security-audit-full.md) — **Mestre.** Auditoria de segurança defensiva exaustiva end-to-end.
- [`auth-authorization-audit`](./auth-authorization-audit.md) — Autenticação & autorização (IDOR/BOLA, RBAC, multi-tenant).
- [`auth-token-refresh-safety`](./auth-token-refresh-safety.md) — Refresh token rotation seguro (mutex, interceptor 401).
- [`secrets-and-config-exposure-audit`](./secrets-and-config-exposure-audit.md) — Segredos/config, `.env`/`.gitignore`, secret managers.
- [`injection-xss-csrf-audit`](./injection-xss-csrf-audit.md) — Injeções, XSS, CSRF, headers.
- [`file-upload-security-audit`](./file-upload-security-audit.md) — Upload de arquivos (MIME, limites, path traversal).
- [`password-credential-security`](./password-credential-security.md) — Senhas/credenciais (Argon2id/bcrypt).
- [`production-readiness-audit`](./production-readiness-audit.md) — DevSecOps: CVEs + leftovers antes do deploy.

### 🗄️ Banco de Dados & Dados
- [`database-tenant-isolation-audit`](./database-tenant-isolation-audit.md) — Isolamento multi-tenant (RLS/schema), leaks, least privilege.
- [`database-performance-audit`](./database-performance-audit.md) — RLS lenta, N+1/DataLoader, índices, EXPLAIN.
- [`data-integrity-and-ledger-audit`](./data-integrity-and-ledger-audit.md) — Invariantes, double-entry, transações atômicas.
- [`cache-and-server-state-architecture`](./cache-and-server-state-architecture.md) — Coerência de cache client + ORM/DB-side.

### 📊 Observabilidade & Operação
- [`observability-logging-audit`](./observability-logging-audit.md) — **Mestre.** Logging estruturado, correlação, redaction, métricas, tracing.
- [`production-monitoring-standards`](./production-monitoring-standards.md) — Padrões para sistemas monitoráveis.
- [`error-handling-audit`](./error-handling-audit.md) — Tratamento de erros (FE+BE), error boundaries.
- [`product-analytics-architecture`](./product-analytics-architecture.md) — Catálogo de eventos, funil, auto-tracking, privacy-first.

### ⚙️ Rigor Operacional & Coordenação
- [`paranoid-execution-mode`](./paranoid-execution-mode.md) — Gates empíricos, memória-vs-realidade, atômico+rollback.
- [`multi-phase-operation-coordination`](./multi-phase-operation-coordination.md) — Fases com pause points, ondas paralelas, artefatos.
- [`gotchas-knowledge-transfer`](./gotchas-knowledge-transfer.md) — Captura/transferência de armadilhas.
- [`pre-ship-smoke-checklist`](./pre-ship-smoke-checklist.md) — Smoke pré/pós-deploy com critérios observáveis.

### 🐛 Depuração, Testes & Qualidade
- [`ai-code-review`](./ai-code-review.md) — **Mestre.** Code review de código de IA para *vibe coders*.
- [`scientific-debugging-protocol`](./scientific-debugging-protocol.md) — 5-Whys, classificação de erro, hipótese, forensics.
- [`conversational-uat`](./conversational-uat.md) — UAT conversacional com auto-diagnóstico.
- [`test-coverage-audit`](./test-coverage-audit.md) — Cobertura de testes em áreas críticas.
- [`e2e-test-architecture`](./e2e-test-architecture.md) — E2E resiliente (Page Object Model, anti-flakiness).
- [`dead-code-elimination`](./dead-code-elimination.md) — Remoção segura de código morto.
- [`type-safety-audit`](./type-safety-audit.md) — Segurança de tipos (qualquer linguagem tipada).
- [`performance-optimization-audit`](./performance-optimization-audit.md) — Performance frontend + backend.

### 🎨 Frontend & Arquitetura de UI
- [`state-management-audit`](./state-management-audit.md) — Gerenciamento de estado de UI.
- [`reactive-hooks-audit`](./reactive-hooks-audit.md) — Hooks/primitivas reativas (React/Vue/Svelte/Solid/Angular).
- [`component-architecture-audit`](./component-architecture-audit.md) — Separação lógica/apresentação.
- [`frontend-design-distinctiveness`](./frontend-design-distinctiveness.md) — Anti-clichês de design de IA.

### 🔌 Integrações, Billing & Privacidade
- [`third-party-integration-playbook`](./third-party-integration-playbook.md) — Webhooks idempotentes, retry, sync assíncrono.
- [`saas-billing-and-quota-enforcement`](./saas-billing-and-quota-enforcement.md) — Quotas DB+UX, planos, trial/dunning, cron.
- [`privacy-consent-lgpd-gdpr-compliance`](./privacy-consent-lgpd-gdpr-compliance.md) — Consentimento dual-layer, erase, DSAR.

### 🏗️ Processo, Design & Documentação
- [`architecture-design-blueprint`](./architecture-design-blueprint.md) — Blueprint via entrevista multi-fase.
- [`skill-authoring`](./skill-authoring.md) — Meta-skill para autorar skills Mythos.
- [`doc-coauthoring-reader-testing`](./doc-coauthoring-reader-testing.md) — Docs em 3 estágios com reader testing.
- [`git-workflow-standards`](./git-workflow-standards.md) — Convenções de branch/commit/PR.

### 📱 Mobile / Flutter (especializados)
- [`flutter-overflow-guard`](./flutter-overflow-guard.md) — Prevenir/diagnosticar/verificar overflow de layout; + princípios cross-stack (CSS/RN/SwiftUI/Compose).
- [`flutter-pro-polish`](./flutter-pro-polish.md) — Tirar a "cara de Flutter/vibecoding" via design tokens; + princípios cross-stack.

### 💼 Negócios
- [`business-deep-dive-consultant`](./business-deep-dive-consultant.md) — Consultor sócrata + plano de 30 dias.

---

## Princípios
Agnóstico de stack · rigor sub-atômico · verificação empírica (hash/count/exit-code) · defensivo/autorizado · formato de saída fixo (resumo → achados com correção + teste → tabela → plano em fases → checklist). Para usar como skills nativas do Claude Code, veja o repositório irmão **SKILLS**.

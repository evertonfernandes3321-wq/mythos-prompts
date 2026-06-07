<div align="center">

# 🜂 Mythos Prompts

### **44 superprompts** de engenharia em markdown puro — nível _Mythos_

Cole em qualquer LLM (Claude · ChatGPT · Gemini · …) e aponte para o seu código/contexto.

**Rigor sub-atômico · Agnósticos de stack · Defensivos · Formato de saída fixo**

[![License: MIT](https://img.shields.io/badge/License-MIT-22c55e.svg)](./LICENSE)
![Prompts](https://img.shields.io/badge/prompts-44-6366f1.svg)
![Stack](https://img.shields.io/badge/stack-agnóstico-0ea5e9.svg)
![Idioma](https://img.shields.io/badge/idioma-pt--BR-f59e0b.svg)

</div>

---

## O que é isto

Cada arquivo `.md` é um **superprompt operacional** pronto para uso. É o conteúdo idêntico das skills do repositório irmão [**mythos-skills**](https://github.com/evertonfernandes3321-wq/mythos-skills) — aqui sem o frontmatter de skill, para você **copiar e colar** em qualquer assistente de IA.

O que os torna **nível Mythos**:

- **Rigor sub-atômico** — caminho feliz _e_ de erro, edge cases, defaults, concorrência, papéis e ambientes.
- **Agnósticos de stack** — funcionam em qualquer linguagem/framework, com exemplos paralelos (JS/TS, Python, Go, Java/Kotlin, C#/.NET, Ruby, PHP, Rust, mobile; Postgres/MySQL/Mongo; Stripe/Square; PostHog/Mixpanel…). Dois são especializados em **Flutter**.
- **Verificação empírica** — validar por output não-falsificável (hash/count/exit-code), nunca "parece que funcionou".
- **Defensivos** — temas sensíveis são exclusivamente defensivos/autorizados; segredos sempre mascarados.
- **Formato de saída fixo** — resumo executivo → achados com localização + correção + teste → tabela → plano em fases → checklist final.

## Como usar

1. Abra o `.md` do objetivo desejado.
2. Copie **todo** o conteúdo.
3. Cole no seu assistente de IA, anexando ou apontando para o código/contexto a analisar.

> 🧩 Quer usar como **skills nativas do Claude Code** (descoberta e roteamento automáticos, com `references/assets/scripts`)? Use o repositório irmão [**mythos-skills**](https://github.com/evertonfernandes3321-wq/mythos-skills).

---

## Índice

| Categoria | Prompts |
|-----------|---------|
| [🔒 Segurança](#-segurança) | 9 |
| [🗄️ Banco de Dados & Dados](#️-banco-de-dados--dados) | 4 |
| [📊 Observabilidade & Operação](#-observabilidade--operação) | 5 |
| [⚙️ Rigor Operacional & Coordenação](#️-rigor-operacional--coordenação) | 4 |
| [🐛 Depuração, Testes & Qualidade](#-depuração-testes--qualidade) | 8 |
| [🎨 Frontend & Arquitetura de UI](#-frontend--arquitetura-de-ui) | 4 |
| [🔌 Integrações, Billing & Privacidade](#-integrações-billing--privacidade) | 3 |
| [🏗️ Processo, Design & Documentação](#️-processo-design--documentação) | 4 |
| [📱 Mobile / Flutter](#-mobile--flutter) | 2 |
| [💼 Negócios](#-negócios) | 1 |

🏅 = prompt **mestre** (o mais abrangente da categoria).

---

## 🔒 Segurança

### [`security-audit-full`](./security-audit-full.md) 🏅
Auditoria de segurança defensiva **end-to-end**, no nível sub-atômico.
**Quando:** pentest defensivo autorizado, revisão pré-deploy ou hardening abrangente.
**Cobre:** auth · autorização/IDOR · injeções · XSS · SSRF · CSRF · uploads · secrets · cripto · supply chain · CI/CD · cloud/IaC · privacidade · business logic · concorrência · IA/LLM.

### [`auth-authorization-audit`](./auth-authorization-audit.md)
Autenticação e autorização, com **matriz de permissões** por recurso/papel.
**Quando:** validar quem pode fazer o quê; achar rotas desprotegidas e checagens ausentes.
**Cobre:** tokens/sessão/JWT (assinatura, expiração, revogação, logout, inatividade) · RBAC/ABAC · IDOR/BOLA · isolamento multi-tenant · endpoints admin · menor privilégio · identidade nunca confiada do cliente.

### [`auth-token-refresh-safety`](./auth-token-refresh-safety.md)
Refresh token rotation **seguro sob concorrência** (o mecanismo, não o RBAC).
**Quando:** implementar/revisar login persistente em mobile/SPA.
**Cobre:** mutex single-flight · flag anti-loop no 401 · PUBLIC_PATHS · interceptor 401 reativo · taxonomia de erros · rotação no backend.

### [`secrets-and-config-exposure-audit`](./secrets-and-config-exposure-audit.md)
Caça a segredos e configuração exposta antes de publicar/deployar.
**Quando:** antes de tornar um repo público ou de um deploy.
**Cobre:** keys/tokens/credenciais hardcoded (cliente e servidor) · endpoints internos vazados no frontend · `.gitignore`/`.env` versionados · migração para env vars e secret managers · validação de config na inicialização.

### [`injection-xss-csrf-audit`](./injection-xss-csrf-audit.md)
Vulnerabilidades web clássicas com correções concretas por ecossistema.
**Quando:** revisar entrada de usuário, templates, formulários e headers.
**Cobre:** injeções (SQL/NoSQL/OS/template) · escaping **por contexto** (HTML/atributo/URL/JS/CSS) · tokens CSRF · validação no backend · headers (CSP, X-Frame-Options, HSTS).

### [`file-upload-security-audit`](./file-upload-security-audit.md)
Segurança de upload e manipulação de arquivos, ponta a ponta.
**Quando:** qualquer endpoint que recebe arquivos.
**Cobre:** MIME real + extensão (allowlist) · magic bytes · limites · sanitização contra path traversal · storage privado · bloqueio de executáveis/SVG-script/polyglots/zip-bombs · URLs assinadas · sandbox · isolamento por tenant.

### [`password-credential-security`](./password-credential-security.md)
Senhas e credenciais com migração de hashes **sem quebrar logins**.
**Quando:** detectou texto plano/hash fraco, ou vai endurecer autenticação.
**Cobre:** detecção de MD5/SHA1/SHA256-cru · salt/pepper · Argon2id/bcrypt/scrypt com cost factor · zero-knowledge · comparação em tempo constante · reset seguro · re-hash transparente no próximo login.

### [`production-readiness-audit`](./production-readiness-audit.md)
Auditoria DevSecOps de prontidão para produção (go/no-go).
**Quando:** antes do release/deploy final.
**Cobre:** dependências vulneráveis/CVEs (npm/pip/go/maven/cargo/composer/bundler) · caça a _leftovers_ (rotas de teste, mocks, dados fake, credenciais hardcoded, bypass de auth) · plano de remoção + upgrade seguro + checklist go/no-go.

### [`https-security-headers-audit`](./https-security-headers-audit.md)
Transporte seguro (HTTPS/TLS) e a suíte completa de **security headers**.
**Quando:** garantir que nada trafega em claro e bloquear downgrade de protocolo.
**Cobre:** mixed content (scripts/imagens/API/websocket via HTTP) · redirect 301 forçado HTTP→HTTPS · HSTS (includeSubDomains/preload) · CSP (nonce/hash, upgrade-insecure-requests) · X-Frame-Options/frame-ancestors · X-Content-Type-Options · Referrer-Policy · Permissions-Policy · cookies Secure/HttpOnly/SameSite · TLS 1.2+ anti-downgrade · config por Nginx/Apache/Caddy/IIS/Traefik/CDN/framework · validação `curl -I`/Observatory.

---

## 🗄️ Banco de Dados & Dados

### [`database-tenant-isolation-audit`](./database-tenant-isolation-audit.md) 🏅
Garante que **um tenant nunca veja dados de outro**.
**Quando:** SaaS multi-tenant; revisar RLS/isolamento.
**Cobre:** RLS vs schema-per-tenant e trade-offs · propagação de contexto de tenant · FORCE RLS · teste por matriz (usuários × tabelas × operações) · detecção de vazamento (views/triggers/SECURITY DEFINER/service-role) · menor privilégio.

### [`database-performance-audit`](./database-performance-audit.md)
Performance do banco e da camada de acesso a dados.
**Quando:** o gargalo é a query, o ORM, a policy em linha ou o acesso a dados.
**Cobre:** RLS lenta (auth-function por linha → cache/SELECT/helpers/índices) · N+1 e batching (DataLoader) · índices ausentes (FK sem índice, full scan) · EXPLAIN/ANALYZE · paginação keyset/cursor · pooling · transações.

### [`data-integrity-and-ledger-audit`](./data-integrity-and-ledger-audit.md)
Invariantes e razão (ledger) para sistemas de **estado crítico**.
**Quando:** antes/depois de mexer em saldos; PR, incidente ou auditoria (financeiro, carteira, escrow, estoque, créditos).
**Cobre:** Fórmula de Ouro (SUM=constante) · fechamento de razão e por lançamento · coerência de cache de saldo · double-entry · transações atômicas com meta-validação · dinheiro nunca em float · append-only com estornos · reconciliação · snapshots forenses (SHA-256).

### [`cache-and-server-state-architecture`](./cache-and-server-state-architecture.md)
Coerência de cache e server-state, do cliente ao banco.
**Quando:** dados stale, bugs de sincronização, invalidação inconsistente.
**Cobre:** query key factory · invalidação por tags/entidades · optimistic update com rollback · flush→refresh→invalidate após colunas geradas por trigger · React Query/RTK/SWR/Apollo/Riverpod + Hibernate/Prisma/SQLAlchemy/EF + Redis/CDN/HTTP.

---

## 📊 Observabilidade & Operação

### [`observability-logging-audit`](./observability-logging-audit.md) 🏅
Deixa o sistema **debuggável, auditável e seguro** em produção.
**Quando:** logs ruins, falhas silenciosas, difícil diagnosticar incidentes.
**Cobre:** logs estruturados JSON · correlação requestId/traceId · eliminação de falhas silenciosas · redaction/masking · níveis de log · métricas · tracing · health checks · alertas.

### [`production-monitoring-standards`](./production-monitoring-standards.md)
**Regras para construir** sistemas monitoráveis (projetar, não auditar).
**Quando:** ao desenhar ou endurecer a operabilidade de um serviço.
**Cobre:** request ID · stack trace com contexto · logs JSON · health checks · query/cache tracking · métricas de performance · testes de regressão · alertas · deploy com rollback automático.

### [`error-handling-audit`](./error-handling-audit.md)
Tratamento de erros e UX de falha, frontend e backend.
**Quando:** erros engolidos, app trava sem feedback, `catch` vazio.
**Cobre:** assíncronos sem tratamento · falhas silenciosas · perda de stack/cause · estados de erro/retry/fallback · error boundaries · handlers globais · erro esperado vs inesperado.

### [`product-analytics-architecture`](./product-analytics-architecture.md)
Analytics de **produto** orientada a eventos (distinto de logging).
**Quando:** medir ativação, retenção e conversão.
**Cobre:** catálogo de eventos como constantes · instrumentação com detecção first-ever (funil) · auto-tracking via observer de rota · init privacy-first com toggle · PostHog/Mixpanel/Amplitude.

### [`backup-disaster-recovery-audit`](./backup-disaster-recovery-audit.md)
Resiliência de dados e **disaster recovery** — antes que o incidente aconteça.
**Quando:** auditar/montar a estratégia de backup/DR (visão SRE/DBA).
**Cobre:** backups automatizados (dumps, cron/scheduler/K8s CronJob) · regra 3-2-1 com isolamento off-site (a credencial da app nunca pode deletar o backup) · cripto + retenção · RPO/RTO · plano de DR/runbook · **teste de restore** (backup não testado não é backup) · scripts multi-stack (pg_dump/xtrabackup/mongodump/restic → S3/GCS/Azure/B2/R2/MinIO) com verificação por hash e alertas.

---

## ⚙️ Rigor Operacional & Coordenação

### [`paranoid-execution-mode`](./paranoid-execution-mode.md) 🏅
Execução paranoica para operações **irreversíveis**.
**Quando:** mexer em banco/deploy/infra/migração/auth/billing onde estado errado causa dano.
**Cobre:** output não-falsificável (hash/count/exit-code) · reconciliação memória-vs-realidade · transações atômicas com meta-validação · backup-first + rollback explícito · disciplina anti-workaround.

### [`multi-phase-operation-coordination`](./multi-phase-operation-coordination.md)
Operações complexas em **fases com pause points obrigatórios**.
**Quando:** migração/refactor/rollout/deploy/backfill/upgrade onde "rodar tudo de uma vez" é perigoso.
**Cobre:** executor reporta, orquestrador valida antes de autorizar · ondas só com escopo disjoint (arquivos PERMITIDOS/PROIBIDOS) · banco nunca em paralelo · estado por artefatos (PLAN/SUMMARY/VERIFICATION) resumível.

### [`gotchas-knowledge-transfer`](./gotchas-knowledge-transfer.md)
Transforma armadilhas em conhecimento transferível.
**Quando:** construir e manter uma base de lições aprendidas.
**Cobre:** template Sintoma → Antipattern → Fix → Root Cause → Validação Empírica → Lição · catálogo de "pegadinhas" · severidade · transferência entre sessões/agentes.

### [`pre-ship-smoke-checklist`](./pre-ship-smoke-checklist.md)
Smoke test pré/pós-deploy com **critérios observáveis cravados**.
**Quando:** logo antes e logo depois de subir algo para produção.
**Cobre:** matriz de cenários (T1..Tn) com passos/esperado/pré-condição · comandos para forçar edge cases · checklist pós-deploy (build/auth logs, DNS, cert, janela anônima) · relato reproduzível.

---

## 🐛 Depuração, Testes & Qualidade

### [`ai-code-review`](./ai-code-review.md) 🏅
Code review rigoroso de código de IA, **explicado para leigos**.
**Quando:** revisar código gerado por IA antes de produção.
**Cobre:** segurança · bugs · arquitetura · performance · tipagem · testes · manutenibilidade · escalabilidade · priorização por risco · antes/depois · código revisado.

### [`scientific-debugging-protocol`](./scientific-debugging-protocol.md)
Depuração científica — investigar **sem pular para o fix**.
**Quando:** bug difícil, intermitente ou de causa desconhecida.
**Cobre:** pipeline com gates (Reproduzir → Rastrear → Propor → Verificar → Reportar) · 5-Whys · rastreio de fluxo de dados · classificação de erro (UI/API-rede/Build) · hipótese com checkpoint · forensics.

### [`conversational-uat`](./conversational-uat.md)
UAT conversacional com **auto-diagnóstico** de falhas.
**Quando:** validar features com um usuário não-técnico, sem interrogatório.
**Cobre:** um teste por vez em texto simples · hipótese de causa raiz automática · plano de correção que realimenta só os gaps · artefato `{fase}-UAT.md`.

### [`test-coverage-audit`](./test-coverage-audit.md)
Acha áreas críticas sem testes e propõe os testes certos.
**Quando:** priorizar onde testar primeiro.
**Cobre:** unitários, integração e casos de erro · prioridade por risco (auth, pagamentos, dados de usuário, lógica de negócio) · foco em comportamento · framework adequado.

### [`e2e-test-architecture`](./e2e-test-architecture.md)
Testes E2E **resilientes** (confiabilidade e manutenção).
**Quando:** suíte E2E _flaky_ ou difícil de manter.
**Cobre:** Page Object Model · seletores por papel/acessibilidade · esperas resilientes sem timeout fixo · locator chaining/filtering · isolamento de estado · Playwright/Cypress/Selenium/WebdriverIO/Appium/Detox.

### [`dead-code-elimination`](./dead-code-elimination.md)
Remoção **segura** de código morto.
**Quando:** limpar o projeto sem quebrar nada.
**Cobre:** componentes/funções/imports/estado/branches mortos · feature flags fossilizadas · deps não usadas · cautelas (reflexão, DI, entrypoints dinâmicos, APIs/SDKs públicos, i18n, code splitting) · ferramentas (knip, ts-prune, vulture, cargo-udeps…).

### [`type-safety-audit`](./type-safety-audit.md)
Segurança de tipos sem overengineering.
**Quando:** muito `any`, dados externos sem validação, tipos frouxos.
**Cobre:** abuso de `any`/escape hatches · parâmetros/retornos sem tipo · validação runtime na fronteira (schemas) · tipos que refletem o domínio · TS/Python typing/Go/Java/Kotlin/C#/Rust.

### [`performance-optimization-audit`](./performance-optimization-audit.md)
Performance com **medição obrigatória**.
**Quando:** lentidão real, frontend ou backend.
**Cobre:** re-renders e memoização justificada · cálculos no render · virtualização de listas · imagens/bundles · N+1 · paginação/índices/cache · operações bloqueantes · timeouts.

---

## 🎨 Frontend & Arquitetura de UI

### [`state-management-audit`](./state-management-audit.md) 🏅
Estado de UI no lugar certo, sem duplicação nem global desnecessário.
**Quando:** prop drilling, estado inconsistente, context para tudo.
**Cobre:** prop drilling · estado no nível errado · duplicado/derivado · uso indevido de context/store global · colocation · server-state vs client-state · React/Vue/Svelte/Solid/Angular.

### [`reactive-hooks-audit`](./reactive-hooks-audit.md)
Hooks/primitivas reativas previsíveis e testáveis.
**Quando:** bugs de re-render, stale closure, loop infinito; revisar custom hooks.
**Cobre:** regras de hooks · dependências de efeitos corretas · extração para hooks/composables · estado simples vs reducer/máquina de estado · React/Vue/Svelte/Solid/Angular.

### [`component-architecture-audit`](./component-architecture-audit.md)
Separação entre **lógica e apresentação** (sem overengineering).
**Quando:** componentes que fazem demais, regra de negócio na view.
**Cobre:** lógica vazada para a UI · data-fetching em componentes de apresentação · container/presentational vs hooks/composables · refatoração para reutilizáveis e testáveis.

### [`frontend-design-distinctiveness`](./frontend-design-distinctiveness.md)
Mata o **"AI slop"** visual e exige identidade estética.
**Quando:** UI genérica/gerada por IA; definir identidade antes de construir.
**Cobre:** rejeita clichês (gradiente roxo, Inter/Space Grotesk, bento boxes, orbs, hero centralizado, copy genérica) · exige tipografia ousada, paleta intencional, layout que quebra o grid · checklist de anti-padrões.

---

## 🔌 Integrações, Billing & Privacidade

### [`third-party-integration-playbook`](./third-party-integration-playbook.md) 🏅
Integração **robusta** com serviços externos.
**Quando:** integrar/endurecer gateways/SaaS (pagamentos, CRM, analytics, email, mensageria).
**Cobre:** webhooks idempotentes (id determinístico via hash) · retry/replay · state machine de eventos · sync assíncrono fire-and-forget que não bloqueia a transação · auth de webhook por header-secret · API client tipado · email transacional por template.

### [`saas-billing-and-quota-enforcement`](./saas-billing-and-quota-enforcement.md)
Cobrança e **quotas que o app não contorna**.
**Quando:** construir/auditar planos pagos, limites de uso e trials.
**Cobre:** quota em duas camadas (banco + UX) · catálogo de planos · usage metrics · máquinas de estado de assinatura (trialing/active/past_due/canceled) via jobs agendados · RLS WITH CHECK, pg_cron, billing_events, Stripe/Asaas.

### [`privacy-consent-lgpd-gdpr-compliance`](./privacy-consent-lgpd-gdpr-compliance.md)
Compliance **operacional** de privacidade (não vuln scan).
**Quando:** qualquer sistema com dados pessoais — crítico para saúde/PII e financeiro.
**Cobre:** consentimento dual-layer (provider + log local imutável) · políticas versionadas com gate bloqueante · cerimônia de _erase_ (pseudonimização/soft-delete, revogação de token) · DSAR em prazo legal · preservação forense da trilha de auditoria.

---

## 🏗️ Processo, Design & Documentação

### [`architecture-design-blueprint`](./architecture-design-blueprint.md) 🏅
Blueprint de arquitetura via **entrevista multi-fase com gates**.
**Quando:** desenhar um app/serviço novo (foco técnico).
**Cobre:** Fase 1 descoberta (objetivo + escala) · Fase 2 constraints (frontend/backend/dados/integração) · Fase 3 síntese (patterns + checklist de performance, template, validação) · camadas, contratos, decisões e trade-offs proporcionais.

### [`skill-authoring`](./skill-authoring.md)
Meta-prompt: **criar e revisar skills** de alta qualidade.
**Quando:** autorar uma skill nova, padronizar uma família, auditar antes de publicar.
**Cobre:** seletor de padrão (Tool Wrapper/Pipeline/Generator/Reviewer/Inversion) · frontmatter correto · progressive disclosure com references · estilo Mythos · teste com contexto fresco.

### [`doc-coauthoring-reader-testing`](./doc-coauthoring-reader-testing.md)
Co-autoria de docs em **3 estágios com reader testing**.
**Quando:** specs, RFCs, propostas, design docs, READMEs, ADRs, runbooks.
**Cobre:** coleta de contexto multi-turn · refino seção-a-seção com edits incrementais · reader testing com contexto fresco (prever perguntas, caçar ambiguidade) antes de publicar.

### [`git-workflow-standards`](./git-workflow-standards.md)
Padroniza commits, branches e operações de PR/MR.
**Quando:** dar consistência ao fluxo Git de um time.
**Cobre:** nomes de branch (feature/fix/hotfix/chore) · Conventional Commits · babysitting de PR (CI, fixup, nunca amend em publicado) · gates de workflow · auditoria de conformidade do histórico.

---

## 📱 Mobile / Flutter
> Especializados em Flutter, com seção de **princípios cross-stack** (CSS, React Native, SwiftUI, Compose). _A versão skill (repo irmão) traz `references/assets/scripts`._

### [`flutter-overflow-guard`](./flutter-overflow-guard.md)
Previne, diagnostica e **prova** ausência de overflow de layout.
**Quando:** RenderFlex overflowed, layout quebrando, texto que não cabe, teclado cobrindo botão.
**Cobre:** modelo de constraints · tabela sintoma→correção · Expanded/Flexible/Wrap/SingleChildScrollView/FittedBox · scanner heurístico · harness de widget-test multi-device · checklist (multi-size, textScaler, RTL, dark, SafeArea, teclado) · princípios cross-stack.

### [`flutter-pro-polish`](./flutter-pro-polish.md)
Tira a **"cara de Flutter/vibecoding"** via design tokens.
**Quando:** deixar o app profissional/custom; fugir do Material 3/Roboto/lavanda padrão.
**Cobre:** tabela de _tells_ · design tokens (cor/tipografia/espaço/raio/elevação/motion) · re-tema dos widgets default · scanner de defaults · dark mode desenhado · acessibilidade (AA, ≥48dp) · princípios cross-stack.

---

## 💼 Negócios

### [`business-deep-dive-consultant`](./business-deep-dive-consultant.md)
Consultor sênior que faz um **diagnóstico socrático** do seu negócio.
**Quando:** entender o negócio a fundo e achar onde se ganha/perde dinheiro.
**Cobre:** uma pergunta por vez com follow-ups · modelo de negócio, unit economics, funil, retenção, margem, gargalos · entrega 3 forças ocultas + 3 melhorias quantificadas + 2 ações de 30 dias de alto ROI.

---

## Licença

[MIT](./LICENSE) © 2026 Everton Fernandes — use, copie, modifique e distribua livremente.

## Repositório irmão

🧩 [**mythos-skills**](https://github.com/evertonfernandes3321-wq/mythos-skills) — os mesmos 44 como **skills nativas do Claude Code** (com frontmatter, descoberta automática e `references/assets/scripts`).

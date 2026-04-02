# Especificação Técnica — GRANIX Platform

> **Documento Técnico** | Versão 2.0 | Abril 2026
>
> **Projeto**: GRANIX — Plataforma B2B2C de Educação Financeira Familiar
> **Classificação**: Confidencial
> **Substitui**: `docs/archive/pre-pivot/technical-spec-pre-pivot.md` (modelo B2C standalone)

---

## Índice

1. [Visão Geral da Arquitetura](#1-visão-geral-da-arquitetura)
2. [Modelo de Negócio — B2B2C SaaS](#2-modelo-de-negócio--b2b2c-saas)
3. [Opções de Integração com Bancos Parceiros](#3-opções-de-integração-com-bancos-parceiros)
4. [Fluxo Transacional — Potes Virtuais](#4-fluxo-transacional--potes-virtuais)
5. [Stack Tecnológico](#5-stack-tecnológico)
6. [Microserviços — Core Engine](#6-microserviços--core-engine)
7. [Modelo de Dados](#7-modelo-de-dados)
8. [AI Engine](#8-ai-engine)
9. [Segurança e Compliance](#9-segurança-e-compliance)
10. [Infraestrutura e DevOps](#10-infraestrutura-e-devops)
11. [Observabilidade](#11-observabilidade)

---

## 1. Visão Geral da Arquitetura

### 1.1 Princípio Fundador

> **GRANIX não movimenta, detém ou custodia dinheiro.**
> A GRANIX é um middleware de educação financeira. Todo dinheiro permanece na conta do menor no banco parceiro. A GRANIX orquestra comandos, armazena dados comportamentais e entrega a experiência educacional.

### 1.2 Diagrama C4 — Nível Sistema

```
┌─────────────────────────────────────────────────────────────────┐
│                        FAMÍLIAS                                  │
│                                                                  │
│  [App do Filho]     [App dos Pais]     [Admin Dashboard]        │
│  iOS/Android        iOS/Android        Web (bancos parceiros)   │
└──────────────────────────┬──────────────────────────────────────┘
                           │ HTTPS / SDK / WebView
                           ▼
┌─────────────────────────────────────────────────────────────────┐
│                    API GATEWAY (GRANIX)                          │
│              Rate Limiting · Auth · mTLS · WAF                  │
└──────────────────────────┬──────────────────────────────────────┘
                           │
                           ▼
┌─────────────────────────────────────────────────────────────────┐
│                     CORE ENGINE (GRANIX)                         │
│                                                                  │
│  ┌──────────────┐  ┌──────────────┐  ┌────────────────────┐    │
│  │ Virtual Pots │  │  AI Engine   │  │  Gamification      │    │
│  │   Manager   │  │  (6 modelos) │  │  Engine            │    │
│  └──────────────┘  └──────────────┘  └────────────────────┘    │
│  ┌──────────────┐  ┌──────────────┐  ┌────────────────────┐    │
│  │  Auth &      │  │  Notification│  │  Analytics &       │    │
│  │  KYC Bridge  │  │  Service     │  │  Reporting         │    │
│  └──────────────┘  └──────────────┘  └────────────────────┘    │
└──────────────────────────┬──────────────────────────────────────┘
                           │ mTLS · API REST/Webhook
                           ▼
┌─────────────────────────────────────────────────────────────────┐
│                  BANCO PARCEIRO                                   │
│                                                                  │
│  Core Banking  ·  PIX/Payments  ·  KYC/Compliance  ·  Conta    │
│  (Bradesco, Santander, Itaú, Bancos Digitais, etc.)             │
└─────────────────────────────────────────────────────────────────┘
```

### 1.3 O que a GRANIX armazena vs o que fica no banco

| Dado | Onde fica | Justificativa |
|------|-----------|---------------|
| Saldo real da conta | Banco parceiro | GRANIX nunca detém dinheiro |
| Número de conta, agência | Banco parceiro | Dado financeiro sensível |
| KYC (identidade, documentos) | Banco parceiro | Responsabilidade regulatória do banco |
| Saldo virtual de cada pote | GRANIX DB | Contabilidade interna dos 4 potes |
| Histórico de alocações | GRANIX DB | Necessário para relatórios e ML |
| Dados comportamentais | GRANIX DB (sem PII) | Personalização de conteúdo |
| Conteúdo educacional | GRANIX DB | Core do produto |
| Metas, tarefas, conquistas | GRANIX DB | Gamificação |
| IDs externos do banco | GRANIX DB (referência) | Para orquestrar comandos |

---

## 2. Modelo de Negócio — B2B2C SaaS

### 2.1 Posicionamento

```
BANCO PARCEIRO ──── contrata GRANIX ────► GRANIX entrega
     (B2B)                                experiência às
                                          FAMÍLIAS (B2C)
```

- **Cliente pagante:** Banco parceiro (SaaS fee + revenue share)
- **Usuário final:** Famílias (pais + filhos)
- **Proposta de valor para o banco:** Aumentar engajamento, retenção de famílias jovens, diferenciação de produto, dados comportamentais de menores (com consentimento)
- **Proposta de valor para a família:** Educação financeira gamificada, controle parental, mesada digital com 4 potes

### 2.2 Responsabilidades — GRANIX vs Banco

| Responsabilidade | GRANIX | Banco Parceiro |
|-----------------|--------|----------------|
| Conta corrente do menor | ❌ | ✅ |
| Cartão débito/pré-pago | ❌ | ✅ |
| KYC e onboarding regulatório | ❌ | ✅ |
| Movimentação de dinheiro | ❌ | ✅ |
| PIX, TED, boleto | ❌ | ✅ |
| Licença BACEN | ❌ | ✅ |
| UI/UX de educação financeira | ✅ | ❌ |
| Gamificação e missões | ✅ | ❌ |
| AI de personalização | ✅ | ❌ |
| Gestão de potes virtuais | ✅ | ❌ |
| Notificações parentais | ✅ | ❌ |
| Dashboard para o banco | ✅ | ❌ |
| Compliance LGPD dados educacionais | ✅ | ❌ |

---

## 3. Opções de Integração com Bancos Parceiros

### Opção 1 — SDK + WebView (Integração Leve)

```
App do Banco
    └── WebView embebida
            └── GRANIX Web App
```

**Para:** Bancos tradicionais (legado), MVPs rápidos
**Vantagens:** Integração em semanas, zero mudança no app nativo do banco
**Desvantagens:** UX limitada; Apple/Google podem restringir WebViews em apps financeiros; performance inferior
**Esforço do banco:** < 2 sprints

### Opção 2 — White-Label App (App Dedicado)

```
App GRANIX (white-label com marca do banco)
    └── Autenticação SSO via banco
    └── API GRANIX ← → API Banco
```

**Para:** Bancos que querem app separado para famílias
**Vantagens:** Experiência completa, performance nativa, UX sem compromisso
**Desvantagens:** Requer aprovação nas App Stores, manutenção de 2 apps pelo banco
**Esforço do banco:** Fornecimento de credenciais SSO + revisão de marca

### Opção 3 — SDK Nativo Modular (Integração Profunda) ⭐ Recomendada

```
App do Banco
    ├── Módulo GRANIX Auth
    ├── Módulo GRANIX Dashboard Filho
    ├── Módulo GRANIX Dashboard Pais
    └── Módulo GRANIX Missões/Gamificação
```

**Para:** Bancos digitais (Nubank, C6, Inter), bancos product-first
**Vantagens:** Experiência nativa perfeita, sem WebView, marca do banco preservada, analytics unificados
**Desvantagens:** Integração mais demorada (6-12 semanas), acoplamento maior
**Esforço do banco:** Integração SDK nativo iOS/Android + backend API

---

## 4. Fluxo Transacional — Potes Virtuais

### 4.1 Conceito Fundamental

> **Os 4 Potes são caixas contábeis virtuais no banco de dados da GRANIX.**
> Não são sub-contas reais, não são contas bancárias separadas. O dinheiro fica
> em UMA única conta corrente no banco parceiro. A GRANIX mantém a contabilidade
> interna de quanto de saldo "pertence" a cada pote.

```
CONTA REAL NO BANCO (única)
├── Saldo total: R$ 100,00
│
└── GRANIX DB (contabilidade virtual)
    ├── Pote Gastar:  R$ 40,00
    ├── Pote Guardar: R$ 30,00
    ├── Pote Investir: R$ 20,00
    └── Pote Doar:    R$ 10,00
    
    SOMA ALWAYS = Saldo real: R$ 100,00
```

### 4.2 Fluxo de Alocação de Mesada (Saga Pattern)

```
PAI confirma mesada R$ 100
         │
         ▼
[1] GRANIX → Banco: POST /pix/send {amount: 100, to: conta_filho}
         │
         ▼
[2] Banco executa PIX → conta_filho credita R$ 100
         │
         ▼
[3] Banco → GRANIX: webhook {event: credit_received, amount: 100}
         │
         ▼
[4] GRANIX: calcular split (conforme regra da família)
    ├── Gastar: R$ 40 (40%)
    ├── Guardar: R$ 30 (30%)
    ├── Investir: R$ 20 (20%)
    └── Doar:    R$ 10 (10%)
         │
         ▼
[5] GRANIX DB: UPDATE virtual_pots WHERE family_id = X
    → transação atômica nos 4 potes (banco de dados da GRANIX)
         │
         ▼
[6] GRANIX: notificar filho + pai (push notification)
```

**Compensação (rollback):** Se o webhook do banco não chegar em 30s após o PIX, o step [4] não é executado. GRANIX monitora PIX pendentes via polling a cada 5min durante 24h. Após 24h sem confirmação: alerta ao pai + registro de inconsistência para revisão manual.

### 4.3 Fluxo de Gasto (Compra com Cartão)

```
Filho usa cartão (débito do banco parceiro)
         │
         ▼
[1] Banco autoriza transação (próprio sistema do banco)
         │
         ▼
[2] Banco → GRANIX: webhook {event: debit, amount: X, pot: "gastar"}
         │
         ▼
[3] GRANIX: verificar saldo virtual do pote "Gastar"
    ├── Se saldo >= X → UPDATE virtual_pot (debit) → OK
    └── Se saldo < X → flag pote_negativo → notificar pai
         │
         ▼
[4] GRANIX: registrar na linha do tempo educacional do filho
[5] GRANIX: atualizar score AI (padrão de gasto)
[6] GRANIX: notificar pai se limite configurado foi atingido
```

**Nota:** A GRANIX não bloqueia nem autoriza a transação — isso é do banco. A GRANIX apenas atualiza a contabilidade virtual pós-transação e notifica.

### 4.4 Cache de Saldo e Reconciliação

Para evitar dependência crítica da API do banco em tempo real:

- **TTL de cache:** 30 segundos para saldo total da conta
- **Atualização:** Via webhook do banco (tempo real) + polling fallback a cada 60s
- **Reconciliação diária:** 02h BRT — GRANIX busca saldo real do banco e verifica se soma dos potes virtuais == saldo real. Divergências: alerta para time de operações.
- **Regra de ouro:** Se cache expirado, GRANIX mostra último saldo conhecido + indicador "⏱ atualizado há X min" na UI

---

## 5. Stack Tecnológico

### 5.1 Backend

| Componente | Tecnologia | Justificativa |
|-----------|-----------|---------------|
| API Gateway | Kong / AWS API Gateway | Rate limiting, mTLS, plugins |
| Core Services | Node.js (TypeScript) + NestJS | Consistência, tipagem forte |
| Message Broker | Apache Kafka | Audit log imutável, event streaming |
| Cache | Redis Cluster | Saldo cache, session, rate limit |
| Banco de dados principal | PostgreSQL (RDS) + Row-Level Security | Multi-tenant, LGPD, ACID |
| Banco de dados analítico | ClickHouse | Queries ML, behavioral analytics |
| Search | Elasticsearch | Busca de conteúdo educacional |
| AI/ML | Python (FastAPI) + TensorFlow/Scikit | Isolado em serviço dedicado |

### 5.2 Frontend / SDK

| Componente | Tecnologia |
|-----------|-----------|
| App Mobile (White-label) | React Native (iOS + Android) |
| SDK Nativo iOS | Swift/SwiftUI |
| SDK Nativo Android | Kotlin/Jetpack Compose |
| Web App (WebView / Admin) | Next.js 14 + TypeScript |
| Design System | Tamagui (cross-platform) |

### 5.3 Infraestrutura

| Componente | Tecnologia |
|-----------|-----------|
| Cloud | AWS (multi-AZ, região sa-east-1) |
| Containers | EKS (Kubernetes) |
| CI/CD | GitHub Actions + ArgoCD |
| Secrets | AWS Secrets Manager |
| CDN | CloudFront |
| DNS | Route 53 |

---

## 6. Microserviços — Core Engine

```
core-engine/
├── auth-service          # SSO bridge com banco parceiro
├── family-service        # Perfis de família (pais + filhos)
├── virtual-pots-service  # Contabilidade dos 4 potes ← CORE
├── bank-connector        # Adaptadores por banco parceiro
├── notification-service  # Push, email, in-app
├── ai-engine             # ML models (serviço Python separado)
├── gamification-service  # Missões, conquistas, XP
├── content-service       # Conteúdo educacional
├── analytics-service     # Behavioral analytics
└── admin-service         # Dashboard banco parceiro
```

### 6.1 Bank Connector — Padrão Adaptador

Cada banco parceiro tem um adaptador específico que implementa a interface:

```typescript
interface BankConnector {
  getAccountBalance(accountId: string): Promise<Balance>
  getTransactionHistory(accountId: string, from: Date, to: Date): Promise<Transaction[]>
  sendWebhookRegistration(events: BankEvent[]): Promise<void>
  validateWebhook(payload: unknown, signature: string): boolean
}

// Implementações:
class BradescoConnector implements BankConnector { ... }
class SantanderConnector implements BankConnector { ... }
class ItauConnector implements BankConnector { ... }
class GenericOpenFinanceConnector implements BankConnector { ... } // fallback
```

### 6.2 Multi-Tenancy — Isolamento de Dados

```sql
-- Row-Level Security por tenant (banco parceiro)
CREATE POLICY tenant_isolation ON virtual_pots
  USING (tenant_id = current_setting('app.current_tenant')::uuid);

-- Nunca dados de Banco A visíveis para Banco B
-- App server: SET app.current_tenant = '{bank_partner_id}' no início de cada request
```

Estratégia: **Row-Level Security (RLS)** no PostgreSQL — mesma instância, isolamento garantido por policy. Para bancos com requisitos de dados em instância dedicada: configuração via feature flag (`DEDICATED_DB_INSTANCE=true`).

---

## 7. Modelo de Dados

### 7.1 Entidades Principais

```sql
-- Família
families (
  id UUID PK,
  tenant_id UUID FK → bank_partners,  -- multi-tenant
  bank_account_id VARCHAR,             -- ID da conta no banco parceiro
  created_at, updated_at
)

-- Membros (pais e filhos)
family_members (
  id UUID PK,
  family_id UUID FK,
  role ENUM ('parent', 'child'),
  age INT,
  bank_user_id VARCHAR,               -- ID do usuário no banco parceiro
  -- SEM nome, CPF, email aqui — dados PII ficam no banco parceiro
  created_at
)

-- Potes Virtuais (CORE)
virtual_pots (
  id UUID PK,
  family_id UUID FK,
  child_member_id UUID FK,
  pot_type ENUM ('gastar', 'guardar', 'investir', 'doar'),
  balance_cents BIGINT NOT NULL DEFAULT 0,  -- centavos, evita float
  last_bank_sync_at TIMESTAMP,             -- última reconciliação com banco
  version INT NOT NULL DEFAULT 1,          -- optimistic locking
  created_at, updated_at
)

-- Transações de Pote (audit trail)
pot_transactions (
  id UUID PK,
  pot_id UUID FK,
  amount_cents BIGINT,
  direction ENUM ('credit', 'debit'),
  source ENUM ('allowance', 'task_reward', 'bank_webhook', 'manual_adjustment'),
  bank_transaction_ref VARCHAR,            -- referência da transação no banco
  created_at
)

-- Tarefas
tasks (
  id UUID PK,
  family_id UUID FK,
  assigned_to UUID FK → family_members,
  title, description, reward_cents BIGINT,
  target_pot ENUM ('gastar', 'guardar', 'investir', 'doar'),
  status ENUM ('pending', 'completed', 'approved', 'rejected'),
  due_date DATE,
  created_at, completed_at, approved_at
)

-- Banco Parceiro
bank_partners (
  id UUID PK,
  name VARCHAR,
  connector_class VARCHAR,               -- ex: 'BradescoConnector'
  api_base_url VARCHAR,
  webhook_secret VARCHAR ENCRYPTED,
  config JSONB,                          -- feature flags por banco
  created_at
)
```

### 7.2 Invariante de Consistência dos Potes

```
∀ family ∈ families:
  SUM(virtual_pots.balance WHERE family_id = family.id AND child = X)
  == bank.getAccountBalance(family.bank_account_id)
  
  [verificado pela reconciliação diária às 02h BRT]
```

---

## 8. AI Engine

### 8.1 Modelos — Faseamento por Complexidade

**Fase 1 — MVP (lançamento):**

| Modelo | Input | Output | Algoritmo |
|--------|-------|--------|-----------|
| Anti-Churn | Dias sem login, tarefas pendentes, engajamento | Score 0-1 de risco | Gradient Boosting |
| 4-Pots Advisor | Padrão de gasto histórico, idade, metas | Sugestão de % por pote | Regras + ML simples |

**Fase 2 — Pós-MVP (6 meses):**

| Modelo | Input | Output | Algoritmo |
|--------|-------|--------|-----------|
| Content Recommendation | Histórico de conteúdo, idade, engajamento | Próximo conteúdo ideal | Collaborative Filtering |
| Financial Behavior Score | Todas as transações e interações | Score de saúde financeira familiar | Random Forest |

**Fase 3 — Escala (12+ meses):**

| Modelo | Input | Output | Algoritmo |
|--------|-------|--------|-----------|
| Difficulty Adjustment | Performance em missões, erros, tempo | Nível de dificuldade adaptativo | Reinforcement Learning |
| Challenge Generator | Perfil do filho, contexto | Missão financeira personalizada | LLM fine-tuned |

**Regra de privacidade:** Todos os modelos recebem dados anonimizados — sem nome, CPF, ou qualquer PII. Identificador interno: hash não-reversível do family_id.

**Ajuste sazonal obrigatório:** Anti-churn e Content Recommendation devem incluir `is_school_vacation` como feature, usando calendário escolar brasileiro (julho, dezembro/janeiro). Períodos de férias geram falsos positivos de churn sem esse ajuste.

---

## 9. Segurança e Compliance

### 9.1 Segurança Técnica

| Camada | Controle |
|--------|---------|
| Transporte | TLS 1.3 obrigatório; mTLS para canal GRANIX ↔ Banco |
| Autenticação | OAuth 2.0 + PKCE; JWT com rotação a cada 15min |
| Autorização | RBAC por role (parent / child / bank_admin / granix_admin) |
| Dados em repouso | AES-256 (RDS + S3); campos sensíveis: envelope encryption |
| Secrets | AWS Secrets Manager; zero secrets em código ou variáveis de ambiente em texto claro |
| Auditoria | Kafka append-only para todas as ações; retenção 5 anos (Resolução BCB 4.893) |
| Pentest | Semestral por empresa terceira credenciada |
| SOC 2 Type II | Auditoria anual; 5 trust service criteria |

### 9.2 Conformidade Regulatória — Dados de Menores

> Seção revisada e validada pelo Lex (04/2026).

**Conformidade Regulatória — Proteção de Dados de Menores**

A arquitetura da plataforma GRANIX foi concebida em conformidade com o arcabouço regulatório aplicável ao tratamento de dados pessoais de crianças e adolescentes no Brasil. Em aderência ao **art. 14 da LGPD (Lei nº 13.709/2018)**, todo tratamento de dados pessoais de menores — incluindo dados comportamentais coletados para personalização de conteúdo — está condicionado ao **consentimento específico e em destaque** de pelo menos um dos pais ou responsável legal. A GRANIX implementa mecanismos de coleta e verificação de consentimento parental baseados nas tecnologias disponíveis, adotando os princípios de *privacy-by-design* e *data minimization*, sempre orientados pelo princípio do melhor interesse da criança, conforme orientação da ANPD. O **Relatório de Impacto à Proteção de Dados Pessoais (RIPD)** específico para a população infanto-juvenil é mantido atualizado e disponível para auditorias regulatórias e processos de due diligence de instituições financeiras parceiras.

No âmbito do **ECA Digital (Lei nº 15.211/2025)**, em vigor desde **17 de março de 2026**, a plataforma oferece ferramentas de controle parental nativas e acessíveis, que permitem ao responsável legal gerenciar interações, limitar tempo de uso, controlar sistemas de recomendação baseados em IA e restringir o compartilhamento de dados. A verificação de idade é realizada por mecanismos confiáveis — integrando validação com bases de dados governamentais e/ou financeiras —, garantindo a vinculação de contas de menores de 16 anos aos respectivos responsáveis. O uso de Inteligência Artificial para personalização de conteúdo financeiro é monitorado para assegurar aderência às restrições legais sobre perfilamento de menores e publicidade direcionada. O modelo de IA opera exclusivamente com base no melhor interesse do usuário menor, sem inferência de propensão de consumo, segmentação comercial ou compartilhamento de perfis com terceiros, afastando a incidência das vedações previstas no art. 7º, §§ 3º e 4º da Lei nº 15.211/2025.

No que se refere à dimensão financeira, a GRANIX opera em modelo de orquestração: não movimenta recursos diretamente nem detém dados financeiros dos usuários. O **KYC, a abertura e a movimentação de contas** são realizados pelo banco parceiro sob sua própria licença regulatória, em conformidade com a **Res. CMN 4.753/2019** (contas de depósito — bancos tradicionais) ou **Res. BCB 96/2021** (contas de pagamento — fintechs/IPs), incluindo os requisitos de representação legal e consentimento dos responsáveis legais para contas de menores (Código Civil, arts. 3º e 4º). O contrato de parceria GRANIX ↔ Banco inclui cláusula de representação e garantia de cumprimento dessas normas. A GRANIX complementa com: (i) consentimento parental no próprio onboarding GRANIX (dupla camada), e (ii) log auditável imutável de todos os comandos enviados ao banco, garantindo rastreabilidade e defensabilidade em processos de due diligence regulatória.

**Mapeamento Controlador/Operador (LGPD)**

A GRANIX é:
- **Controladora** dos dados comportamentais e educacionais coletados na plataforma
- **Operadora** em relação aos dados financeiros e de identificação, que permanecem sob controle do banco parceiro

Essa distinção é documentada explicitamente no contrato de parceria e no DPA (Data Processing Agreement) firmado com cada banco parceiro, delimitando responsabilidades e viabilizando auditorias independentes.

### 9.3 Responsible Disclosure

A GRANIX mantém um programa de Vulnerability Disclosure Policy (VDP) público em `security.granix.com.br/disclosure`. Pesquisadores de segurança podem reportar vulnerabilidades com garantia de não-punição. Triagem em 5 dias úteis. Bug Bounty formal planejado para pós-SOC 2.

---

## 10. Infraestrutura e DevOps

### 10.1 Ambientes

| Ambiente | Propósito | Banco Parceiro |
|----------|-----------|----------------|
| `dev` | Desenvolvimento local | Mock / Sandbox |
| `staging` | QA e homologação | Sandbox do banco |
| `production` | Produção | Produção do banco |

### 10.2 Versionamento de API

- **Prefixo de versão:** `/api/v1/`, `/api/v2/`
- **Política de deprecação:** 180 dias de aviso prévio para breaking changes (bancos têm ciclos longos de deploy)
- **Comunicação:** Email para todos os bank_admin cadastrados + banner no Admin Dashboard + changelog público
- **Compatibilidade:** Manter N-1 versão sempre ativa

### 10.3 SLA por Componente

| Componente | SLA | RTO | RPO |
|-----------|-----|-----|-----|
| API Gateway | 99.9% | 15min | 1h |
| Virtual Pots Service | 99.95% | 5min | 0 (sync) |
| AI Engine | 99.5% | 30min | 24h |
| Admin Dashboard | 99.5% | 1h | 4h |

---

## 11. Observabilidade

### 11.1 Stack

- **Métricas:** Prometheus + Grafana
- **Logs:** ELK Stack (ElasticSearch + Logstash + Kibana)
- **Tracing:** OpenTelemetry + Jaeger
- **Alertas:** PagerDuty (crítico) + Slack (warning)
- **Uptime:** StatusPage público para bancos parceiros

### 11.2 Golden Signals por Serviço

| Sinal | Virtual Pots | Bank Connector | AI Engine |
|-------|-------------|----------------|-----------|
| Latência P99 | < 100ms | < 500ms | < 2s |
| Error rate | < 0.01% | < 0.1% | < 1% |
| Reconciliação | Delta diário < 0.001% | N/A | N/A |
| Webhook delay | N/A | < 5s | N/A |

---

## Histórico de Versões

| Versão | Data | Autor | Mudança |
|--------|------|-------|---------|
| 1.0 | Jan 2026 | Toto | Versão inicial (modelo B2C standalone) — **arquivada** |
| 2.0 | Abr 2026 | Toto + Forge | Pivot para modelo B2B2C SaaS; potes virtuais; multi-tenant |

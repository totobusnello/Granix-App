# GRANIX — PRD v2.0 — Plataforma B2B2C de Educação Financeira Familiar

> **Documento de Produto** | Versão 2.0 | Abril 2026
>
> **Substitui:** docs/archive/pre-pivot/PRD-pre-pivot.md
>
> **Projeto:** Plataforma B2B2C SaaS de educação financeira familiar
> **Modelo:** White-label para bancos parceiros
> **Autor:** Toto (CPO) | Gerado com auxílio de Claude Code

---

## Índice

1. [Resumo Executivo](#1-resumo-executivo)
2. [Modelo B2B2C](#2-modelo-b2b2c)
3. [Proposta de Valor (Dupla)](#3-proposta-de-valor-dupla)
4. [Funcionalidades Essenciais](#4-funcionalidades-essenciais)
5. [Arquitetura de Informação e Sitemap](#5-arquitetura-de-informação-e-sitemap)
6. [Jornadas de Usuário](#6-jornadas-de-usuário)
7. [Wireframes (ASCII)](#7-wireframes-ascii)
8. [Requisitos Técnicos](#8-requisitos-técnicos)
9. [Regras de Negócio Brasil](#9-regras-de-negócio-brasil)
10. [Monetização e Pricing](#10-monetização-e-pricing)
11. [Métricas e KPIs](#11-métricas-e-kpis)
12. [Plano de MVP](#12-plano-de-mvp)
13. [Riscos e Compliance](#13-riscos-e-compliance)
14. [Backlog Inicial](#14-backlog-inicial)

---

## 1. Resumo Executivo

### 1.1 Visão do Produto (B2B2C)

**GRANIX** é uma **plataforma SaaS B2B2C** de educação financeira familiar que bancos parceiros embute nas suas ofertas para clientes com menores de idade.

**Modelo:**
- **Cliente pagante:** Banco parceiro (taxa SaaS mensal)
- **Usuário final:** Famílias (pais + filhos)
- **GRANIX entrega:** Interface UI/UX educacional, gamificação, AI, sistema de 4 potes virtuais
- **Banco entrega:** Conta, cartão, KYC, PIX, licença BACEN, liquidação

**Princípio Fundador (OBRIGATÓRIO EM TODOS OS DOCS):**

> **GRANIX não movimenta, detém ou custodia dinheiro. É um middleware de educação financeira. Todo dinheiro fica na conta do menor no banco parceiro.**

### 1.2 Problema a Resolver

- **47% dos brasileiros** têm dificuldades em organizar o orçamento (Pesquisa Onze)
- **59% admitem** não saber como fazer planejamento financeiro
- **Falta de educação financeira** desde a infância
- Bancos carecem de diferenciadores para contas de menores
- Famílias não têm ferramentas adequadas para ensinar finanças digitais

### 1.3 Proposta de Valor

**Para o Banco:**
> "Aumentar a retenção de clientes pais oferecendo educação financeira de alto valor para seus filhos, sem custo operacional alto."

- Diferencial competitivo exclusivo
- Aumenta stickiness (pais não saem do banco pelos filhos)
- Monetiza conta de menor (produto que customiza)
- White-label - mantém marca do banco
- Sem necessidade de build interno

**Para a Família:**
> "Ensine educação financeira com uma ferramenta moderna que torna aprender a gerenciar dinheiro divertido e seguro."

- Sistema de 4 potes (Gastar/Guardar/Doar/Investir) educacional
- Gamificação, missões e desafios
- Controles parentais completos
- PIX, tarefas com recompensas, metas de poupança
- Conteúdo educacional interativo

---

## 2. Modelo B2B2C

### 2.1 Arquitetura de Negócio

```
┌─────────────────────────────────────────────────────────────┐
│                      GRANIX B2B2C STACK                     │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  TIER 1: BANCO PARCEIRO (Cliente Pagante)                  │
│  ┌──────────────────────────────────────────────┐          │
│  │ • Conta de depósito do menor                 │          │
│  │ • Cartão de débito (físico + virtual)        │          │
│  │ • Licença BACEN (KYC, PIX, etc)              │          │
│  │ • Liquidação de transações                   │          │
│  │ • Paga a GRANIX taxa SaaS + revenue share    │          │
│  └──────────────────────────────────────────────┘          │
│                          ↕                                  │
│  TIER 2: GRANIX (Middleware)                               │
│  ┌──────────────────────────────────────────────┐          │
│  │ • UI/UX (Apps mobile + web)                  │          │
│  │ • Sistema de 4 potes virtuais/contábeis      │          │
│  │ • Gamificação, tarefas, metas                │          │
│  │ • Educação financeira                        │          │
│  │ • Multi-tenancy (cada banco = tema/branding) │          │
│  │ • Webhooks para banco                        │          │
│  │ • Analytics e relatórios                     │          │
│  └──────────────────────────────────────────────┘          │
│                          ↕                                  │
│  TIER 3: USUÁRIOS FINAIS (Famílias)                        │
│  ┌──────────────────────────────────────────────┐          │
│  │ • Pais: gerenciam filhos, limites, mesada   │          │
│  │ • Filhos: aprendem, gastam, poupam           │          │
│  │ Acessam via app do banco (white-label)       │          │
│  └──────────────────────────────────────────────┘          │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### 2.2 Fluxo de Dados

```
Banco Parceiro
      ↓
  [Integração API]
      ↓
  GRANIX Platform
      ├── Valida dados
      ├── Aplica lógica educacional
      ├── Gerencia potes virtuais
      └── Retorna estado
      ↓
  [Webhooks + Callbacks]
      ↓
  Banco (atualiza saldo real)
      ↓
  Famílias (veem na app do banco)
```

### 2.3 Responsabilidades Claras

| Aspecto | GRANIX | Banco |
|---------|--------|-------|
| **Conta** | Espelha saldo real | Detém a conta |
| **Cartão** | Regras, limites, UX | Emite, processa transações |
| **PIX** | Regras, whitelist | Realiza transferência |
| **KYC** | UX, fluxo | Valida documentos |
| **Educação** | Conteúdo, gamificação | Apenas consome |
| **Potes** | Lógica virtual/contábil | Não tem visibilidade |
| **Tarefas/Metas** | 100% GRANIX | Não tem visibilidade |

---

## 3. Proposta de Valor (Dupla)

### 3.1 Para o Banco Parceiro

**Diferenciais Competitivos:**
- ✅ Feature exclusiva (educação financeira integrada)
- ✅ Não exige build interno (time reduzido)
- ✅ Customizável por marca (white-label)
- ✅ Validado no mercado (modelo Greenlight EUA + aprendizados BR)

**Métricas de Negócio:**
- ⬆ Aumenta retenção de pais (filhos = ancla)
- ⬆ Aumenta engajamento (app acessado diariamente)
- ⬆ Monetiza conta de menor (antes sem receita)
- ⬆ Cross-sell oportunidades (pais usam mais o banco)

**ROI:**
- Custo: Taxa SaaS + implementação inicial
- Benefício: +3-5% retenção de clientes pais = milhões de reais

### 3.2 Para as Famílias

**Educação:**
- 🎓 Aprende gestão de dinheiro desde jovem
- 🎓 Sistema de 4 potes (pilar do Greenlight global)
- 🎓 Conteúdo interativo + gamificação
- 🎓 Tarefas com recompensas = conexão trabalho↔dinheiro

**Segurança:**
- 🔐 Controles parentais completos
- 🔐 Limites configuráveis
- 🔐 Bloqueio de categorias (jogos, álcool, etc)
- 🔐 Supervisão em tempo real

**Engajamento:**
- 🎮 Missões diárias, badges, níveis
- 🎮 Metas visuais (ex: PS5 40% preenchido)
- 🎮 Desafios entre irmãos
- 🎮 Integração com banco que a família já usa

---

## 4. Funcionalidades Essenciais

### 4.0 🌟 CORE FEATURE: Sistema de 4 Potes (Virtual/Contábil)

**Princípio:** Cada centavo na conta é automaticamente dividido em 4 categorias educacionais.

Os potes são **virtuais na BD da GRANIX** - o banco vê saldo único, GRANIX gerencia a divisão.

```
MESADA/GANHO: R$ 100
          ↓
┌─────────┴────────────────────┐
│  ALOCAÇÃO AUTOMÁTICA         │
├──────────────────────────────┤
│ 💳 GASTAR      R$ 50 (50%)  │ → Gastos imediatos
│ 🐷 GUARDAR     R$ 30 (30%)  │ → Metas de poupança
│ 🎁 DOAR        R$ 10 (10%)  │ → Instituições/família
│ 📈 INVESTIR    R$ 10 (10%)  │ → Tesouro, CDB (futuro)
└──────────────────────────────┘
  (% configurável pelos pais)
```

**Por que funciona:**
- Criança vê dinheiro = aprende trade-offs
- Guardar fica VISUAL (PS5 40% preenchido)
- Não é "proibido" gastar, é "gerenciado"
- Investimento torna matemática concreta

### 4.1 MVP (Prioridade Alta)

| # | Feature | Descrição | Usuário |
|---|---------|-----------|---------|
| 1 | **🌟 Sistema de 4 Potes** | Divisão automática virtual | Ambos |
| 2 | **Conta Digital Menor** | Conta simplificada (espelha banco) | Filho |
| 3 | **Cartão Virtual** | Cartão pré-pago virtual (balde GASTAR) | Filho |
| 4 | **Controles Parentais** | Limites, % dos potes, notificações | Pai |
| 5 | **Mesada Automática** | Transferência automática com divisão | Pai→Filho |
| 6 | **Metas de Poupança** | Metas visuais vinculadas balde GUARDAR | Filho |
| 7 | **PIX** | Enviar/receber via PIX (do balde GASTAR) | Ambos |
| 8 | **Extrato por Pote** | Visualização de transações por categoria | Ambos |
| 9 | **Onboarding Familiar** | Cadastro pai + convite filho + config potes | Ambos |
| 10 | **Notificações Push** | Alertas de transações e metas | Ambos |

### 4.2 Pós-MVP (Prioridade Média)

| # | Feature | Descrição |
|---|---------|-----------|
| 11 | **Cartão Físico** | Cartão de débito físico personalizado |
| 12 | **Tarefas (Chores)** | Criar tarefas domésticas com recompensa |
| 13 | **Balde DOAR ativo** | Doações para instituições parceiras |
| 14 | **Juros Parentais** | Pais pagam % extra no balde GUARDAR |
| 15 | **Bloqueio de Categorias** | Bloquear gastos em categorias específicas |
| 16 | **Educação Financeira v1** | Quizzes e conteúdo básico |
| 17 | **Round-ups** | Arredondar compras para o balde GUARDAR |
| 18 | **Cashback** | % de volta para o balde GUARDAR |

### 4.3 Futuro (Prioridade Baixa)

| # | Feature | Descrição |
|---|---------|-----------|
| 19 | **Balde INVESTIR ativo** | Tesouro Direto, CDB, fundos para menores |
| 20 | **Localização** | GPS do filho em tempo real |
| 21 | **SOS/Emergência** | Botão de emergência com localização |
| 22 | **Open Finance** | Agregar contas de outros bancos |
| 23 | **Gamificação Avançada** | Níveis, badges, competições |
| 24 | **Comunidade** | Desafios entre amigos |
| 25 | **Conta Conjunta Irmãos** | Poupança compartilhada no balde GUARDAR |

---

## 5. Arquitetura de Informação e Sitemap

[Mantém mesma estrutura do PRD v1.0 - omitida por brevidade]

---

## 6. Jornadas de Usuário

[Mantém mesma estrutura do PRD v1.0 - omitida por brevidade]

---

## 7. Wireframes (ASCII)

[Mantém mesma estrutura do PRD v1.0 - omitida por brevidade]

---

## 8. Requisitos Técnicos

[Mantém mesma estrutura do PRD v1.0 - omitida por brevidade]

---

## 9. Regras de Negócio Brasil

[Mantém mesma estrutura do PRD v1.0 - omitida por brevidade]

---

## 10. Monetização e Pricing

### 10.1 Modelo de Receita (B2B2C)

```
┌─────────────────────────────────────────────────────────────┐
│              FONTES DE RECEITA (GRANIX)                     │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  PRIMÁRIA (70%)                                             │
│  ┌──────────────────────────────────────────────┐          │
│  │  TAXA SaaS MENSAL (por Banco)                │          │
│  │  • Modelo: R$ [X] fixo + R$ [Y] por usuário │          │
│  │  • Exemplo: R$ 50k + R$ 10 por ativo/mês    │          │
│  │  • Previsibilidade total                     │          │
│  └──────────────────────────────────────────────┘          │
│                                                             │
│  SECUNDÁRIA (25%)                                           │
│  ┌──────────────────────────────────────────────┐          │
│  │  REVENUE SHARE COM BANCO                     │          │
│  │  • Interchange compartilhado (% das trx)     │          │
│  │  • Exemplo: 0.25% do volume processado       │          │
│  │  • Incentiva crescimento conjunto            │          │
│  └──────────────────────────────────────────────┘          │
│                                                             │
│  TERCIÁRIA (5%)                                             │
│  ┌──────────────────────────────────────────────┐          │
│  │  OUTROS                                       │          │
│  │  • Cartão personalizado (banco aprova)       │          │
│  │  • Serviços adicionais (API custom, etc)     │          │
│  │  • Parcerias educacionais (sponsor content)  │          │
│  └──────────────────────────────────────────────┘          │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### 10.2 Não Cobramos das Famílias

✅ **Uso gratuito para pais/filhos** - O banco paga a GRANIX, não a família.

Isso é:
- Vantagem competitiva (vs Mozper, Tindin que cobram)
- Melhor modelo (reduz churn)
- Alinhado com proposta de valor (banco investe em educação financeira dos clientes)

---

## 11. Métricas e KPIs

### 11.1 Métricas para GRANIX (B2B Perspective)

| Métrica | Descrição | Target |
|---------|-----------|--------|
| **Bancos onboardados** | Número de bancos parceiros | 3 em 12 meses |
| **AUM por banco** | Assets under management total | R$ 50M+ |
| **MRR B2B** | Receita recorrente mensal dos bancos | R$ 200k em 12 meses |
| **Churn B2B** | Taxa de cancelamento de bancos | < 2% anual |
| **NPS B2B** | Satisfação dos bancos | > 40 |

### 11.2 Métricas para Famílias (B2C Perspective)

| Métrica | Descrição | Target |
|---------|-----------|--------|
| **Famílias ativas** | Agregado de todos os bancos | 50k em 12 meses |
| **DAU/MAU** | Usuários ativos diários/mensais | > 30% |
| **Transações/mês** | Média por conta de filho | > 15 |
| **Tarefas completadas** | Taxa de conclusão | > 70% |
| **NPS** | Net Promoter Score | > 50 |

---

## 12. Plano de MVP

[Mantém mesma estrutura, ajustando timelineconforme B2B2C]

---

## 13. Riscos e Compliance

### 13.1 Diferenças vs PRD v1.0

**Novo Risco B2B2C:**
- Dependência de banco parceiro (contrato é crítico)
- Go-to-market exclusivamente B2B (sem venda direta)
- White-label: reputação vinculada ao banco

**Compliance:**
- SameODOCUMENTAS regras (LGPD, Bacen, etc)
- Agora: assinado pelo Banco (KYC, PIX, etc)
- GRANIX: responsável por educação, potes, segurança

---

## 14. Backlog Inicial

[Mantém mesma estrutura do PRD v1.0]

---

## Anexo A: Glossário

[Mantém mesma estrutura do PRD v1.0]

---

## Anexo B: Referências

- [Greenlight](https://greenlight.com/) - Site oficial
- [Greenlight App Store](https://apps.apple.com/us/app/greenlight-kids-teen-banking/id1049340702)

---

**Fim do Documento**

*Última atualização: Abril 2026*
*Versão: 2.0 (B2B2C)*

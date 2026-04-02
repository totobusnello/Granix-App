# GRANIX — Educacao Financeira para a Nova Geracao Brasileira

> Plataforma B2B2C de educacao financeira familiar. GRANIX fornece a inteligencia (AI, gamificacao, conteudo) como SDK embarcado no app de bancos e instituicoes financeiras parceiras.

## Visao

Transformar a relacao de familias brasileiras com dinheiro atraves de um **ciclo virtuoso** que conecta pais, filhos e instituicoes financeiras:

```
Pai cria tarefa → Filho completa → Pai aprova (abre o app!) → Mesada liberada → 4 Potes → Aprende fazendo → Quer mais!
```

**Principio fundamental:** GRANIX nao movimenta recursos. Toda parte financeira (contas, saldos, transacoes) fica dentro da instituicao financeira parceira. GRANIX gera informacoes e comandos.

## Modelo de Negocio (Pivot v2 — Mar 2026)

| Componente | Descricao |
|------------|-----------|
| **SDK/WebView** | Experiencia GRANIX embarcada no app do banco com skin customizavel |
| **AI Engine** | Personalizacao de conteudo, anti-churn, recomendacao de trilhas |
| **Component Library** | Modulos independentes (Tarefas, 4 Potes, Academy, Gamificacao) |
| **Revenue** | SaaS para banco + revenue share em assinaturas premium |

## Estrutura do Projeto

```
Granix-App/
├── README.md
├── CLAUDE.md                        Instrucoes do projeto
├── index.html                       Landing page
├── teaser.html                      Teaser investidor
│
├── PRD-v2.md                        Product Requirements v2.0
├── api-spec-v2.md                   API Specification v2.0
├── mobile-architecture-v2.md        Mobile Architecture v2.0
├── technical-spec-v2.md             Technical Spec v2.0
│
├── docs/
│   ├── decks/                       Pitch decks e apresentacoes
│   ├── arquitetura/                 Diagramas C4/UML + flow diagrams
│   ├── estrategia/                  Pivot strategy, roteiros, design docs
│   ├── investidor/                  Material para investidores
│   └── scripts/                     Scripts de geracao de decks
│
├── branding/                        Identidade visual, logo, naming
├── wireframes/                      Wireframes dos modulos (HTML)
└── _archive/                        Documentos pre-pivot v1
```

## Status do Projeto

| Fase | Status | Descricao |
|------|--------|-----------|
| Pesquisa de mercado | Completo | Greenlight benchmark, concorrentes BR, LGPD/ECA Digital |
| Pivot v2 (B2B2C) | Completo | Modelo component library + AI engine |
| Documentacao tecnica v2 | Completo | PRD, API spec, tech spec, mobile arch |
| Branding | Completo | Logo, identidade visual, naming |
| Wireframes | Completo | Modulos tarefas, gamificacao, academy |
| Pitch parceiros | Completo | Deck institucional, jornada interativa |
| Arquitetura tecnica | Completo | Diagramas C4, fluxos, seguranca |
| Modelo financeiro | Completo | Projecoes SaaS + revenue share |
| Conversas com parceiros | Em andamento | Apresentacao para IFs |
| Desenvolvimento MVP | Pendente | Apos fechamento de parceria |

## Documentacao Chave

- [PRD v2.0](PRD-v2.md) — Product Requirements Document atualizado
- [API Spec v2.0](api-spec-v2.md) — Especificacao de API
- [Tech Spec v2.0](technical-spec-v2.md) — Especificacao tecnica
- [Mobile Arch v2.0](mobile-architecture-v2.md) — Arquitetura mobile
- [Pitch Partners](docs/decks/pitch-partners-v2.html) — Deck para IFs
- [Jornada Trilha Broto](docs/decks/jornada-trilha-broto.html) — Experiencia interativa
- [Arquitetura](docs/arquitetura/) — Diagramas C4 e fluxos
- [Strategy Pivot](docs/estrategia/strategy-pivot-saas-xp.md) — Documento do pivot v2

---

**Fundador:** Toto Busnello (CEO/CTO/CPO)
**Versao:** 2.0 (Pivot B2B2C — Mar 2026)

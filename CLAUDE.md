# GRANIX — Instrucoes do Projeto

## O que e o GRANIX

Plataforma B2B2C de educacao financeira familiar. GRANIX fornece SDK + AI Engine para bancos e instituicoes financeiras (IFs) embarcarem no app deles.

**Principio #1:** GRANIX nunca movimenta dinheiro. So gera informacoes e comandos. Toda parte financeira fica dentro da IF.

**Principio #2:** O Ciclo Virtuoso (Tarefas → Mesada → 4 Potes) e o BACKBONE do produto, nao uma feature. Deve ser central em todos os materiais.

## Modelo de Negocio

- **SDK/WebView** embarcado no app do banco com skin customizavel
- **AI Engine** para personalizacao, anti-churn, recomendacao
- **Revenue:** SaaS mensal para banco + revenue share em assinaturas premium
- Revenue share entre GRANIX (70%) e IF (30%) — modelo sugerido, a ser negociado

## Documentos Tecnicos v2.0 (na raiz)

- `PRD-v2.md` — Product Requirements Document
- `api-spec-v2.md` — API Specification
- `technical-spec-v2.md` — Technical Specification
- `mobile-architecture-v2.md` — Mobile Architecture

## Estrutura da Pasta

```
/                        Raiz: landing pages + docs tecnicos v2
docs/decks/              Pitch decks e apresentacoes (HTML, PPTX, PDF)
docs/arquitetura/        Diagramas C4/UML (PNG + PPTX) + flow diagrams (Mermaid)
docs/estrategia/         Pivot strategy, roteiros, design docs
docs/investidor/         Material para investidores
docs/scripts/            Scripts Python de geracao de decks
branding/                Identidade visual, logo, naming
wireframes/              Wireframes interativos dos modulos
_archive/v1-pre-pivot/   Documentos obsoletos do projeto v1
_archive/research/       Pesquisa de mercado e regulacao (pre-pivot, dados ainda validos)
```

## Stack Tecnico

- Frontend: React Native / WebView (SDK embarcavel)
- Backend: Node.js + TypeScript
- Database: PostgreSQL + Prisma
- AI: Python
- Deploy: Vercel / AWS
- Integracao com IF: REST API + OAuth2 + mTLS

## Compliance

- LGPD, ECA Digital (Lei 15.211/2025), BACEN, Open Finance Brasil
- Dados de menores requerem consentimento parental explicito

## Convencoes

- Apresentacoes sao criadas em HTML e convertidas via Chrome DevTools MCP + python-pptx
- Documentos de estrategia em Markdown
- Branding segue identidade em branding/granix-brand-identity.md
- Portugues brasileiro em todos os materiais de cliente

## Status Atual (Abr 2026)

- Pivot v2 concluido, modelo B2B2C definido
- Documentacao tecnica v2 completa (PRD, API, tech spec, mobile arch)
- Materiais de pitch completos (deck, jornada, arquitetura)
- Em conversas com instituicoes financeiras parceiras
- Proximo passo: fechar parceria e iniciar desenvolvimento MVP

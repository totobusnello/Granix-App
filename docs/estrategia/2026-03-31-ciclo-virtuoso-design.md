# Design Spec: Ciclo Virtuoso Familiar — Elevacao de Tarefas/Mesada no GRANIX

**Data:** 2026-03-31
**Deadline:** Apresentacao amanha (2026-04-01)
**Aprovado por:** Toto

---

## Contexto

O ciclo Tarefa→Aprovacao→Mesada→4 Potes e o motor central do GRANIX, mas esta sub-representado no pitch deck (mencionado como feature, nao como core) e fragmentado no strategy doc (aparece em ~15 lugares sem secao unificada). Precisamos elevar isso para espinha dorsal da narrativa.

## Escopo — 3 Entregaveis

### 1. Pitch Deck HTML (pitch-partners-v2.html)

**Mudancas:**
- **Slide novo 5:** "O Motor: Ciclo Virtuoso Familiar" — diagrama circular grande mostrando o loop completo (Tarefa criada pelo pai → Crianca completa → Pai aprova (abre app do banco!) → Mesada liberada → Crianca divide nos 4 Potes → Aprende fazendo → Quer mais)
- **Slide novo 6:** "3 Camadas de Valor" — Para a FAMILIA (educacao pratica), Para a INSTITUICAO (DAU organico, pai abrindo app diariamente), vs CONCORRENCIA (ninguem tem ciclo completo)
- **Slides de modulos reescritos:** Cada modulo explicado como parte do ciclo (Academy ENSINA → Tarefas PRATICAM → 4 Potes APLICAM → Gamificacao RECOMPENSA)
- **Renumerar slides subsequentes**
- **Manter:** tema branco, GRANIX branding, portugues com acentos corretos

### 2. Strategy Doc (strategy-pivot-saas-xp.md)

**Mudancas:**
- **Nova secao de primeiro nivel:** "Motor de Engajamento Familiar" (~200-300 linhas)
  - Conceito central do ciclo
  - Mecanica detalhada (tipos de tarefas, fluxo aprovacao, liberacao mesada, distribuicao 4 Potes)
  - Triplice valor (familia, instituicao, competitivo)
  - Metricas do ciclo
  - Integracao com outros modulos
- **Posicao:** Apos secao de onboarding/user flow, antes dos modulos especificos
- **Referencias existentes:** mantidas, agora apontam para secao central

### 3. Jornada Interativa HTML (NOVO arquivo)

**Arquivo:** `docs/jornada-trilha-broto.html`
**Formato:** Scroll storytelling, HTML unico, sem dependencias externas
**Tema:** Alinhado com pitch deck (branco + cores GRANIX)

**10 Cenas:**

#### PARTE 1: BASTIDORES (como criamos)

**Cena 1 — "Tudo comeca com um grao"**
- Problema: crianca recebe mesada mas nao sabe o que fazer
- Dado: 72% dos pais nao sabem ensinar educacao financeira
- Visual: ilustracao conceitual do gap

**Cena 2 — "Desenhando a Trilha Broto (9-11 anos)"**
- Curriculo espiral: mapa de conceitos por idade
- Arvore de licoes com "Minha Primeira Mesada" em destaque
- Alinhamento BNCC visual

**Cena 3 — "A Fabrica de Conteudo: 6 Agentes AI"**
- Pipeline visual: Gap Detector → Generator → Pedagogo Digital → Revisao Humana → A/B Tester → Optimizer
- Callout: "90% reducao custo, 50+ licoes/mes"

**Cena 4 — "Personalizacao Invisivel"**
- Perfis AI (Explorer, Focused, Social...)
- Mesma licao em 3 versoes (futebol, games, musica)

#### PARTE 2: EXPERIENCIA DO USUARIO (como a familia vive)

**Cena 5 — "Joao, 10 anos, abre o app"**
- Onboarding simulado: 5 telas, 3 min
- Avatar, quiz rapido, primeira trilha
- Aha moment: badge + trilha personalizada

**Cena 6 — "O Ciclo Virtuoso comeca"**
- Pai cria tarefa: "Arrumar o quarto toda manha"
- Mockup tela do pai (TaskCreator)
- Push notification pro Joao

**Cena 7 — "Joao completa a tarefa"**
- Mockup tela do Joao (checklist, foto de prova)
- Pai aprova em 1 tap
- Mesada R$10 liberada → animacao 4 Potes

**Cena 8 — "A magica: aprender fazendo"**
- Joao dividiu R$10 nos Potes
- App sugere licao contextual
- Quiz interativo simulado (5 min)
- Badge: "Mestre dos Potes"

**Cena 9 — "Uma semana depois"**
- Dashboard do pai: progresso, insights AI
- "Joao completa tarefas 40% mais rapido quando voce aprova em <1h"
- Evolucao semana 1 vs semana 4

**Cena 10 — "E para a instituicao?"**
- Metricas: DAU organico, LTV familiar, cross-sell
- "Isso tudo roda DENTRO do seu app"
- Call to action

**Requisitos Visuais:**
- Cada cena ocupa ~80-100vh
- Transicoes suaves com scroll (CSS scroll-snap ou intersection observer)
- Mockups de celular estilizados (CSS, nao imagens)
- Icones SVG inline e animacoes CSS
- Paleta: branco, GRANIX green (#2D5016 ou similar), accent colors
- Tipografia: system fonts (nao depender de Google Fonts carregando)
- Responsivo mas otimizado para apresentacao em tela grande (16:9)

## Restricoes

- Tudo em HTML/CSS/JS vanilla — zero dependencias externas
- Portugues brasileiro com acentos corretos em TODOS os textos
- Deve funcionar offline (abrir arquivo local no browser)
- Prioridade: impacto visual + conteudo preciso > perfeicao de codigo

## Ordem de Execucao

1. Strategy doc (fundacao conceitual)
2. Pitch deck (narrativa reestruturada)
3. Jornada interativa (peca de impacto)

Itens 1 e 2 podem ser parcialmente paralelizados. Item 3 depende do conteudo refinado em 1 e 2.

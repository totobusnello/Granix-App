# GRANIX - Pivot Estrategico v2: Component Library + AI Content Engine

**Data**: 23 de Marco de 2026
**Status**: Em planejamento
**Versao**: 2.0

---

## 1. RESUMO EXECUTIVO

GRANIX pivota de "plataforma SaaS com integracao via API" para **component library white-label + AI content engine** que roda **dentro** do ambiente seguro da instituicao financeira.

**Modelo**: Assinatura cobrada do cliente final pela instituicao, com revenue share 70/30 (GRANIX/instituicao).
**Produto core**: Component Library (React/RN) + AI Content Engine + Gamification SDK.
**Marca**: 100% da instituicao financeira, com selo "by GRANIX" ou "powered by GRANIX".
**AI-first**: Personalizacao, predicao de comportamento, predicao de churn e criacao automatizada de conteudo.

### O que muda (v1 → v2)

| Aspecto | v1 (SaaS Layer) | v2 (Component Library + AI) |
|---------|-----------------|----------------------------|
| Arquitetura | App SaaS com API ao banco | **Components embeddaveis no app do banco** |
| Integracao | API com core bancario | **Zero integracao** — banco consome library |
| Quem paga | Familia paga GRANIX | **Familia paga via billing da instituicao** |
| Revenue | Subscription + revenue share 70/30 | **Assinatura split 70% GRANIX / 30% instituicao** |
| Produto | 3 modulos como app | **Component Library + AI Engine + SDK** |
| AI | Ausente | **Pilar central do produto** |
| Escopo | XP-first | **White-label desde o inicio** para qualquer instituicao |
| Marca | App GRANIX | **Marca da instituicao**, selo "by GRANIX" |
| Dados financeiros | GRANIX processava | **GRANIX nunca ve dados financeiros** |
| Compliance | Dependia do parceiro | **Zero compliance** — e software puro |

### Por que este pivot

**Insight critico**: Nenhuma instituicao financeira brasileira vai abrir seu ambiente seguro de transacao para uma API externa. Este ponto gera friccao insuperavel que inviabiliza qualquer modelo que dependa de integracao com core bancario. A solucao: nao integrar — **embeddar**.

---

## 2. O PROBLEMA QUE GRANIX RESOLVE

### A Realidade do Mercado Financeiro Brasileiro

Instituicoes financeiras (XP, Nubank, Inter, BTG, C6) ja oferecem contas para menores. Todas tem:
- Conta transacional (PIX, cartao de debito)
- Investimentos (em graus variados)
- App funcional

**Nenhuma tem**:
- Experiencia adaptada para jovens
- Educacao financeira interativa
- Gamificacao
- Sistema de tarefas/recompensas familiar
- Framework de educacao financeira (4 Potes)
- Personalizacao por AI

### Por que nao constroem internamente?

1. **Nao e core business** — bancos fazem banking, nao edtech
2. **Expertise ausente** — gamificacao + pedagogia + AI e uma combinacao rara
3. **Custo de oportunidade** — time de produto focado em features bancarias
4. **Conteudo e continuo** — requer equipe dedicada de pedagogos + AI
5. **AI e complexa** — predicao de comportamento juvenil e dominio especializado

### A Barreira de Seguranca

Instituicoes financeiras operam em ambientes regulados com requisitos rigidos:
- **Segregacao de dados** — dados de clientes nao saem do perimetro
- **Auditoria** — toda interacao com dados e rastreada
- **Compliance BCB/CVM** — qualquer acesso externo requer aprovacao regulatoria
- **Risco reputacional** — vazamento de dados de menores e catastrofico

**Conclusao**: O unico modelo viavel e entregar software que roda DENTRO do ambiente deles, sem acesso a dados financeiros.

---

## 3. PRODUTO: COMPONENT LIBRARY + AI ENGINE

### Arquitetura

```
┌─────────────────────────────────────────────────────┐
│  APP DA INSTITUICAO FINANCEIRA (ambiente seguro)    │
│                                                     │
│  ┌─────────────────────────────────────────────┐    │
│  │  GRANIX COMPONENT LIBRARY (embeddado)       │    │
│  │                                             │    │
│  │  ┌──────────┐ ┌──────────┐ ┌────────────┐  │    │
│  │  │ Tarefas  │ │ Academy  │ │Gamificacao │  │    │
│  │  │   UI     │ │   UI     │ │    UI      │  │    │
│  │  └──────────┘ └──────────┘ └────────────┘  │    │
│  │                                             │    │
│  │  ┌──────────────────────────────────────┐   │    │
│  │  │  4 POTES (Gastar/Guardar/Doar/Inv.) │   │    │
│  │  │  Framework visual — zero transacao   │   │    │
│  │  └──────────────────────────────────────┘   │    │
│  │                                             │    │
│  └──────────┬──────────────────────────────────┘    │
│             │ callbacks / eventos                    │
│  ┌──────────▼──────────────────────────────────┐    │
│  │  BACKEND DA INSTITUICAO                     │    │
│  │  (contas, transacoes, investimentos)        │    │
│  │  Responsabilidade 100% da instituicao       │    │
│  └─────────────────────────────────────────────┘    │
│                                                     │
└───────────────────────┬─────────────────────────────┘
                        │ HTTPS (conteudo + AI,
                        │ sem dados financeiros)
┌───────────────────────▼─────────────────────────────┐
│  GRANIX CLOUD (AI Engine + Content CDN)             │
│                                                     │
│  ┌──────────┐ ┌──────────┐ ┌────────────────────┐  │
│  │ AI       │ │ Content  │ │ Analytics          │  │
│  │ Engine   │ │ CDN      │ │ (comportamento,    │  │
│  │          │ │          │ │  sem dados PII)    │  │
│  └──────────┘ └──────────┘ └────────────────────┘  │
│                                                     │
└─────────────────────────────────────────────────────┘
```

**Principio fundamental**: GRANIX Cloud recebe apenas dados de comportamento anonimizados (licoes completadas, tempo de uso, padroes de engajamento). **Zero dados financeiros, zero PII**.

---

### Fluxo de Uso: Da Ativacao ao Loop Diario

O fluxo de uso e desenhado para que em **3 minutos** o sistema se molde ao usuario e entregue uma experiencia personalizada desde o primeiro segundo.

---

#### ETAPA 0: Ativacao (feita pela instituicao)

A instituicao financeira ativa o GRANIX para uma familia dentro do seu app. O pai ve a opcao "Educacao Financeira" ou "Programa Jovem" (nome definido pela instituicao) e toca para comecar.

```
[App da Instituicao]
  └── "Programa Jovem" (ou nome white-label)
       └── Ativa GRANIX → Onboarding inicia
```

---

#### ETAPA 1: Onboarding — "Vamos conhecer sua familia" (~3 minutos)

O onboarding e uma experiencia fluida, visual e rapida. Nao e um formulario — e uma conversa guiada com animacoes e feedback instantaneo.

##### Tela 1 — Familia (30 segundos)

```
┌─────────────────────────────────┐
│                                 │
│   👋 Ola! Vamos comecar.       │
│                                 │
│   Quantos filhos participam?    │
│                                 │
│   ┌───┐  ┌───┐  ┌───┐  ┌───┐  │
│   │ 1 │  │ 2 │  │ 3 │  │ 4+│  │
│   └───┘  └───┘  └───┘  └───┘  │
│                                 │
│   Para cada filho:              │
│   Nome: [________]  Idade: [__] │
│                                 │
│              [Continuar →]      │
└─────────────────────────────────┘
```

**AI ja faz**: Detecta faixa etaria (Semente/Broto/Arvore/Floresta) automaticamente. Se tem mais de 1 filho, ativa features de ranking familiar.

##### Tela 2 — Perfil do Pai (30 segundos)

```
┌─────────────────────────────────────┐
│                                     │
│   Como e a relacao com dinheiro     │
│   na sua familia hoje?              │
│                                     │
│   ○ Ja dou mesada fixa              │
│   ○ Dou dinheiro quando pedem       │
│   ○ Ainda nao converso sobre isso   │
│   ○ Quero comecar agora             │
│                                     │
│   O que mais te preocupa?           │
│   (escolha ate 2)                   │
│                                     │
│   ┌──────────┐ ┌──────────────┐     │
│   │ Consumo  │ │ Nao saber    │     │
│   │ impulsivo│ │ poupar       │     │
│   └──────────┘ └──────────────┘     │
│   ┌──────────┐ ┌──────────────┐     │
│   │ Nao      │ │ Preparar pro │     │
│   │ entender │ │ futuro       │     │
│   │ dinheiro │ │              │     │
│   └──────────┘ └──────────────┘     │
│                                     │
│              [Continuar →]          │
└─────────────────────────────────────┘
```

**AI ja faz**: Define tom do conteudo (mais basico se "ainda nao converso", mais avancado se "ja dou mesada"). Prioriza modulos baseado na preocupacao (consumo impulsivo → modulo "Querer vs Precisar" primeiro).

##### Tela 3 — Perfil do Jovem (60 segundos) — GAMIFICADA

Aqui o filho assume. A tela muda de tom — cores vibrantes, linguagem jovem, interacao divertida.

```
┌─────────────────────────────────────┐
│                                     │
│   🎮 E ai, [Nome]! Bora descobrir  │
│   seu perfil financeiro?            │
│                                     │
│   O que voce mais curte?            │
│   (toca nos que voce gosta)         │
│                                     │
│   ⚽ Esportes    🎮 Games           │
│   🎵 Musica      🎬 Videos          │
│   📱 Tech        🎨 Arte            │
│   📚 Ciencia     🛍️ Moda            │
│                                     │
│   Se voce ganhasse R$100 agora,     │
│   o que faria?                      │
│                                     │
│   🛒 Comprava algo legal            │
│   🐷 Guardava pro futuro            │
│   🎁 Dava um presente               │
│   📈 Tentava fazer render            │
│                                     │
│              [Continuar →]          │
└─────────────────────────────────────┘
```

**AI ja faz**: Define contexto para conteudo (futebol, games, etc.). A resposta do R$100 calibra a tendencia natural dos 4 Potes (quem escolhe "comprava" precisa mais de Guardar; quem escolhe "tentava render" esta pronto para Investir mais cedo).

##### Tela 4 — Mini-Quiz Relampago (60 segundos)

5 perguntas rapidas que calibram o nivel de conhecimento. Formato visual, nao textual.

```
┌─────────────────────────────────────┐
│                                     │
│   ⚡ Quiz Relampago! 5 perguntas    │
│   Responde rapido, sem medo de      │
│   errar — isso ajuda a montar       │
│   SUA trilha!                       │
│                                     │
│   1/5: O que e "guardar dinheiro"?  │
│                                     │
│   🅰️ Esconder debaixo do colchao   │
│   🅱️ Colocar em um lugar seguro    │
│      pra usar depois               │
│   🅲️ Nunca gastar nada              │
│                                     │
│   ████████░░ 1/5                    │
│                                     │
└─────────────────────────────────────┘
```

As 5 perguntas sao adaptativas por faixa etaria:

| Faixa | Pergunta exemplo | Calibra |
|-------|-----------------|---------|
| Semente (6-8) | "O que e mais caro: um sorvete ou uma bicicleta?" | Nocao de valor |
| Broto (9-11) | "Se voce guardar R$10/semana, quanto tera em 1 mes?" | Calculo basico |
| Arvore (12-14) | "O que sao juros?" | Conceitos financeiros |
| Floresta (15-17) | "Qual a diferenca entre renda fixa e renda variavel?" | Conhecimento de mercado |

**AI ja faz**: Score do quiz calibra o ponto de partida no curriculo. Se acertou 5/5, pula licoes basicas. Se acertou 1/5, comeca do zero com formato mais visual.

##### Tela 5 — Momento "Aha!" (30 segundos) ⭐

O momento magico. A AI ja processou tudo e apresenta a jornada personalizada.

```
┌──────────────────────────────────────────┐
│                                          │
│   ✨ Pronto, [Nome]!                     │
│   Sua jornada esta montada.              │
│                                          │
│   ┌────────────────────────────────────┐ │
│   │  Seu perfil: EXPLORADOR 🧭         │ │
│   │  Nivel: Broto (9-11 anos)          │ │
│   │  Interesse: Games + Esportes       │ │
│   │  Conhecimento: Intermediario       │ │
│   └────────────────────────────────────┘ │
│                                          │
│   📋 Sua trilha personalizada:           │
│                                          │
│   ✅ Proximo: "Quanto custa um jogo?"   │
│      (7 min, simulador)                 │
│   🔜 Depois: "Seu primeiro objetivo"    │
│   🔜 Desafio: "Economize R$20 essa      │
│      semana"                             │
│                                          │
│   🏆 Seu primeiro badge:                │
│   ┌──────────────┐                       │
│   │  🌱 SEMENTE  │                       │
│   │  "Primeiro    │                       │
│   │   passo"      │                       │
│   └──────────────┘                       │
│   Voce ganhou 10 XP!                     │
│                                          │
│   Seus 4 Potes (comece a preencher!):    │
│   🛒 Gastar [____] 🐷 Guardar [____]    │
│   🎁 Doar   [____] 📈 Investir [____]   │
│                                          │
│          [🚀 Comecar primeira licao!]    │
│                                          │
└──────────────────────────────────────────┘
```

**O que acontece nesse momento:**
- Jovem ve que o sistema **o entende** (interesse, nivel, perfil)
- Ja ganhou algo (badge + XP) — dopamina imediata
- Trilha parece alcancavel e relevante (nao generica)
- 4 Potes aparecem vazios — cria vontade de preencher
- Call-to-action claro: comecar primeira licao
- Pai recebe em paralelo: "Joao comecou! Crie a primeira tarefa para ele."

---

#### ETAPA 2: Primeira Sessao — "Hook Imediato" (5-7 minutos)

A primeira sessao e desenhada para **viciar**. O jovem deve sair com:

| Conquista | Tempo | Sentimento |
|-----------|:-----:|-----------|
| 1 licao completada (contextualizada) | 5 min | "Isso e sobre o que eu gosto!" |
| 1 quiz passado | 2 min | "Eu sei coisas!" |
| 1 badge ganho | Instantaneo | "Quero mais!" |
| 1 objetivo definido nos 4 Potes | 1 min | "Tenho um plano!" |
| XP acumulado + nivel visivel | Instantaneo | "Estou progredindo!" |
| Notificacao para o pai | Automatico | Pai engaja tambem |

**Primeira licao e SEMPRE contextualizada ao interesse:**

| Interesse | Primeira licao | Formato |
|-----------|---------------|---------|
| Games | "Quanto custa um jogo? O preco real das skins" | Simulador interativo |
| Futebol | "O salario dos jogadores: de onde vem o dinheiro?" | Historia animada |
| Musica | "Como artistas ganham dinheiro com streaming?" | Infografico interativo |
| Tech | "Quanto custa criar um app?" | Cenario interativo |
| Moda | "Fast fashion vs qualidade: a conta real" | Quiz de comparacao |

---

#### ETAPA 3: Loop Semanal — Engajamento Sustentavel

Apos o onboarding, a AI gerencia o ritmo do usuario. O loop semanal e o motor de retencao.

##### Ciclo Semanal Tipico

```
SEGUNDA
  └── Notificacao: "Desafio da semana disponivel!" (AI-personalizado)
  └── Pai: Criar/renovar tarefas da semana

TERCA-QUINTA
  └── 1-2 licoes curtas (5-8 min cada)
  └── AI ajusta baseado em engajamento de segunda

SEXTA
  └── Quiz semanal (revisao dos conceitos da semana)
  └── Resultado + XP + possivel badge

SABADO
  └── Desafio pratico do mundo real
  └── Ex: "Va ao supermercado e compare 3 marcas de cereal. Qual e melhor custo-beneficio?"

DOMINGO
  └── "Family time": Atividade pai + filho
  └── Ex: "Conversem sobre o objetivo do pote Guardar. Voces acham que vao conseguir?"
  └── Resumo semanal para o pai
```

##### Cadencia por Faixa Etaria

| Faixa | Sessoes/semana | Duracao/sessao | Formato predominante |
|-------|:--------------:|:--------------:|---------------------|
| Semente (6-8) | 3-4 | 3-5 min | Historias + jogos simples |
| Broto (9-11) | 4-5 | 5-7 min | Simuladores + quizzes |
| Arvore (12-14) | 4-5 | 7-10 min | Simuladores + cenarios |
| Floresta (15-17) | 3-5 | 8-12 min | Cenarios + analise + debates |

**AI ajusta dinamicamente**: Se o usuario engaja mais, aumenta frequencia. Se engaja menos, reduz para nao saturar. Qualidade > quantidade.

##### Triggers de Engajamento (AI-Managed)

A AI envia notificacoes/estimulos baseado em sinais:

| Trigger | Condicao | Acao |
|---------|---------|------|
| Streak em risco | 20h sem sessao (usuario diario) | "Faltam 4h pro seu streak de [N] dias! 🔥" |
| Badge proximo | Falta 1 acao para desbloquear badge | "Voce esta a 1 licao do badge [X]! 🏆" |
| Novo conteudo contextual | Evento real detectado (Copa, Black Friday) | "Desafio especial: [tema do evento] ⚡" |
| Pai inativo | Pai nao interagiu ha 3+ dias | Para o pai: "[Filho] completou 3 tarefas esperando aprovacao" |
| Marco de aprendizado | Completou modulo inteiro | Celebracao especial + badge + notificacao para o pai |
| Ranking familiar | Irmao ultrapassou no ranking | "Seu irmao te passou no ranking! Desafio de recuperacao? 😄" |
| Momento ensinavel | Contexto detectado (inicio do mes, ferias) | "Comeco do mes! Hora de planejar o orcamento 📋" |

---

#### ETAPA 4: Loop Mensal — Evolucao e Recompensa

##### Fechamento do Mes

```
┌──────────────────────────────────────────┐
│                                          │
│   📊 Resumo de [Mes] — [Nome]           │
│                                          │
│   Licoes completadas: 12 (+3 vs mes ant)│
│   Quizzes: 8 (media 78%)               │
│   Desafios praticos: 3                  │
│   Streak maximo: 15 dias 🔥             │
│   XP ganho: 450                         │
│   Nivel: Broto ████████░░ 82%           │
│                                          │
│   4 Potes (evolucao visual):            │
│   🛒 Gastar  ██████░░ R$120 / R$200    │
│   🐷 Guardar █████████ R$320 / R$500 ✨│
│   🎁 Doar    ████░░░░ R$30 / R$50      │
│   📈 Investir███████░ R$200 / R$1000   │
│                                          │
│   💡 Destaque do mes:                   │
│   "Voce aprendeu juros compostos e      │
│    ja sabe calcular quanto seu           │
│    dinheiro rende em 1 ano!"             │
│                                          │
│   🏆 Badges novos: [Calculista] [Streak]│
│                                          │
│   Proximo mes: Modulo "Investimentos"    │
│   Voce esta pronto! 🚀                  │
│                                          │
└──────────────────────────────────────────┘
```

##### Para o Pai — Relatorio Mensal

```
┌──────────────────────────────────────────────┐
│                                              │
│   📋 Relatorio Mensal — [Nome do Filho]      │
│                                              │
│   Aprendizado:                               │
│   • Completou modulo "Orcamento Inteligente" │
│   • Destaque em: juros compostos (92% quiz)  │
│   • Precisa reforcar: comparacao de precos   │
│                                              │
│   Comportamento financeiro:                  │
│   • Guardou R$120 no pote Guardar (+40%)     │
│   • Meta "Bicicleta" a 64% do objetivo      │
│   • Tendencia: mais equilibrado entre potes  │
│                                              │
│   Engajamento:                               │
│   • 18 sessoes este mes (↑ 20% vs anterior)  │
│   • Horario preferido: 19h-20h              │
│   • Formato preferido: simuladores           │
│                                              │
│   💡 Sugestao para voce:                     │
│   "Joao esta quase na meta da bicicleta.     │
│    Que tal criar um desafio-bonus de R$50    │
│    se ele completar o modulo de              │
│    Investimentos este mes?"                  │
│                                              │
│   Comparacao (anonima):                      │
│   Seu filho esta no top 25% de progresso     │
│   para a faixa 9-11 anos 🌟                 │
│                                              │
└──────────────────────────────────────────────┘
```

---

#### ETAPA 5: Marcos da Jornada — Momentos Especiais

Ao longo da jornada, existem marcos que geram celebracoes especiais:

| Marco | Quando | Celebracao |
|-------|--------|-----------|
| **Primeiro Badge** | Onboarding | Animacao especial + notificacao para pai |
| **Primeiro Objetivo Alcancado** | Quando pote atinge meta | Animacao de "desbloqueio" + badge exclusivo + pai notificado |
| **Mudanca de Faixa** | Semente→Broto, etc. | Cerimonia de "graduacao" com novo avatar + resumo do aprendido |
| **Streak de 30 dias** | 30 sessoes consecutivas | Badge raro + destaque no ranking familiar |
| **100 Licoes** | Acumula 100 licoes completadas | Badge "Centenario" + retrospectiva da jornada |
| **Primeiro Investimento Real** | Pai confirma investimento no mundo real | Badge "Investidor" + licao especial sobre "seu dinheiro trabalhando" |
| **Aniversario GRANIX** | 1 ano na plataforma | Retrospectiva animada ("1 ano atras voce nao sabia o que era juros...") |
| **Pre-18** | 6 meses antes de completar 18 | Trilha especial "Adulto Financeiro" preparando para conta adulta |

##### Transicao de Faixa (Cerimonia de Graduacao)

Um dos momentos mais importantes — o jovem sente que **cresceu**:

```
┌──────────────────────────────────────────┐
│                                          │
│   🎓 GRADUACAO!                          │
│                                          │
│   [Nome], voce evoluiu de                │
│                                          │
│   🌱 SEMENTE  →  🌿 BROTO               │
│                                          │
│   Retrospectiva:                         │
│   • 25 licoes completadas               │
│   • 12 quizzes (media 81%)              │
│   • 5 desafios praticos no mundo real    │
│   • 8 badges conquistados               │
│                                          │
│   Voce aprendeu:                         │
│   ✅ O que e dinheiro                    │
│   ✅ Querer vs Precisar                  │
│   ✅ Como guardar com objetivo           │
│   ✅ Generosidade financeira             │
│   ✅ Sua primeira mesada consciente      │
│                                          │
│   Agora voce esta pronto para:           │
│   📊 Orcamentos de verdade              │
│   🧮 Calculos financeiros               │
│   🎯 Metas mais ambiciosas              │
│   💡 Empreendedorismo basico             │
│                                          │
│   Novo avatar desbloqueado! 🌿           │
│                                          │
│        [🚀 Comecar fase Broto!]         │
│                                          │
└──────────────────────────────────────────┘
```

---

#### Resumo do Fluxo Completo

```
ATIVACAO (Instituicao)
  │
  ▼
ONBOARDING (3 minutos)
  │ Tela 1: Familia (30s)
  │ Tela 2: Perfil do pai (30s)
  │ Tela 3: Perfil do jovem — gamificado (60s)
  │ Tela 4: Mini-quiz relampago (60s)
  │ Tela 5: Momento "Aha!" — trilha + badge + 4 potes (30s)
  │
  ▼
PRIMEIRA SESSAO (5-7 min)
  │ Licao contextualizada + quiz + badge + objetivo nos 4 Potes
  │
  ▼
LOOP SEMANAL
  │ Seg: Desafio da semana
  │ Ter-Qui: 1-2 licoes curtas
  │ Sex: Quiz semanal + XP
  │ Sab: Desafio pratico real
  │ Dom: Family time + resumo
  │
  ▼
LOOP MENSAL
  │ Resumo do jovem + relatorio do pai
  │ Ajuste de trilha + novos objetivos
  │
  ▼
MARCOS (ao longo da jornada)
  │ Badges, graduacoes, streaks, aniversarios
  │ Cada marco → celebracao + reengajamento
  │
  ▼
TRANSICAO 18 ANOS
  │ Trilha "Adulto Financeiro"
  │ Prepara para conta adulta na instituicao
  │ Retencao do cliente para o parceiro ✅
```

---

### Motor de Engajamento Familiar

---

#### 3.1 Conceito Central

O Motor de Engajamento Familiar nao e uma feature. E a **espinha dorsal** do produto inteiro.

Enquanto outras plataformas de educacao financeira ensinam conceitos em abstrato, GRANIX conecta **trabalho, recompensa e aprendizado** em um ciclo continuo onde a crianca aprende fazendo — com dinheiro real, tarefas reais e aprovacao do pai em tempo real.

O ciclo funciona assim:

```
┌─────────────────────────────────────────────────────────────────┐
│                                                                 │
│                  MOTOR DE ENGAJAMENTO FAMILIAR                  │
│                                                                 │
│   ┌──────────────┐      cria tarefa      ┌──────────────────┐  │
│   │              │ ───────────────────►  │                  │  │
│   │     PAI      │                       │   TAREFA CRIADA  │  │
│   │  (app banco) │ ◄───────────────────  │  (tipo + valor)  │  │
│   │              │  abre app p/ aprovar  └────────┬─────────┘  │
│   └──────┬───────┘                               │             │
│          │ aprova (1 tap)                         │ notificacao │
│          │                                        ▼             │
│          │                              ┌──────────────────┐   │
│   ┌──────▼───────┐                      │                  │   │
│   │   MESADA     │                      │    CRIANCA       │   │
│   │  LIBERADA    │ ◄──────────────────  │   COMPLETA       │   │
│   │ automatica   │   prova (foto/check) │   TAREFA         │   │
│   └──────┬───────┘                      └──────────────────┘   │
│          │                                                      │
│          ▼                                                      │
│   ┌──────────────────────────────────────────────────────┐     │
│   │  DIVISAO NOS 4 POTES (crianca decide, AI sugere)     │     │
│   │                                                      │     │
│   │   🛒 Gastar    🐷 Guardar    🎁 Doar    📈 Investir  │     │
│   └──────────────────────────────┬───────────────────────┘     │
│                                  │                              │
│                                  ▼                              │
│                       ┌──────────────────┐                     │
│                       │   APRENDE FAZENDO│                     │
│                       │  quer mais!      │                     │
│                       │  nova tarefa ──► │ (ciclo reinicia)    │
│                       └──────────────────┘                     │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

**Por que funciona:**

| Principio | O que acontece | Resultado |
|-----------|---------------|-----------|
| Trabalho precede recompensa | Crianca entende que dinheiro e conquistado, nao dado | Mentalidade financeira saudavel desde cedo |
| Aprovacao do pai e obrigatoria | Pai abre o app do banco para aprovar | DAU organico para a instituicao |
| Recompensa e imediata | Mesada liberada no momento da aprovacao | Associacao positiva trabalho → dinheiro |
| Distribuicao consciente | Crianca divide nos 4 Potes com orientacao da AI | Educacao financeira aplicada, nao teorica |
| Loop fechado | Aprender → ganhar → dividir → querer mais | Retencao natural, sem necessidade de push |

Este ciclo e o que diferencia GRANIX de toda a concorrencia: **nenhum competitor tem o loop completo.**

---

#### 3.2 Mecanica Detalhada

##### Tipos de Tarefa

Existem tres categorias de tarefas, cada uma com proposito pedagogico distinto:

**1. Tarefas Domesticas**

A crianca aprende que contribuir com a casa tem valor. Tarefas praticas do cotidiano.

| Tarefa | Faixa recomendada | Valor sugerido | Frequencia |
|--------|:-----------------:|:--------------:|:----------:|
| Arrumar o quarto | Semente (6-8) | R$2 - R$5 | Diaria |
| Ajudar na cozinha (mesa, louça) | Semente (6-8) | R$3 - R$8 | Diaria |
| Passear com o cachorro | Broto (9-11) | R$5 - R$15 | Diaria |
| Dobrar a roupa | Broto (9-11) | R$3 - R$8 | Semanal |
| Limpar o banheiro | Arvore (12-14) | R$10 - R$20 | Semanal |
| Lavar o carro | Arvore (12-14) | R$15 - R$30 | Semanal |
| Organizar a garagem | Floresta (15-17) | R$20 - R$50 | Mensal |
| Fazer compras no mercado | Floresta (15-17) | R$10 - R$25 | Semanal |

**2. Tarefas Educacionais**

Conectam diretamente com o conteudo da Academy. A tarefa pratica o que a licao ensina.

| Tarefa | Faixa recomendada | Vinculada ao modulo | Valor sugerido |
|--------|:-----------------:|---------------------|:--------------:|
| Completar licao GRANIX | Todas | Qualquer modulo ativo | R$2 - R$5 |
| Ler 20 minutos | Semente (6-8) | Qualidade de vida | R$3 - R$5 |
| Praticar matematica (30 min) | Broto (9-11) | Calculo financeiro | R$5 - R$8 |
| Pesquisar 3 precos (produto) | Broto (9-11) | Comparar antes de comprar | R$8 - R$12 |
| Montar orcamento do mes | Arvore (12-14) | Orcamento inteligente | R$10 - R$20 |
| Simular investimento (app) | Floresta (15-17) | Mercado financeiro | R$5 - R$10 |

**3. Desafios GRANIX**

Desafios semanais gerados pela AI, vinculados ao conteudo da semana. Crianca completa, pai valida.

| Desafio | Semana vinculada | Prova exigida | Valor |
|---------|:----------------:|:-------------:|:-----:|
| "Va ao mercado e compare 3 marcas de cereal" | Semana de "preco vs qualidade" | Foto do caderno de anotacoes | R$10 |
| "Economize R$20 sem gastar em impulso por 7 dias" | Semana de "consumo consciente" | Sem compra nao planejada | R$20 |
| "Explique o que e juro composto para um parente" | Semana de "juros compostos" | Relato escrito (2 frases) | R$8 |
| "Monte um plano de 3 meses para um objetivo" | Semana de "metas financeiras" | Screenshot do plano no app | R$15 |

---

##### Fluxo de Aprovacao

```
CRIANCA COMPLETA TAREFA
  │
  │ (opcional) foto como prova enviada ao pai
  │
  ▼
NOTIFICACAO PUSH PARA O PAI
  │ "Joao completou: Arrumar o quarto"
  │ [Ver prova] [Aprovar R$5] [Rejeitar]
  │
  ▼
PAI ABRE O APP DO BANCO (momento critico para a instituicao)
  │
  ├── APROVAR (1 tap)
  │     └── Mesada liberada automaticamente
  │     └── Notificacao para a crianca: "Parabens! R$5 liberados!"
  │     └── XP + streaks atualizados
  │
  └── REJEITAR (com mensagem opcional)
        └── Crianca notificada: "Tente de novo: [mensagem do pai]"
        └── Tarefa retorna para "em andamento"
```

O `<TaskApproval>` e o componente mais estrategico da library: **e ele que gera o DAU do pai no app da instituicao.**

---

##### Liberacao da Mesada

Existem dois modos, configurados pelo pai via `<AllowanceScheduler>`:

| Modo | Como funciona | Melhor para |
|------|--------------|-------------|
| **Automatico** | Mesada liberada no instante da aprovacao | Criancas que precisam de reforco imediato (Semente, Broto) |
| **Agendado** | Mesada acumula e e liberada em dia fixo (ex: domingo) | Ensinar planejamento semanal (Arvore, Floresta) |

**Modo agendado** e o mais pedagogico: a crianca ve o valor acumulando durante a semana e aprende a antecipar e planejar — um conceito financeiro fundamental.

---

##### Distribuicao nos 4 Potes

Assim que a mesada e liberada, a crianca ve a tela de distribuicao via `<BucketDistribution>`:

```
┌──────────────────────────────────────────────────┐
│                                                  │
│   Voce ganhou R$25 essa semana!                  │
│   Como quer dividir?                             │
│                                                  │
│   💡 Sugestao da AI (baseada no seu perfil):     │
│   🛒 Gastar   R$10  ████░░░░  40%               │
│   🐷 Guardar  R$10  ████░░░░  40%               │
│   🎁 Doar     R$2   █░░░░░░░   8%               │
│   📈 Investir R$3   █░░░░░░░  12%               │
│                                                  │
│   [Usar sugestao]   [Editar divisao]             │
│                                                  │
│   Sua meta: Tenis novo (R$180)                   │
│   Guardar agora: R$10 → falta R$95!              │
│                                                  │
└──────────────────────────────────────────────────┘
```

A AI sugere a divisao baseada em:
- Perfil de aprendizado atual (tendencia do onboarding calibrada com historico)
- Metas ativas em cada pote
- Fase do curriculo (quem esta no modulo de "investir" recebe sugestao de % maior no pote Investir)
- Historico de decisoes anteriores (progressao gradual, sem choques)

A crianca pode aceitar a sugestao ou editar livremente. A AI nunca impora — apenas guia. Cada decisao e um dado de aprendizado.

---

##### Tarefas por Faixa Etaria — Referencia Completa

| Faixa | Tarefas ideais | Valor medio/semana | Frequencia sugerida | Prova tipica |
|-------|---------------|:-----------------:|:-------------------:|:------------:|
| Semente (6-8) | Arrumar quarto, ajudar com mesa, regar plantas | R$10 - R$20 | 3-4 tarefas/semana | Foto do resultado |
| Broto (9-11) | Passear com cachorro, dobrar roupa, licao GRANIX, pesquisa de preco | R$20 - R$50 | 4-5 tarefas/semana | Foto + check simples |
| Arvore (12-14) | Lavar carro, limpar banheiro, orcamento mensal, desafio GRANIX | R$40 - R$100 | 4-5 tarefas/semana | Relato escrito + foto |
| Floresta (15-17) | Compras no mercado, organizacao, simulacao de investimento, pesquisa financeira | R$60 - R$200 | 3-5 tarefas/semana | Entrega documentada |

---

#### 3.3 Triplice Valor

O ciclo de tarefas gera valor simultaneo para tres atores. Este e o coração do argumento comercial para a instituicao parceira.

```
┌─────────────────────────────────────────────────────────────────┐
│                       TRIPLICE VALOR                            │
├───────────────────┬───────────────────┬─────────────────────────┤
│   PARA A FAMILIA  │  PARA A INSTITUICAO│   VS CONCORRENCIA       │
├───────────────────┼───────────────────┼─────────────────────────┤
│ Educacao pratica, │ Pai abre o app    │ Nubank / NG.Cash:       │
│ nao teorica.      │ TODOS OS DIAS     │ conta para menor, zero  │
│ Crianca aprende   │ para aprovar      │ educacao. Sem tarefas,  │
│ com dinheiro      │ tarefas = DAU     │ sem loop, sem retencao. │
│ real e tarefas    │ organico e        │                         │
│ reais.            │ gratuito.         │ Greenlight (EUA):       │
│                   │                   │ tarefas e mesada, mas   │
│ Pai tem           │ Familia retida    │ sem AI, sem curriculo   │
│ visibilidade e    │ por anos:         │ pedagogico, sem 4 Potes,│
│ controle total    │ crianca 8 → 18    │ sem espiral de conteudo.|
│ sobre o que filho │ = 10 anos de LTV. │                         │
│ aprende e ganha.  │                   │ GRANIX: unico com o     │
│                   │ Cross-sell        │ ciclo completo:         │
│ Relacao pai-filho │ natural: pai ja   │ tarefas + mesada +      │
│ fortalecida por   │ esta no app,      │ 4 Potes + AI + curriculo│
│ conversa sobre    │ propenso a        │ pedagogico integrado.   │
│ dinheiro com      │ contratar outros  │                         │
│ proposito.        │ produtos.         │ Nenhum competitor tem   │
│                   │                   │ o loop inteiro.         │
│                   │ CAC efetivo:      │                         │
│                   │ R$2,20/ano por    │                         │
│                   │ familia ativa.    │                         │
└───────────────────┴───────────────────┴─────────────────────────┘
```

**Para a familia** — o problema central que GRANIX resolve nao e "meu filho nao sabe matematica financeira." E "meu filho nao entende o valor do dinheiro porque nunca precisou ganhar, nem decidir." O ciclo de tarefas cria essa conexao de forma natural e progressiva.

**Para a instituicao** — o argumento nao e educacional. E de negocio:
- Pai que abre o app diariamente para aprovar tarefas e um pai **muito mais propenso** a ver ofertas, contratar produtos e recomendar a instituicao
- Familia retida por 10 anos e rara em qualquer produto financeiro
- CAC de R$2,20/familia/ano (assumindo custo zero de aquisicao via app existente da instituicao) e **melhor que qualquer campanha de marketing**

**vs Concorrencia** — a diferenca nao e de feature, e de arquitetura de produto:

| Dimensao | Nubank/NG.Cash | Greenlight | GRANIX |
|----------|:--------------:|:----------:|:------:|
| Conta para menor | Sim | Sim | Via parceiro |
| Tarefas/chores | Nao | Sim | **Sim** |
| Mesada automatica | Basico | Sim | **Sim** |
| 4 categorias de poupanca | Nao | Parcial | **Sim (4 Potes)** |
| Curriculo pedagogico | Nao | Nao | **Sim (BNCC-alinhado)** |
| AI personalizacao | Nao | Nao | **Sim** |
| Espiral de conteudo | Nao | Nao | **Sim** |
| Branco para bancos | Nao | Nao | **Sim** |
| Loop fechado completo | Nao | Nao | **Sim** |

---

#### 3.4 Metricas do Ciclo

O Motor de Engajamento Familiar e saudavel quando o ciclo esta girando com frequencia e qualidade. As metricas abaixo sao os **sinais vitais** do produto.

##### Metricas Primarias

| Metrica | Definicao | Meta saudavel | Frequencia de tracking |
|---------|-----------|:-------------:|:---------------------:|
| **Tasks created/week** | Numero de tarefas criadas pelo pai por semana | >= 3 | Semanal |
| **Task completion rate** | % de tarefas criadas que a crianca completa | >= 75% | Semanal |
| **Approval time (pai)** | Tempo medio entre crianca completar e pai aprovar | < 4 horas | Diaria |
| **Distribuicao nos Potes** | % de familias que customizam (nao apenas aceitam sugestao) | >= 40% | Mensal |
| **Task streak** | Semanas consecutivas com pelo menos 1 ciclo completo | >= 4 semanas | Mensal |

##### Metricas de Diagnostico

| Metrica | O que revela | Acao quando abaixo do limite |
|---------|-------------|------------------------------|
| **Pai approval time > 24h** | Pai perdeu habito ou esta desengajado | Push reativacao ao pai: "[Nome] completou 2 tarefas esperando voce!" |
| **Task creation = 0 por 7 dias** | Pai nao esta usando o ciclo | Sugestao de tarefa pronta: "Que tal criar 'Arrumar o quarto' por R$5?" |
| **Crianca rejeita sugestao AI > 3x seguidas** | Sugestao AI desalinhada com perfil real | Recalibrar modelo de sugestao para esse usuario |
| **Distribuicao Gastar > 80%** | Crianca ainda nao internalizou os outros potes | AI sugere desafio especifico do pote Guardar na proxima semana |
| **Zero tarefas educacionais** | Ciclo so com domesticas — perda pedagogica | AI sugere tarefa vinculada a licao ativa da trilha |

##### Correlacoes Criticas (Churn)

```
SINAL DE ALERTA AMARELO:
  Pai nao cria tarefas por 5+ dias
  → Probabilidade de churn em 30 dias: 3x maior que a media

SINAL DE ALERTA LARANJA:
  Aprovacao media > 12 horas por 2 semanas consecutivas
  → Engajamento do pai em declinio
  → Intervencao: email/push para pai + sugestao de tarefas prontas

SINAL CRITICO VERMELHO:
  Zero ciclos completos por 14 dias
  → Churn iminente
  → Acionar fluxo de reativacao personalizado (AI-generated)
```

A **atividade no Motor de Engajamento Familiar e o sinal #1 de saude da familia** — mais preditivo que licoes completadas, badges ou tempo de sessao. Uma familia que cria tarefas, completa e aprova raramente churna.

---

#### 3.5 Integracao com os Outros Modulos

O Motor de Engajamento nao e isolado. E o **eixo central** ao qual todos os outros modulos se conectam:

```
                    ┌─────────────────────────────┐
                    │   MOTOR DE ENGAJAMENTO      │
                    │       FAMILIAR              │
                    │                             │
                    │  Tarefa → Completa →        │
                    │  Aprova → Mesada →          │
                    │  4 Potes → Aprende →        │
                    │  Quer mais                  │
                    └──────────┬──────────────────┘
                               │
           ┌───────────────────┼───────────────────┐
           │                   │                   │
           ▼                   ▼                   ▼
   ┌───────────────┐  ┌────────────────┐  ┌────────────────┐
   │   ACADEMY     │  │  GAMIFICACAO   │  │    4 POTES     │
   │               │  │               │  │                │
   │ Licoes ENSINAM│  │ Streaks de    │  │ Destino da     │
   │ conceitos que │  │ tarefas       │  │ mesada ganha.  │
   │ as tarefas    │  │ completadas.  │  │ Onde decisoes  │
   │ PRATICAM.     │  │               │  │ financeiras    │
   │               │  │ Badges por    │  │ acontecem.     │
   │ Desafios      │  │ ciclos        │  │                │
   │ GRANIX sao    │  │ completos.    │  │ Metas dos      │
   │ tarefas       │  │               │  │ potes motivam  │
   │ educacionais  │  │ XP ganho em   │  │ criacao de     │
   │ do ciclo.     │  │ cada aprovacao│  │ mais tarefas.  │
   └───────────────┘  └────────────┬──┘  └────────────────┘
                                   │
                                   ▼
                         ┌─────────────────┐
                         │       AI        │
                         │                 │
                         │ Personaliza     │
                         │ dificuldade e   │
                         │ tipo de tarefa  │
                         │ por perfil.     │
                         │                 │
                         │ Detecta quando  │
                         │ sugerir novo    │
                         │ tipo de tarefa. │
                         │                 │
                         │ Task activity   │
                         │ = sinal #1 de   │
                         │ churn prediction│
                         └─────────────────┘
```

**Academy → Motor**: Cada modulo do curriculo gera **Desafios GRANIX** — tarefas educacionais que aplicam o conceito recentemente ensinado no mundo real. Sem o Motor, o aprendizado fica apenas na teoria.

**Motor → Academy**: A frequencia de ciclos completos sinaliza que a crianca esta engajada e pronta para progredir no curriculo. Pai que aprova consistentemente recebe sugestoes de licoes mais avancadas.

**Motor → Gamificacao**: O `<StreakCounter>` e `<AchievementBadge>` refletem atividade no ciclo. Streak de tarefas e um dos indicadores de engajamento mais vistos pelo jovem — motiva a pedir ao pai que crie novas tarefas.

**Motor → 4 Potes**: O pote so tem sentido quando tem dinheiro chegando. Cada ciclo completo alimenta os potes — as metas visuais do `<BucketGoal>` so progridem via tarefa completada. Crianca com objetivo claro num pote (ex: tenis novo) **pede ativamente** ao pai que crie mais tarefas.

**AI → Motor**: O AI Engine analisa historico de tarefas e aprende quais tipos geram mais engajamento para cada perfil. Sugere ao pai tarefas que tem maior probabilidade de serem completadas. Detecta quando a crianca esta pronta para tarefas de maior complexidade (ex: de domesticas para educacionais). Antecipa churn monitorando cadencia do ciclo.

**Motor → Churn Prediction**: A cadencia do ciclo — criacao, completude, aprovacao — e a variavel mais correlacionada com retencao a longo prazo. Uma familia com ciclos regulares tem probabilidade de churn dramaticamente menor que uma familia que usa apenas licoes ou apenas 4 Potes sem tarefas.

---

### Pilar 1: Component Library (React / React Native)

Biblioteca de componentes UI white-label que o time de desenvolvimento da instituicao importa e renderiza no app deles.

**Componentes de Tarefas & Recompensas:**
- `<TaskList>` — lista de tarefas com status
- `<TaskCreator>` — criacao de tarefas pelo pai
- `<TaskApproval>` — fluxo de aprovacao
- `<AllowanceScheduler>` — configuracao de mesada
- `<StreakCounter>` — contador de sequencias
- `<FamilyDashboard>` — visao consolidada do pai

**Componentes de Academy:**
- `<LessonCard>` — card de licao com progresso
- `<LessonPlayer>` — player de conteudo adaptativo
- `<QuizEngine>` — motor de quizzes interativos
- `<SimulatorWidget>` — simuladores financeiros (juros compostos, orcamento)
- `<LearningPath>` — trilha de aprendizado visual
- `<AgeGateSelector>` — seletor de faixa etaria

**Componentes de Gamificacao:**
- `<AvatarBuilder>` — avatar customizavel
- `<AchievementBadge>` — badges de conquista
- `<XPProgressBar>` — barra de progresso de experiencia
- `<LeaderboardFamily>` — ranking entre irmaos
- `<ChallengeCard>` — desafios semanais
- `<StreakFlame>` — indicador visual de streak

**Componentes dos 4 Potes:**
- `<FourBuckets>` — visualizacao dos 4 potes (Gastar/Guardar/Doar/Investir)
- `<BucketGoal>` — meta por pote com progresso visual
- `<BucketDistribution>` — divisao percentual visual
- `<BucketHistory>` — historico visual por pote

**Todos os componentes**:
- Recebem dados via props (a instituicao alimenta)
- Emitem callbacks/eventos (a instituicao processa)
- Sao themeable (cores, fontes, icones da marca do parceiro)
- Zero acesso a APIs financeiras
- React + React Native (mono-repo compartilhado)

---

### Pilar 2: AI Content Engine — O Diferencial Central

GRANIX nao e uma library estatica de componentes. E uma **engine inteligente que aprende, cria e evolui** com cada usuario. A AI e o conteudo sao inseparaveis — a AI gera, personaliza, otimiza e mede o conteudo. O conteudo alimenta a AI com dados de eficacia. Este ciclo virtuoso e o moat.

---

#### 2.1 CONTEUDO: Curriculo Financeiro Completo por Faixa Etaria

##### Estrutura Pedagogica

O curriculo e organizado em 4 trilhas por faixa etaria, cada uma com modulos tematicos progressivos. Todo conteudo e alinhado a **BNCC** (Base Nacional Comum Curricular) e validado por pedagogos.

**Trilha Semente (6-8 anos) — "Descobrindo o Dinheiro"**

| Modulo | Tema | Formato Principal | Licoes |
|--------|------|-------------------|:------:|
| O que e dinheiro? | Historia do dinheiro, troca, moeda | Historia animada + quiz | 6 |
| Querer vs Precisar | Necessidades vs desejos, prioridades | Jogo de classificacao | 5 |
| Primeiro Cofrinho | Guardar, esperar, objetivo simples | Simulador visual de cofrinho | 5 |
| Gentileza Financeira | Doar, compartilhar, impacto social | Historia + desafio real | 4 |
| Minha Primeira Mesada | Receber, planejar, gastar com consciencia | Simulador de mesada | 5 |
| **Total** | | | **25** |

**Trilha Broto (9-11 anos) — "Construindo Objetivos"**

| Modulo | Tema | Formato Principal | Licoes |
|--------|------|-------------------|:------:|
| Orcamento Inteligente | Receita, despesa, saldo, planejamento mensal | Planilha interativa gamificada | 6 |
| O Poder da Espera | Juros simples, tempo, gratificacao adiada | Simulador de crescimento | 5 |
| Comparando Precos | Custo-beneficio, pesquisa, consumo consciente | Jogo de comparacao | 5 |
| Metas de Verdade | SMART goals, plano de economia, tracking | Builder de metas + tracker | 6 |
| Empreendedor Mirim | Produto, preco, lucro, lemonade stand | Simulador de negocio | 6 |
| Dinheiro Digital | PIX, cartao, pagamentos online, seguranca | Quiz + cenarios | 5 |
| **Total** | | | **33** |

**Trilha Arvore (12-14 anos) — "Investindo no Futuro"**

| Modulo | Tema | Formato Principal | Licoes |
|--------|------|-------------------|:------:|
| Juros Compostos | A 8a maravilha, calculos, visualizacao | Calculadora interativa | 7 |
| Mundo dos Investimentos | Renda fixa, renda variavel, risco | Simulador de carteira | 8 |
| Tesouro Direto | Titulos publicos, Tesouro Educa+, Selic | Simulador de compra | 6 |
| Orcamento Avancado | 50-30-20, custos fixos vs variaveis | Planilha AI-assistida | 6 |
| Inflacao e Poder de Compra | Perda de valor, indices, protecao | Timeline interativa | 5 |
| Credito e Divida | Cartao de credito, financiamento, juros abusivos | Simulador de divida | 6 |
| Economia Comportamental | Vieses cognitivos, decisoes, nudges | Cenarios interativos | 5 |
| **Total** | | | **43** |

**Trilha Floresta (15-17 anos) — "Dominando o Mercado"**

| Modulo | Tema | Formato Principal | Licoes |
|--------|------|-------------------|:------:|
| Bolsa de Valores | Acoes, ETFs, analise fundamentalista basica | Simulador de bolsa | 8 |
| Previdencia e Longo Prazo | PGBL, VGBL, aposentadoria, Tesouro Renda+ | Calculadora de aposentadoria | 6 |
| Empreendedorismo | Business model, MVP, receita, escala | Canvas interativo | 7 |
| Impostos e Cidadania | IR, IOF, tributos, declaracao | Simulador de IR simplificado | 5 |
| Economia Global | Cambio, importacao, criptomoedas, mercados | Dashboard de mercados | 6 |
| Planejamento de Vida | Faculdade, primeiro emprego, moradia, carro | Simulador de cenarios de vida | 7 |
| Psicologia do Dinheiro | Relacao emocional, armadilhas, mindset | Autodiagnostico + reflexoes | 5 |
| **Total** | | | **44** |

**Total do curriculo base: 145 licoes** cobrindo toda a jornada de 6 a 17 anos.

##### Formatos de Conteudo

Cada licao pode ser entregue em multiplos formatos, e a AI escolhe o melhor para cada perfil:

| Formato | Descricao | Faixa ideal | Retencao media* |
|---------|-----------|:-----------:|:---------------:|
| **Historia Animada** | Narrativa visual com personagens, dialogo, cenarios | 6-10 | Alta |
| **Quiz Interativo** | Perguntas com feedback instantaneo, explicacao do erro | Todas | Media-Alta |
| **Simulador** | Ferramenta interativa (calculadora, mercado, orcamento) | 10-17 | Muito Alta |
| **Desafio Pratico** | Missao do mundo real (economizar X, pesquisar precos) | 8-17 | Muito Alta |
| **Video Curto** | 60-90 segundos, estilo TikTok educativo | Todas | Media |
| **Cenario Interativo** | "Escolha sua aventura" financeira com consequencias | 10-17 | Alta |
| **Infografico** | Visualizacao de dados/conceitos (juros, inflacao) | 12-17 | Media |
| **Flashcard** | Revisao rapida de conceitos, spaced repetition | Todas | Media |

*Retencao medida por taxa de conclusao + score em quiz posterior. AI ajusta continuamente.

##### Conteudo Contextual e Temporal

A AI gera conteudo conectado a eventos reais para maximizar relevancia:

**Contextualizacao automatica:**
- **Esportes**: Copa do Mundo → economia do futebol, salarios de jogadores, gestao de clubes
- **Games**: Lancamento de jogo popular → economia digital, microtransacoes, custo real de skins
- **Escola**: Volta as aulas → orcamento de material, comparacao de precos
- **Datas comerciais**: Black Friday → consumo consciente, marketing vs necessidade real
- **Economia real**: Alta da Selic → o que muda no seu Tesouro Direto?
- **Familia**: Ferias → planejamento de viagem, orcamento familiar
- **Tendencias**: Influenciadores financeiros → separar informacao de opiniao

**Sazonalidade do curriculo:**
```
Jan: Planejamento anual / mesada do ano
Mar: Volta as aulas / orcamento escolar
Mai: Dia das maes / presente com consciencia
Jun: Ferias / economizar para viagem
Ago: Dia dos pais / investindo junto
Out: Dia das criancas / querer vs precisar
Nov: Black Friday / consumo consciente
Dez: Natal / generosidade + planejamento
```

##### Conteudo para Pais (Dashboard Familiar)

Nao so o jovem aprende — os pais tambem:

- **Dicas semanais**: "Como conversar sobre dinheiro com seu filho de 10 anos"
- **Relatorio de progresso**: O que o filho aprendeu, onde tem dificuldade
- **Sugestoes de interacao**: "Joao completou a licao sobre juros compostos — que tal mostrar quanto rendeu o CDB dele este mes?"
- **Alertas de engajamento**: "Maria nao acessa ha 5 dias — enviar um desafio especial?"
- **Benchmarking anonimo**: "Seu filho esta no top 20% de progresso para a faixa etaria"

---

#### 2.2 AI: PERSONALIZACAO DE EXPERIENCIA

A AI transforma 145 licoes estaticas em **milhoes de jornadas unicas**.

##### Perfil de Aprendizado (Learning Profile)

Para cada usuario, a AI constroi e atualiza continuamente um perfil:

```
LearningProfile {
  // Basico
  faixa_etaria: "Arvore"        // 12-14
  meses_na_plataforma: 7
  licoes_completadas: 38

  // Estilo de aprendizado (AI-detected)
  formato_preferido: "simulador"  // vs quiz, video, historia
  duracao_ideal_sessao: "8min"    // cai engajamento apos 8min
  horario_pico: "19h-20h"        // quando mais engaja
  dia_preferido: "domingo"       // maior taxa de conclusao

  // Cognitivo
  velocidade_aprendizado: 1.2x   // acima da media da faixa
  areas_fortes: ["juros_compostos", "orcamento"]
  areas_fracas: ["risco_investimento", "inflacao"]
  estilo_erro: "impulsivo"       // responde rapido sem ler → AI adiciona "respire e pense"

  // Engajamento
  streak_atual: 12               // dias consecutivos
  streak_recorde: 23
  badges_coletados: 15
  desafios_completados: 8
  desafios_abandonados: 2        // AI analisa por que abandonou

  // Interesses detectados
  contextos_engajam: ["futebol", "games", "youtube"]
  contextos_nao_engajam: ["politica", "historia_antiga"]

  // Familiar
  engajamento_pai: "alto"        // pai aprova tarefas em <2h
  interacao_familiar: "frequente" // pai e filho usam juntos 2x/semana
}
```

##### Motor de Recomendacao

Baseado no Learning Profile, a AI decide:

**1. Proxima licao (Next Best Lesson)**
```
Input: LearningProfile + historico de licoes + hora do dia + dia da semana
Output: {
  licao: "Simulador de Carteira de Investimentos",
  formato: "simulador",           // formato preferido do usuario
  dificuldade: 0.7,               // 70% do maximo (zona de flow)
  duracao_estimada: "7min",       // abaixo do limiar de 8min
  contexto: "futebol",           // "Monte a carteira do Neymar"
  razao: "area_fraca=risco_investimento + contexto=futebol + formato=simulador"
}
```

**2. Dificuldade adaptativa (Zone of Proximal Development)**

A AI calibra a dificuldade para manter o jovem na "zona de flow" — nem tao facil (tedioso) nem tao dificil (frustrante):

```
Score no quiz anterior:
  < 40%  → AI reduz dificuldade, oferece revisao do conceito anterior
  40-60% → AI mantem nivel, muda formato (se era texto, muda para simulador)
  60-80% → Nivel ideal — "zona de flow" — AI mantem
  80-95% → AI aumenta dificuldade, adiciona conceito novo
  > 95%  → AI pula para conceito avancado, sugere desafio pratico
```

**3. Sequencia otima (Learning Path Optimization)**

A AI nao segue a ordem fixa do curriculo. Ela otimiza a sequencia baseado em:
- **Prerequisitos conceituais**: Nao ensina juros compostos antes de juros simples
- **Engajamento recente**: Se o jovem esta muito engajado em orcamento, aprofunda antes de mudar de tema
- **Spaced repetition**: Retorna conceitos antigos em intervalos otimos para fixacao
- **Variedade**: Alterna entre formatos para evitar fadiga
- **Momentum**: Se completou 3 licoes seguidas, oferece um desafio pratico como recompensa

##### Micro-Segmentacao AI-Driven

Dentro de cada faixa etaria, a AI identifica clusters de comportamento:

| Micro-Segmento | Perfil | Estrategia AI |
|----------------|--------|---------------|
| **Explorador** | Alta curiosidade, pula entre temas | Oferecer variedade, conexoes entre temas |
| **Focado** | Aprofunda um tema ate dominar | Trilha linear profunda, desafios avancados |
| **Social** | Engaja mais com rankings e desafios | Enfatizar gamificacao e competicao familiar |
| **Pratico** | Prefere simuladores e desafios reais | Mais hands-on, menos teoria |
| **Cauteloso** | Progride devagar, evita erros | Feedback positivo extra, dificuldade gradual |
| **Intermitente** | Usa em rajadas, some, volta | Sessoes curtas, resumos de "onde parou" |

---

#### 2.3 AI: PREDICAO DE COMPORTAMENTO

A AI modela o comportamento para antecipar acoes e otimizar a experiencia.

##### Modelo de Predicao de Engajamento

```
Engajamento = f(perfil, contexto, historico, sinais_externos)

Inputs:
- Padroes temporais (horario, dia, frequencia)
- Formato de conteudo (qual engaja mais)
- Dificuldade relativa (challenge vs frustration)
- Contexto externo (ferias, provas, feriados)
- Engajamento familiar (pai ativo = jovem mais engajado)
- Streak status (manter streak motiva)

Outputs:
- P(login amanha) = 0.73
- P(completar licao se iniciada) = 0.85
- Formato otimo para proxima sessao = "simulador"
- Horario otimo para notificacao = 19:15
- Desafio otimo = "Calcule quanto seu Tesouro rende em 5 anos"
```

##### Predicao de Marcos de Aprendizado

A AI prediz quando o jovem esta pronto para avancar:

| Marco | Sinais | Acao AI |
|-------|--------|---------|
| Pronto para proxima faixa | Score >80% nos ultimos 5 quizzes + >70% licoes completadas | Oferecer "preview" da proxima faixa como desafio |
| Pronto para investimento real | Completou modulo de juros + simulador usado 3+ vezes | Sugerir ao pai: "Joao esta pronto para o primeiro investimento real" |
| Pronto para orcamento autonomo | Completou modulo de orcamento + usa 4 potes ha >30 dias | Desbloquear ferramentas avancadas de planejamento |
| Risco de estagnacao | Mesmo nivel ha >45 dias + score estavel | Alterar formato de conteudo + adicionar competicao |

##### Predicao de Comportamento Familiar

A dinamica familiar e crucial para retencao:

**Padroes monitorados:**
- Tempo medio de aprovacao de tarefa (pai rapido = jovem mais motivado)
- Frequencia de criacao de tarefas pelo pai
- Interacoes familiares no app (mensagens, emojis, celebracoes)
- Correlacao entre uso do pai e uso do filho

**Insights para o pai:**
- "Quando voce aprova tarefas em menos de 1 hora, Joao completa 40% mais licoes"
- "Domingos a noite e quando voces mais interagem — ideal para criar tarefas da semana"
- "Maria responde melhor a desafios criados por voce do que aos automaticos"

---

#### 2.4 AI: PREDICAO DE CHURN

Motor de predicao que identifica sinais de abandono **antes** que aconteca. A AI nao espera o usuario sumir — age nos primeiros sinais.

##### Modelo de Churn em 3 Camadas

**Camada 1 — Sinais Fracos (Alerta Amarelo, 7-14 dias antes)**
- Reducao de 30%+ na frequencia de sessoes
- Sessoes mais curtas que a media do usuario
- Quiz ignorados (abre licao mas pula quiz)
- Notificacoes nao abertas (de 80% para <50%)
- Streaks quebrados sem retomada em 48h

**Camada 2 — Sinais Medios (Alerta Laranja, 3-7 dias antes)**
- Zero sessoes por 3+ dias (para usuario diario)
- Desafio semanal nao iniciado
- Pai parou de criar/aprovar tarefas
- App aberto mas fechado em <30 segundos
- Downgrade de plano solicitado

**Camada 3 — Sinais Fortes (Alerta Vermelho, 0-3 dias)**
- Zero sessoes por 7+ dias
- Nenhuma interacao familiar por 5+ dias
- Notificacoes desativadas
- App desinstalado (se detectavel)

##### Acoes Automaticas Anti-Churn por Camada

**Camada 1 — Reenergizar:**
- AI ajusta dificuldade (se detectar frustracao) ou formato (se detectar tedio)
- Gera desafio ultra-personalizado baseado em interesse detectado
- "Missao relampago" com recompensa de badge exclusivo
- Notificacao contextual: "Voce sabia que o Vinicius Jr ganha X por ano? Descubra como investidores pensam"

**Camada 2 — Resgatar:**
- Envia "Resumo do que voce perdeu" com conquistas proximas de serem desbloqueadas
- Ativa desafio familiar: notifica o pai para criar tarefa especial
- Oferece "power session": 3 minutos para recuperar streak + badge especial
- AI gera conteudo no tema de maior engajamento historico do usuario

**Camada 3 — Reconquistar:**
- Email/push com progresso acumulado: "Voce ja completou 38 licoes e ganhou 15 badges"
- Oferta de periodo premium gratis (se usuario free)
- Desafio de "volta triunfal" com recompensas multiplicadas
- Notificacao ao pai com sugestao pratica de reengajamento

##### Metricas de Churn para a Instituicao (Dashboard B2B)

| Metrica | Descricao | Frequencia |
|---------|-----------|:----------:|
| Churn rate por plano | % de cancelamentos Free/Premium/Premium+ | Mensal |
| Churn rate por cohort | % por mes de entrada + faixa etaria | Mensal |
| Predicao de churn 30d | % estimado de churn nos proximos 30 dias | Semanal |
| Eficacia anti-churn | % de usuarios resgatados por camada | Semanal |
| NPS por faixa etaria | Satisfacao segmentada | Trimestral |
| Health score por familia | Indice composto de engajamento familiar | Diario |
| Benchmarking cross-instituicao | Comparacao anonimizada vs outras instituicoes GRANIX | Mensal |

---

#### 2.5 AI: CRIACAO AUTOMATIZADA DE CONTEUDO

A AI nao so personaliza conteudo existente — ela **cria conteudo novo** continuamente, reduzindo custo de producao e aumentando relevancia.

##### Pipeline de Criacao

```
┌──────────────────────────────────────────────────────────────────────┐
│                    PIPELINE DE CONTEUDO GRANIX                       │
│                                                                      │
│  ┌─────────┐    ┌──────────┐    ┌──────────┐    ┌───────────────┐   │
│  │ DETECT  │───>│ GENERATE │───>│ REVIEW   │───>│ A/B TEST      │   │
│  │         │    │          │    │          │    │               │   │
│  │ AI      │    │ AI       │    │ Humano + │    │ AI otimiza    │   │
│  │ detecta │    │ gera     │    │ AI       │    │ formato,      │   │
│  │ gaps no │    │ rascunho │    │ valida   │    │ dificuldade,  │   │
│  │ curriculo│   │ completo │    │ acuracia │    │ sequencia     │   │
│  └─────────┘    └──────────┘    └──────────┘    └───────┬───────┘   │
│                                                         │           │
│  ┌─────────────────────────────────────────────────────┐│           │
│  │ OPTIMIZE                                            ││           │
│  │                                                     ▼│           │
│  │  AI monitora metricas de aprendizado ──────────────>Loop         │
│  │  - Taxa de conclusao                                             │
│  │  - Score medio no quiz                                           │
│  │  - Retencao pos-licao (volta no dia seguinte?)                   │
│  │  - Feedback implicito (tempo gasto, skips, replays)              │
│  └──────────────────────────────────────────────────────────────────┘│
└──────────────────────────────────────────────────────────────────────┘
```

##### Tipos de Conteudo Gerado por AI

**1. Licoes Novas (Gap Detection)**

A AI analisa o curriculo e identifica gaps:
- Conceito X tem baixo score medio → gerar licao alternativa com abordagem diferente
- Nenhuma licao conecta tema A com tema B → gerar licao-ponte
- Novo regulamento financeiro (ex: PIX por aproximacao) → gerar licao atualizada
- Evento sazonal proximo → gerar licao contextual

**2. Quizzes Adaptativos (Dificuldade Calibrada)**

A AI gera quizzes com dificuldade calibrada por usuario:
```
Exemplo — Faixa Arvore, tema "Juros Compostos":

Nivel 1 (basico):
"Se voce investir R$100 a 10% ao ano, quanto tera em 1 ano?"
a) R$110  b) R$100  c) R$120  d) R$90

Nivel 3 (intermediario):
"Joao investiu R$500 no Tesouro Selic que rende 12% ao ano.
Maria investiu R$500 na poupanca que rende 6% ao ano.
Apos 3 anos, qual a diferenca entre os dois?"
[Campo de calculo interativo]

Nivel 5 (avancado):
"Seu pai te deu 2 opcoes: R$1.000 hoje ou R$100/mes por 12 meses.
Considerando que voce pode investir a 1% ao mes, qual vale mais?
Mostre seu raciocinio."
[Campo de resposta aberta, AI avalia raciocinio]
```

**3. Desafios Personalizados (Context-Aware)**

A AI gera desafios conectados ao mundo real do jovem:
```
Para usuario com contexto "futebol":
  "Neymar ganha R$160M por ano no Al-Hilal.
   Se ele investisse 10% no Tesouro IPCA+, quanto teria em 20 anos?
   Agora calcule: se VOCE investir R$50/mes no mesmo titulo, quanto tera em 20 anos?
   Compare os resultados. O que voce aprende sobre juros compostos?"

Para usuario com contexto "games":
  "Uma skin legendaria no Fortnite custa R$80.
   Se voce investisse R$80/mes por 1 ano a 12% ao ano, quanto teria?
   Quantas skins isso compraria? Vale mais ter a skin hoje ou o dinheiro investido?"

Para usuario com contexto "musica":
  "Taylor Swift faturou US$2 bilhoes na Era Tour.
   Se ela investisse 50% em renda fixa brasileira a 13% ao ano,
   quanto renderia POR DIA? Compare com o seu rendimento mensal."
```

**4. Explicacoes Alternativas (Quando o Aluno Nao Entende)**

Se o score no quiz e baixo, AI gera uma explicacao diferente:
- Primeira explicacao foi textual → AI gera versao visual (infografico)
- Primeira foi abstrata → AI gera com exemplo concreto do interesse do usuario
- Primeira foi longa → AI gera versao de 60 segundos (video curto estilo)
- Primeira foi individual → AI gera versao com desafio familiar (pai e filho resolvem juntos)

**5. Resumos e Revisoes (Spaced Repetition)**

AI gera flashcards e resumos nos intervalos otimos de revisao:
```
Dia 1: Aprende "Juros Compostos"
Dia 3: Flashcard de revisao (3 perguntas rapidas)
Dia 7: Quiz curto (5 perguntas, nivel 2)
Dia 14: Desafio pratico ("Calcule o rendimento real do seu cofrinho")
Dia 30: Integracao com conceito novo ("Juros compostos + inflacao = rendimento real")
```

##### Human-in-the-Loop: Controle de Qualidade

A AI gera, mas humanos garantem qualidade:

| Tipo de Conteudo | Nivel de Review | Quem Aprova |
|------------------|:---------------:|-------------|
| Quiz com resposta objetiva | Automatico | AI (se score de confianca >95%) |
| Quiz com resposta aberta | Sampling | Pedagogo revisa 10% aleatorio |
| Licao nova (gap detection) | Completo | Pedagogo revisa 100% antes de publicar |
| Desafio personalizado | Regras | AI gera dentro de templates validados |
| Explicacao alternativa | Automatico | AI (variacao de conteudo ja validado) |
| Conteudo contextual (eventos) | Completo | Pedagogo + editor revisa antes de publicar |

##### Localizacao e Adaptacao Cultural

**Portugues (Brasil)** — lingua base:
- Exemplos com Real (R$), Tesouro Direto, PIX, Nubank
- Referências culturais brasileiras (futebol, Carnaval, Black Friday Brasil)
- Alinhamento com BNCC

**Espanhol (LATAM)** — expansao Fase 3:
- AI traduz + adapta contexto cultural
- Mexico: pesos, CETES, Mercado Libre
- Colombia: pesos, CDTs, Rappi
- Argentina: pesos, inflacao como tema central, dolares

**Adaptacao por instituicao:**
- Componentes de conteudo que mencionam produtos financeiros sao parametrizaveis
- XP: exemplos com Tesouro Educa+, fundos XP, acoes na B3
- Nubank: exemplos com Caixinhas, RDB, compras com cartao
- Inter: exemplos com CDB Inter, Shopping Inter, cashback

---

#### 2.6 AI: ANALYTICS E INSIGHTS PARA INSTITUICOES (Dashboard B2B)

GRANIX entrega para cada instituicao parceira um dashboard de inteligencia sobre a base de usuarios jovens.

##### Metricas de Aprendizado

| Metrica | O que mostra | Valor para a instituicao |
|---------|-------------|--------------------------|
| Learning Velocity | Velocidade media de progressao por faixa | Eficacia do produto na educacao |
| Knowledge Score | Score medio por tema (juros, orcamento, investimento) | Onde os jovens tem mais dificuldade |
| Completion Funnel | % que completa cada modulo | Onde ha dropout de conteudo |
| Format Effectiveness | Qual formato gera mais aprendizado | Otimizacao de investimento em conteudo |
| Age Readiness | % prontos para conceitos avancados por faixa | Quando introduzir produtos financeiros |

##### Metricas de Engajamento

| Metrica | O que mostra | Valor para a instituicao |
|---------|-------------|--------------------------|
| DAU/MAU ratio | Stickiness do produto | Saude do engajamento |
| Session depth | Licoes/sessao media | Profundidade de uso |
| Family co-engagement | % de familias com pai + filho ativos | Predicao de retencao de conta |
| Feature adoption | Uso por modulo (tarefas, academy, gamificacao) | Onde investir em marketing |
| Streak distribution | % com streaks ativos por faixa | Habito formado vs uso esporadico |

##### Insights Preditivos

| Insight | O que prediz | Acao sugerida |
|---------|-------------|---------------|
| Churn Risk Score | Probabilidade de cancelamento em 30 dias | Intervencao personalizada |
| Upsell Readiness | Familia pronta para upgrade Free→Premium | Oferta direcionada |
| Investment Readiness | Jovem pronto para primeiro investimento real | Sugestao ao assessor/pai |
| Graduation Pipeline | Jovens proximos de 18 anos, engajados | Preparar transicao para conta adulta |
| Family Lifetime Value | Valor projetado da familia ao longo de 10 anos | Priorizacao de retencao |

##### Benchmarking Cross-Instituicao (Anonimizado)

Cada instituicao ve como sua base se compara com a media de todas as instituicoes GRANIX:

```
Sua instituicao vs Media GRANIX:
  Engajamento:      ████████░░ 82%  (media: 71%)  ↑ acima
  Aprendizado:      ███████░░░ 74%  (media: 68%)  ↑ acima
  Retencao 90d:     █████░░░░░ 54%  (media: 61%)  ↓ abaixo ⚠️
  Conversao Free→Pago: ██████░░░░ 62%  (media: 45%)  ↑ acima
  Churn mensal:     ███░░░░░░░ 3.2% (media: 4.1%) ↑ melhor
```

Este benchmarking cria **pressao competitiva saudavel** entre instituicoes e valida o investimento em GRANIX.

---

### Pilar 2B: Metodologia Pedagogica — O Diferencial das Trilhas

As 4 trilhas nao sao apenas "conteudo mais dificil conforme a idade". Cada faixa tem uma **abordagem pedagogica fundamentalmente diferente** — a forma de ensinar muda, nao so o que se ensina.

#### Progressao Cognitiva por Faixa

| Faixa | Estagio Cognitivo | Abordagem Pedagogica | Formato Dominante | Relacao com Dinheiro |
|-------|-------------------|----------------------|-------------------|---------------------|
| **Semente** (6-8) | Concreto-operacional | Aprender **brincando** — conceitos atraves de historias e jogos. Zero abstracao. | Historias animadas, jogos de classificacao | Dinheiro = troca de coisas |
| **Broto** (9-11) | Operacional | Aprender **fazendo** — simuladores simples, causa e efeito visivel. Inicio de logica. | Simuladores visuais, desafios praticos | Dinheiro = ferramenta para objetivos |
| **Arvore** (12-14) | Abstrato inicial | Aprender **calculando** — numeros reais, projecoes, comparacoes. Pensamento hipotetico. | Calculadoras, cenarios "e se?", graficos | Dinheiro = sistema com regras |
| **Floresta** (15-17) | Abstrato avancado | Aprender **analisando** — tomada de decisao complexa, trade-offs, visao sistemica. | Analise de casos reais, debates, planejamento | Dinheiro = instrumento de autonomia |

#### Como Conceitos Evoluem Entre Trilhas

O mesmo conceito e revisitado em profundidade crescente. Exemplo com **"Guardar Dinheiro"**:

| Faixa | Como o conceito e apresentado | Formato |
|-------|-------------------------------|---------|
| **Semente** | "O cofrinho magico: quando voce guarda uma moeda, ela fica la esperando ate voce precisar!" | Historia do cofrinho que "guarda" coisas para o personagem |
| **Broto** | "Se voce guardar R$5 por semana, em 10 semanas tem R$50! O que voce compraria?" | Simulador visual de cofrinho enchendo semana a semana |
| **Arvore** | "R$50 na poupanca rende 0,5%/mes. No Tesouro Selic, rende 1%/mes. Em 12 meses, a diferenca e..." | Calculadora comparativa com graficos de crescimento |
| **Floresta** | "Analise: onde voce colocaria R$5.000 hoje considerando inflacao de 5%, Selic a 13%, e seu objetivo de comprar um notebook em 18 meses?" | Caso real com multiplas variaveis e trade-offs |

#### O que Torna GRANIX Diferente de Duolingo/Khan Academy

| Aspecto | Duolingo | Khan Academy | GRANIX |
|---------|----------|-------------|--------|
| Dominio | Idiomas | Academico geral | **Educacao financeira exclusiva** |
| Faixa etaria | Adultos (primariamente) | Todas | **6-17 anos (especializado)** |
| Contextualizacao | Generica | Generica | **Personalizada por interesse (games, futebol, musica)** |
| Aplicacao real | Nenhuma (pratica in-app) | Nenhuma | **Conectado a dinheiro real via 4 Potes** |
| Familia | Individual | Individual | **Pai + filho como unidade** |
| Gamificacao | Forte (streaks, XP) | Basica | **Forte + conectada a resultados reais** |
| AI | Recomendacao de exercicios | Recomendacao de videos | **Personalizacao + predicao + geracao de conteudo** |
| Modelo | B2C | B2C/B2G | **B2B2C (via instituicoes financeiras)** |

**Diferencial raiz**: Duolingo ensina um idioma que voce pratica fora do app. Khan Academy ensina matematica que voce pratica na escola. **GRANIX ensina financas que voce pratica COM SEU DINHEIRO REAL, na sua conta real, com sua familia.** A distancia entre aprender e aplicar e zero.

#### Conexoes Inter-Trilhas (Espiral Curricular)

O curriculo nao e linear — e uma **espiral** onde conceitos fundamentais sao revisitados com profundidade crescente:

```
ESPIRAL CURRICULAR GRANIX

Conceito: "Investir"

Semente (6-8):
  └── "Plantar uma semente e esperar ela crescer"
       (metafora: dinheiro plantado = dinheiro que cresce)

Broto (9-11):
  └── "Seu dinheiro pode trabalhar pra voce"
       (cofrinho vs poupanca: um cresce, outro nao)
       └── Retoma metafora da semente com numeros reais

Arvore (12-14):
  └── "Renda fixa vs renda variavel"
       (Tesouro Direto, CDB, acoes — risco vs retorno)
       └── Retoma poupanca do Broto: "lembra quando R$50 virou R$53?"
       └── Agora: "e se fossem R$56 no CDB? Por que?"

Floresta (15-17):
  └── "Construindo uma carteira de investimentos"
       (diversificacao, correlacao, horizonte temporal)
       └── Retoma tudo: da semente ao portfolio
       └── "Voce plantou sua primeira semente aos 7 anos.
            Agora com 16, vamos ver quanto ela cresceu
            e montar sua estrategia para os proximos 10 anos."
```

A AI rastreia quais conceitos cada jovem ja viu e referencia experiencias anteriores na trilha: *"Lembra quando voce aprendeu sobre juros compostos no modulo Arvore? Agora vamos usar isso pra montar sua primeira carteira."*

---

### Pilar 2C: Producao de Conteudo com AI + Agentes — Operacao Lean

Este e o pilar que torna o modelo economicamente viavel. GRANIX produz conteudo na velocidade de uma empresa de 50 pessoas com um time de 3-5.

#### Time Humano Minimo

| Pessoa | Funcao | Dedicacao | O que FAZ | O que NAO faz |
|--------|--------|:---------:|-----------|---------------|
| **Pedagogo Senior** | Diretor de curriculo | Full-time | Define estrutura curricular, valida acuracia, aprova conteudo critico | Nao escreve licoes do zero |
| **Pedagogo Jr** | Review de conteudo | Full-time | Revisa conteudo gerado por AI, ajusta linguagem por faixa, testa quizzes | Nao cria quizzes manualmente |
| **Editor de Conteudo** | Curadoria + contexto | Full-time | Alimenta AI com contexto (eventos, tendencias), curadoria de conteudo contextual | Nao pesquisa dados — AI faz |
| **Designer** (part-time) | Assets visuais | Part-time | Cria templates visuais, animacoes base, icones | Nao cria cada ilustracao — AI adapta templates |
| **Dev AI/ML** | Manutencao dos agentes | Full-time | Treina modelos, ajusta pipelines, monitora qualidade | Nao cria conteudo |

**Total: 4 full-time + 1 part-time = ~R$80K/mes**

Modelo tradicional equivalente (produzir 50+ licoes/mes + quizzes + desafios + localizacao): **15-20 pessoas = ~R$300K/mes**

**Reducao: 73% no custo de operacao de conteudo.**

#### Sistema de Agentes AI

A producao de conteudo e orquestrada por 6 agentes especializados que trabalham em pipeline:

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    PIPELINE DE AGENTES GRANIX                          │
│                                                                        │
│  ┌──────────┐    ┌──────────────┐    ┌─────────────┐                   │
│  │ AGENTE 1 │───>│  AGENTE 2    │───>│  AGENTE 3   │                   │
│  │ Detector │    │  Gerador     │    │  Pedagogo   │                   │
│  │ de Gaps  │    │  de Conteudo │    │  Digital    │                   │
│  └──────────┘    └──────────────┘    └──────┬──────┘                   │
│                                             │                          │
│                                    ┌────────▼────────┐                 │
│                                    │  HUMANO REVISA  │                 │
│                                    │  (Pedagogo)     │                 │
│                                    └────────┬────────┘                 │
│                                             │                          │
│  ┌──────────┐    ┌──────────────┐    ┌──────▼──────┐                   │
│  │ AGENTE 6 │<───│  AGENTE 5    │<───│  AGENTE 4   │                   │
│  │ Otimiza- │    │  A/B Tester  │    │  Contextu-  │                   │
│  │ dor      │    │              │    │  alizador   │                   │
│  └──────────┘    └──────────────┘    └─────────────┘                   │
│                                                                        │
└─────────────────────────────────────────────────────────────────────────┘
```

##### Agente 1: Detector de Gaps

**Funcao**: Analisa continuamente o curriculo e identifica o que falta.

**Inputs:**
- Metricas de aprendizado (quais licoes tem baixo score)
- Cobertura curricular (quais conceitos da BNCC nao estao cobertos)
- Eventos externos (calendario sazonal, noticias relevantes)
- Feedback implicito (licoes com alta taxa de abandono)

**Outputs:**
- Lista priorizada de gaps: "Falta licao sobre PIX por aproximacao na faixa Arvore"
- Brief de conteudo: tema, faixa, formato sugerido, conceitos prerequisitos

**Frequencia**: Roda diariamente, gera relatorio semanal para o time.

```
Exemplo de output:
{
  "gap": "PIX por aproximacao",
  "prioridade": "alta",
  "razao": "Feature lancada pelo BCB em Nov/2025, nenhuma licao cobre",
  "faixa_alvo": ["Arvore", "Floresta"],
  "formato_sugerido": "cenario_interativo",
  "prerequisitos": ["licao_pix_basico", "licao_seguranca_digital"],
  "contexto_sugerido": "Seu amigo te pede pra encostar o celular pra pagar o lanche. E seguro?"
}
```

##### Agente 2: Gerador de Conteudo

**Funcao**: Cria rascunhos completos de licoes, quizzes, desafios e explicacoes alternativas.

**Inputs:**
- Brief do Agente 1 (ou do time humano)
- Estilo e tom por faixa etaria (Semente = simples e ludico, Floresta = analitico)
- Templates validados de licoes anteriores com bom desempenho
- Base de conhecimento BNCC + regulacao financeira

**Outputs:**
- Licao completa: texto + roteiro de interacao + quiz de 5 perguntas
- 3 variantes de abordagem (para A/B test)
- Metadados: nivel de dificuldade, tempo estimado, conceitos cobertos

**Capacidade**: Gera **10-15 rascunhos de licoes por dia** (vs 1-2 por dia de um redator humano).

```
Exemplo — Brief recebido:
"Licao sobre juros compostos, faixa Arvore, formato simulador, contexto games"

Output do Agente:
─────────────────────────────────────
TITULO: "O Power-Up do Seu Dinheiro"

INTRODUCAO (60 segundos):
"Sabe quando no jogo voce pega um item que multiplica
seus pontos? Juros compostos sao o power-up do dinheiro
real. Cada mes, seus juros ganham juros — e o crescimento
acelera como um combo infinito."

SIMULADOR INTERATIVO:
- Slider: "Quanto voce investe por mes?" (R$10 - R$500)
- Slider: "Taxa de juros anual" (6% - 15%)
- Slider: "Por quantos anos?" (1 - 30)
- Grafico: curva de crescimento com animacao
- Comparacao: "Com R$50/mes a 12% por 10 anos = R$11.501"
              "Sem juros compostos seria apenas R$6.000"
              "O power-up te deu R$5.501 de bonus!"

QUIZ (5 perguntas, dificuldade progressiva):
1. [Basica] "Juros compostos sao juros sobre..."
2. [Media] "R$100 a 10%/ano. Apos 2 anos, quanto?"
3. [Media] "Por que comecar cedo importa?"
4. [Avancada] "Regra do 72: quanto tempo pra dobrar a 12%?"
5. [Desafio] "Calcule: R$200/mes, 13%/ano, 5 anos"

DESAFIO PRATICO:
"Pergunte pro seu pai quanto rende o investimento dele
por mes. Calcule: em 10 anos, quanto o rendimento
vai ter rendido? (juros sobre juros!)"

VARIANTE B (contexto futebol):
"Se o Neymar investisse 1 mes de salario a 12%/ano..."

VARIANTE C (contexto musica):
"Se a Taylor Swift colocasse o lucro de 1 show no Tesouro..."
─────────────────────────────────────
```

##### Agente 3: Pedagogo Digital

**Funcao**: Valida o conteudo gerado contra criterios pedagogicos e de acuracia.

**Checks automaticos:**
- Linguagem adequada para a faixa etaria? (vocabulario, complexidade de frase)
- Conceitos financeiros corretos? (calculos, definicoes, regulacao)
- Alinhado a BNCC? (competencias mapeadas)
- Nivel de dificuldade consistente com a faixa?
- Perguntas do quiz tem resposta correta inequivoca?
- Nenhum vies ou estereotipo? (genero, classe social, raca)

**Output**: Score de qualidade (0-100) + lista de issues encontrados.

```
Exemplo:
{
  "score": 87,
  "status": "aprovado_com_ajustes",
  "issues": [
    {
      "tipo": "linguagem",
      "local": "introducao",
      "problema": "Palavra 'combo' pode nao ser familiar para todos na faixa 12-14",
      "sugestao": "Adicionar: '(como quando voce acumula pontos bonus no jogo)'"
    },
    {
      "tipo": "acuracia",
      "local": "quiz_pergunta_4",
      "problema": "Regra do 72 da 6 anos a 12%, nao 6.17 como na resposta",
      "sugestao": "Simplificar para '~6 anos' e explicar que e uma aproximacao"
    }
  ]
}
```

**Apos checks**: Conteudo com score >85 vai direto para review humano. Score <85 volta para o Agente 2 com as correcoes.

##### REVIEW HUMANO (Pedagogo)

O pedagogo humano **nao cria do zero** — ele:
- Revisa o rascunho ja validado pelo Agente 3
- Ajusta nuances de tom e linguagem
- Verifica se a experiencia de aprendizado faz sentido como um todo
- Aprova ou solicita ajustes (que voltam para o Agente 2)

**Tempo medio de review**: 15-20 minutos por licao (vs 4-8 horas para criar do zero).

**Taxa de aprovacao na primeira review**: ~70% (melhora com o tempo conforme AI aprende o estilo do pedagogo).

##### Agente 4: Contextualizador

**Funcao**: Pega conteudo aprovado e gera variantes contextualizadas por interesse do usuario.

**Input**: Licao base aprovada + lista de contextos populares (futebol, games, musica, tech, moda)

**Output**: N variantes da mesma licao com exemplos diferentes.

```
Licao base: "Juros Compostos"

Variante futebol:
  "Se o Palmeiras investisse a premiacao da Libertadores (R$25M)..."

Variante games:
  "Uma skin rara vale R$200 hoje. Se voce investisse esse valor..."

Variante musica:
  "O Spotify paga R$0,004 por stream. Quanto um artista com 1M de streams..."

Variante tech:
  "O iPhone 1 custava US$499 em 2007. Ajustado pela inflacao..."
```

**Volume**: 1 licao base → 5-8 variantes contextuais em **minutos** (vs dias manualmente).

##### Agente 5: A/B Tester

**Funcao**: Gerencia experimentos de conteudo automaticamente.

**Como funciona:**
1. Recebe 2-3 variantes de uma licao (formato diferente, contexto diferente, ou abordagem diferente)
2. Distribui aleatoriamente para usuarios da mesma faixa
3. Mede: taxa de conclusao, score no quiz, retorno no dia seguinte, tempo na licao
4. Declara vencedor quando atinge significancia estatistica
5. Promove vencedor, arquiva perdedores, gera insight para o Agente Gerador

```
Experimento #247:
  Licao: "Orcamento Inteligente" (faixa Broto)
  Variante A: Formato historia animada
  Variante B: Formato simulador interativo
  Variante C: Formato quiz-first (quiz antes da licao)

  Resultado (apos 500 usuarios/variante):
  - A: 72% conclusao, score medio 68%, 45% retorno D+1
  - B: 85% conclusao, score medio 74%, 62% retorno D+1  ← VENCEDOR
  - C: 61% conclusao, score medio 71%, 38% retorno D+1

  Insight gerado: "Para faixa Broto, tema orcamento, formato simulador
  supera historia e quiz-first em todas as metricas.
  Aplicar para futuras licoes de orcamento nesta faixa."
```

##### Agente 6: Otimizador

**Funcao**: Analisa dados de todos os agentes e melhora o sistema continuamente.

**Analises:**
- Quais tipos de brief geram conteudo com maior taxa de aprovacao pelo pedagogo?
- Quais contextos funcionam melhor por faixa etaria e regiao?
- Quais formatos tem melhor retencao por micro-segmento?
- Quais periodos do ano tem melhor/pior engajamento?
- Quais licoes precisam de atualizacao (dados defasados, regulacao mudou)?

**Output**: Ajusta parametros dos outros agentes automaticamente.

```
Exemplo de ajuste:
"Agente 2: para faixa Broto + tema orcamento,
priorizar formato simulador (87% mais eficaz que historia).
Reduzir geracao de historias para este tema de 33% para 10%."
```

#### Economia da Producao AI vs Tradicional

| Metrica | Modelo Tradicional | Modelo GRANIX (AI + Agentes) | Reducao |
|---------|:-----------------:|:---------------------------:|:-------:|
| Custo por licao (criacao) | R$3.000-5.000 | R$300-600 | **~90%** |
| Tempo por licao (criacao) | 5-10 dias | **4-8 horas** (incl. review humano) | ~90% |
| Licoes produzidas/mes | 8-12 | **50-80** | 5-7x mais |
| Variantes contextuais/licao | 1 (generica) | **5-8** (por interesse) | 5-8x mais |
| Custo de localizacao/idioma | R$500-1.000/licao | R$50-100/licao | ~90% |
| Time necessario | 15-20 pessoas | **4-5 pessoas** | ~75% |
| Custo mensal de operacao | R$250-350K | **R$70-90K** | ~75% |

#### Projecao de Producao — Ano 1

| Mes | Licoes novas | Quizzes | Desafios | Variantes | Total piecas |
|:---:|:-----------:|:-------:|:--------:|:---------:|:------------:|
| 1-2 | 30 (manual + AI) | 60 | 15 | 60 | 165 |
| 3-4 | 50 (AI-dominant) | 100 | 30 | 200 | 380 |
| 5-8 | 40/mes | 80/mes | 25/mes | 200/mes | 345/mes |
| 9-12 | 50/mes | 100/mes | 30/mes | 300/mes | 480/mes |
| **Total Ano 1** | **~450** | **~900** | **~270** | **~2.600** | **~4.220** |

Com modelo tradicional, produzir 4.220 pecas de conteudo custaria **~R$12M** e 20+ pessoas por 12 meses.
Com AI + Agentes: **~R$1M** e 5 pessoas por 12 meses. **Economia de ~R$11M no Ano 1.**

#### Evolucao da Automacao ao Longo do Tempo

```
Ano 1:  Humano 40% ████████░░░░░░░░░░░░ AI 60%
        AI aprende estilo, pedagogo revisa tudo

Ano 2:  Humano 20% ████░░░░░░░░░░░░░░░░ AI 80%
        AI gera com alto score, pedagogo revisa amostragem

Ano 3:  Humano 10% ██░░░░░░░░░░░░░░░░░░ AI 90%
        AI auto-aprovado para formatos validados,
        humano foca em conteudo inedito e estrategia
```

O humano nunca desaparece — ele **sobe de nivel**: de criador de conteudo para **curador e estrategista**. Quanto mais a AI aprende, mais o humano pode focar no que importa: qualidade pedagogica e inovacao curricular.

---

### Pilar 3: Gamification SDK

Sistema de gamificacao completo como SDK embeddavel:

**Mecanicas:**
- XP Points (experiencia) por completar tarefas e licoes
- Niveis progressivos (Semente → Broto → Arvore → Floresta)
- Badges/Conquistas (ex: "Primeiro Objetivo", "30 dias aprendendo")
- Ranking familiar (entre irmaos)
- Desafios semanais personalizados por AI
- Streaks de aprendizado
- Avatar customizavel que evolui com o progresso

**API do SDK:**
```
// Instituicao integra assim:
GranixSDK.init({ theme: 'banco-marca', locale: 'pt-BR' })
GranixSDK.trackEvent('lesson_completed', { lessonId, score })
GranixSDK.getRecommendation(userId) // retorna proximo desafio
GranixSDK.getChurnRisk(userId) // retorna score de risco
```

**Diferencial**: Gamificacao alimentada por AI. Nao sao badges genericos — cada desafio e calibrado para o perfil individual do jovem. A dificuldade, o timing e a recompensa sao otimizados por machine learning.

---

### Pilar 4: Framework 4 Potes

Gastar / Guardar / Doar / Investir — metodologia visual de educacao financeira.

**O que GRANIX faz:**
- Componentes visuais para distribuicao entre os 4 potes
- Metas visuais por pote
- Progresso visual
- Licoes tematicas por pote
- Simuladores por pote (ex: calculadora de juros compostos para "Investir")

**O que GRANIX NAO faz:**
- Nao move dinheiro
- Nao acessa saldos reais
- Nao executa transacoes
- A instituicao alimenta os dados visuais via props

**Como funciona na pratica:**
```
// Instituicao passa dados para o componente:
<FourBuckets
  gastar={{ total: 150, meta: 200, label: "Mesada livre" }}
  guardar={{ total: 320, meta: 500, label: "Bicicleta" }}
  doar={{ total: 30, meta: 50, label: "ONG Animais" }}
  investir={{ total: 200, meta: 1000, label: "Tesouro Educa+" }}
  theme={bancoTheme}
/>
// GRANIX renderiza. Banco controla os dados.
```

---

## 4. MODELO DE NEGOCIO

### Quem paga: Cliente final (familia)

A instituicao financeira cobra a assinatura GRANIX via seu proprio billing. GRANIX recebe revenue share.

| Plano | Preco/mes | Inclui |
|-------|:---------:|--------|
| **Gratis** | R$0 | Academy limitada (1 licao/semana), 2 potes, tarefas basicas (3/mes) |
| **Premium** | R$19,90 | Academy completa com AI, 4 potes, tarefas ilimitadas, gamificacao basica |
| **Premium+** | R$39,90 | Tudo + AI personalizada avancada, multi-filhos, simuladores, relatorios, desafios exclusivos |

### Revenue Share

| Componente | GRANIX | Instituicao |
|------------|:------:|:-----------:|
| Assinatura Premium/Premium+ | **70%** | 30% |
| Transacoes financeiras | 0% | 100% |
| Interchange (cartao) | 0% | 100% |
| Float/Juros | 0% | 100% |
| Spread investimentos | 0% | 100% |

### Por que a instituicao aceita

- **30% de receita recorrente** sem custo de desenvolvimento
- **Retém 100%** do interchange, float e spread
- **CAC intergeracional**: Jovem de 10 anos → cliente adulto aos 18 com 8 anos de lealdade
- **Defesa competitiva**: Concorrentes ja tem conta de menor (Nubank, Inter, C6) — falta experiencia
- **Zero custo de build**: GRANIX entrega componentes + conteudo + AI prontos
- **Churn reduction**: AI de predicao de churn reduz abandono da conta familiar inteira

### Por que GRANIX aceita

- **Zero compliance financeiro** — e software puro
- **Distribuicao via base do parceiro** — sem custo de aquisicao de cliente
- **White-label escala** — mesmo produto para N instituicoes
- **AI como moat** — dados agregados (anonimizados) de todas as instituicoes alimentam modelos melhores
- **Receita recorrente** previsivel

### Validacao do Modelo

**Greenlight for Banks**: 150+ bancos parceiros pagam Greenlight US$3-8/familia/mes. JPMorgan e Wells Fargo investiram E se tornaram parceiros. Revenue US$228.5M (2024), valuation $3.2B.

**Banzai**: 750+ instituicoes financeiras pagam por educacao financeira como servico. Prova que bancos pagam por conteudo educativo.

**GoHenry/Acorns**: Subscription-only model, cobrado do cliente final. £30.6M revenue no UK.

---

## 5. AI COMO MOAT COMPETITIVO

### Por que AI e o moat (e nao os componentes)

Componentes React podem ser copiados. Conteudo estatico pode ser licenciado. **O que nao pode ser replicado**:

1. **Dados comportamentais agregados de milhoes de jovens** across instituicoes
2. **Modelos de predicao treinados** com anos de interacoes reais
3. **Efeito rede de AI**: cada nova instituicao melhora a AI para TODAS
4. **Velocidade de geracao de conteudo**: AI + pedagogos > so pedagogos
5. **Personalizacao em escala**: impossivel manualmente com 145+ licoes x N formatos x micro-segmentos

### Dados agregados criam vantagem composta

Cada instituicao que adota GRANIX contribui com dados comportamentais anonimizados:

| Tipo de dado | Exemplo | Valor para AI |
|-------------|---------|---------------|
| Engajamento por formato | "Simuladores retém 3x mais que videos na faixa 12-14" | Otimiza formato por perfil |
| Eficacia pedagogica | "Ensinar juros via historia antes de formula aumenta score em 25%" | Otimiza sequencia curricular |
| Sinais de churn | "Streak quebrado + pai inativo = 78% de churn em 30 dias" | Predicao precoce |
| Contextualizacao | "Conteudo sobre futebol engaja 2x mais que sobre politica para meninos 10-14" | Geracao de conteudo direcionado |
| Familiar | "Pai que usa app junto tem retencao 3x maior" | Otimiza features familiares |
| Sazonal | "Janeiro tem 40% menos engajamento (ferias)" | Ajuste de expectativas e conteudo |

**Efeito rede**: Com 1 instituicao, a AI conhece ~50K jovens. Com 7 instituicoes, conhece ~1.5M. Os modelos de predicao melhoram exponencialmente com volume. Uma instituicao sozinha NUNCA tera dados suficientes para treinar modelos comparaveis.

### Defesa contra "build in-house"

| O que a instituicao precisaria | Custo estimado | Tempo | GRANIX ja tem |
|-------------------------------|:--------------:|:-----:|:-------------:|
| Time de AI/ML (5 engenheiros) | R$1.5M/ano | Permanente | Sim |
| Time de pedagogos (3) | R$360K/ano | Permanente | Sim |
| 145 licoes por faixa etaria | R$500K | 12 meses | Sim |
| Modelos de predicao treinados | R$800K | 18 meses | Sim |
| Dados de comportamento juvenil | Impossivel | Anos | Sim (cross-instituicao) |
| A/B testing framework | R$200K | 6 meses | Sim |
| Manutencao de conteudo | R$300K/ano | Permanente | AI automatiza |
| **Total Ano 1** | **~R$3.7M** | **18 meses** | **Pronto** |

**A conta de "build vs buy" e brutal**: R$3.7M+ e 18 meses para chegar no ponto que GRANIX ja esta, sem os dados cross-instituicao que nunca terao.

### Stack Tecnico de AI

| Camada | Funcao | Tecnologia | Dados |
|--------|--------|-----------|-------|
| **Personalizacao** | Trilhas adaptativas, recomendacao | Recommendation engine (collaborative filtering + content-based) | Engajamento individual |
| **Predicao** | Comportamento + churn + readiness | Gradient boosting + LSTM para series temporais | Padroes agregados |
| **Geracao** | Conteudo, quizzes, desafios | LLMs fine-tuned para educacao financeira juvenil | Curriculo BNCC + gaps |
| **Otimizacao** | A/B testing + multi-armed bandit | Bayesian optimization | Metricas de aprendizado |
| **NLP** | Avaliacao de respostas abertas | LLMs com rubrics pedagogicas | Respostas de usuarios |
| **Segmentacao** | Micro-segmentos de usuarios | Clustering (k-means + DBSCAN) | Profiles comportamentais |

### Roadmap de AI

**Fase 1 (Meses 1-4) — Foundation:**
- Recomendacao basica por faixa etaria + formato
- Learning Profile inicial (5 features)
- Conteudo 100% manual, AI so recomenda sequencia

**Fase 2 (Meses 5-8) — Prediction:**
- Modelo de churn v1 (sinais fracos e medios)
- Acoes automaticas anti-churn (camada 1)
- Learning Profile expandido (15+ features)
- AI gera quizzes adaptativos (dificuldade calibrada)

**Fase 3 (Meses 9-14) — Generation:**
- AI gera licoes novas (gap detection + contextualizacao)
- Human-in-the-loop review pipeline
- A/B testing automatico de formatos
- Predicao de comportamento avancada
- Dashboard B2B com insights preditivos

**Fase 4 (Meses 15-24) — Intelligence:**
- Modelo de churn v2 com dados cross-instituicao
- Geracao automatizada de 50%+ do conteudo novo
- NLP para avaliacao de respostas abertas
- Benchmarking cross-instituicao
- Predicao de lifetime value familiar
- API de insights para assessores financeiros

---

## 6. GAP COMPETITIVO — ATUALIZADO

### Cenario Brasil (Contas de Menor)

| Instituicao | Conta | Tarefas | Educacao | Gamificacao | Investimento | 4 Potes | AI |
|-------------|:-----:|:-------:|:--------:|:-----------:|:------------:|:-------:|:--:|
| Nubank Familia | Sim | Nao | Nao | Nao | Nao | Nao | Nao |
| Inter Kids | Sim | Nao | Nao | Nao | Sim | Nao | Nao |
| C6 Yellow | Sim | Nao | Nao | Nao | Sim | Nao | Nao |
| NextJoy | Sim | Sim | Basico | Sim | Nao | Nao | Nao |
| BB Cash | Sim | Sim | Nao | Nao | Basico | Nao | Nao |
| BTG Conta Jovem | Sim | Nao | Nao | Nao | Sim | Nao | Nao |
| XP (sozinha) | Sim | Nao | Nao | Nao | Completo | Nao | Nao |
| **Qualquer + GRANIX** | **Sim** | **Sim** | **Sim** | **Sim** | **Parceiro** | **Sim** | **Sim** |

**Ninguem no Brasil combina educacao financeira gamificada + AI personalizada como componentes embeddaveis.**

---

## 7. PROJECOES FINANCEIRAS

### Premissas

- **Cenario base**: 1 instituicao parceira (XP) no Ano 1, expandindo para 3-5 no Ano 3
- Base XP: 4.8M clientes ativos
- Adocao: 1% (Ano 1) → 3% (Ano 3) → 5% (Ano 5)
- Mix de planos: 60% Free, 25% Premium (R$19,90), 15% Premium+ (R$39,90)
- Churn mensal: 5% (Ano 1) → 3% (Ano 3) → 2% (Ano 5) — AI reduz churn progressivamente
- Revenue share: 70% GRANIX / 30% instituicao

### Projecao 5 Anos — Cenario Base (XP + expansao)

| Metrica | Ano 1 | Ano 2 | Ano 3 | Ano 5 |
|---------|:-----:|:-----:|:-----:|:-----:|
| Instituicoes parceiras | 1 | 2 | 4 | 7 |
| Base total acessivel | 4.8M | 12M | 25M | 45M |
| Familias totais na plataforma | 48.000 | 180.000 | 500.000 | 1.500.000 |
| Familias pagantes (40%) | 19.200 | 72.000 | 200.000 | 600.000 |
| ARPU pagantes (blended) | R$24,90 | R$26,90 | R$28,90 | R$31,90 |
| Revenue bruto/mes | R$478K | R$1.94M | R$5.78M | R$19.1M |
| Revenue bruto/ano | R$5.7M | R$23.2M | R$69.4M | R$229.6M |
| **Share GRANIX (70%)** | **R$4.0M** | **R$16.3M** | **R$48.6M** | **R$160.7M** |
| Share instituicoes (30%) | R$1.7M | R$7.0M | R$20.8M | R$68.9M |

### Cenario Conservador (apenas XP, crescimento lento)

| Metrica | Ano 1 | Ano 2 | Ano 3 | Ano 5 |
|---------|:-----:|:-----:|:-----:|:-----:|
| Familias totais | 24.000 | 72.000 | 144.000 | 288.000 |
| Familias pagantes (40%) | 9.600 | 28.800 | 57.600 | 115.200 |
| Revenue bruto/ano | R$2.9M | R$9.3M | R$20.0M | R$44.1M |
| **Share GRANIX (70%)** | **R$2.0M** | **R$6.5M** | **R$14.0M** | **R$30.9M** |

---

## 8. ROADMAP

### Fase 1: Core Library + MVP Academy (Meses 1-4)

**Component Library:**
- Design system base (themeable, white-label)
- Componentes de Tarefas & Recompensas
- Componentes dos 4 Potes
- React + React Native (mono-repo)
- Documentacao de integracao para devs do parceiro

**AI Engine v1:**
- Personalizacao basica de trilhas por faixa etaria
- Recomendacao de proxima licao
- Conteudo inicial: 20 licoes por faixa etaria (80 total)
- Pipeline de conteudo com human-in-the-loop

**Meta**: Deploy com primeiro parceiro (XP) em ambiente de staging.

### Fase 2: Gamificacao + AI Avancada (Meses 5-8)

**Gamification SDK:**
- Sistema de XP Points, niveis, badges
- Avatar customizavel
- Desafios semanais (AI-generated)
- Ranking familiar

**AI Engine v2:**
- Predicao de churn (modelo treinado com dados do Fase 1)
- Acoes automaticas anti-churn
- A/B testing de formatos de conteudo
- Dashboard de insights para a instituicao

**Meta**: Lancamento publico com XP. Primeiros dados reais de comportamento.

### Fase 3: Geracao de Conteudo + Expansao (Meses 9-14)

**AI Engine v3:**
- Geracao automatizada de conteudo (com curadoria humana)
- Predicao de comportamento avancada
- Contextualizacao com eventos reais
- Conteudo em espanhol (LATAM)

**White-label:**
- Onboarding self-service para novas instituicoes
- Documentacao completa de integracao
- Segundo e terceiro parceiro

**Meta**: 3+ instituicoes ativas. AI gerando 50%+ do conteudo novo.

### Fase 4: Escala (Meses 15-24)

- AI de predicao de comportamento cross-instituicao
- Marketplace de conteudo (instituicoes contribuem)
- Parcerias com escolas (BNCC)
- Expansion LATAM (Mexico, Colombia, Argentina)
- Premium analytics para instituicoes

---

## 9. INVESTIMENTO NECESSARIO

### Pre-Seed: R$2.2M

| Categoria | Valor | % | Detalhe |
|-----------|:-----:|:-:|---------|
| Dev — Component Library | R$480K | 22% | 4 devs React/RN x 12 meses |
| Dev — AI/ML Engine | R$540K | 25% | 3 engenheiros ML x 12 meses |
| Design/UX | R$240K | 11% | 2 designers x 12 meses |
| Conteudo educativo | R$200K | 9% | 2 pedagogos + 1 editor x 12 meses |
| Infra Cloud + AI | R$180K | 8% | GPUs, hosting, CDN, APIs de LLM |
| Marketing / BD | R$120K | 5% | Business development + materiais de venda |
| PoC para 1o parceiro | R$50K | 2% | Customizacao + deploy + suporte de piloto |
| Legal + LGPD | R$80K | 4% | Contratos de revenue share, politica de privacidade, DPIA |
| ISO 27001 (certificacao) | R$100K | 5% | Consultoria + auditoria + implementacao |
| Registro de PI | R$30K | 1% | Marcas INPI + registro de software + deposito de curriculo |
| Buffer | R$180K | 8% | Contingencia (~8%) |

### Equipe Ano 1

| Fase | Pessoa | Perfil | Tipo | Custo/mes |
|:----:|--------|--------|:----:|:---------:|
| M1 | **CEO/Founder** (Toto) | Produto + estrategia + BD | Founder | Pro-labore |
| M1 | **CTO** | Full-stack senior + arquitetura React/RN | Founder ou contratacao #1 | R$18-25K |
| M1 | **AI/ML Lead** | ML engineer, NLP, recommendation systems | Contratacao #2 | R$18-25K |
| M1 | **Designer UX** | UI/UX para jovens, design system, branding | Contratacao #3 | R$12-15K |
| M2 | **Dev Frontend** | React + React Native, componentes | Contratacao #4 | R$12-18K |
| M2 | **Dev Frontend** | React + React Native, componentes | Contratacao #5 | R$12-18K |
| M3 | **Pedagogo Senior** | Curriculo financeiro, BNCC, review de conteudo | Contratacao #6 | R$8-12K |
| M3 | **Dev ML** | Modelos de predicao, pipeline de dados | Contratacao #7 | R$15-20K |
| M4 | **Dev Backend** | APIs, infra cloud, CDN, analytics | Contratacao #8 | R$12-18K |
| M5 | **Pedagogo Jr** | Review de conteudo AI-generated, quizzes | Contratacao #9 | R$5-8K |
| M6 | **Editor de Conteudo** | Curadoria, contextualizacao, localizacao | Contratacao #10 | R$6-10K |

**Total time Mes 12: 10-11 pessoas** (incluindo founder)
**Folha mensal estimada Mes 12: ~R$130-170K**

### O que NAO precisa

- R$0 em licenca bancaria
- R$0 em infra BaaS
- R$0 em compliance bancario
- R$0 em processamento de pagamentos
- R$0 em emissao de cartao
- R$0 em aquisicao de clientes (distribuicao via parceiro)
- R$0 em time comercial grande (BD focado, nao vendas em massa)

---

## 10. GO-TO-MARKET (GTM)

### Estrategia: White-label Multi-Instituicao desde o Dia 1

GRANIX nao e um produto para XP — e um produto para **qualquer instituicao financeira com conta de menor**. XP e o primeiro parceiro, mas o pipeline ja inclui outras instituicoes.

### Compradores na Instituicao

O produto interessa a 3 areas que devem ser abordadas simultaneamente:

| Area | Interesse | Argumento |
|------|-----------|-----------|
| **Produto Digital** | Experiencia do app, retencao, features competitivas | "Seus concorrentes ja tem experiencia jovem. Voce nao. Aqui esta o plug-and-play." |
| **Inovacao** | Diferenciacao, AI, tendencias de mercado | "AI personalizada para educacao financeira juvenil. Nenhum banco no Brasil tem isso." |
| **Marketing** | Aquisicao de familias, marca, CAC intergeracional | "Captura a proxima geracao de clientes com CAC zero. Jovem de 10 anos → adulto investidor aos 18." |

### Ciclo de Vendas

```
FASE 1: ABERTURA (Semana 1-2)
│
├── Approach: Contato com head de Produto, Inovacao OU Marketing
├── Material: Demo interativa (prototipo navegavel) + deck de 10 slides
├── Entregavel: Prototipo white-label com marca da instituicao (mockup)
├── Objetivo: Reuniao de 30 min para mostrar o gap + a solucao
│
▼
FASE 2: POC TECNICA (Semanas 3-8)
│
├── O que: 3-4 componentes GRANIX rodando no ambiente de staging da instituicao
├── Componentes da PoC:
│   ├── <OnboardingFlow> (questionario + momento aha)
│   ├── <LessonPlayer> (1 licao completa com quiz)
│   ├── <FourBuckets> (visualizacao dos 4 potes)
│   └── <AchievementBadge> (primeiro badge)
├── Theming: Aplicado com cores/fontes/logo da instituicao
├── Custo para GRANIX: ~R$30-50K (investimento proprio para fechar deal)
├── Custo para a instituicao: ZERO (risco zero para eles)
│
▼
FASE 3: PILOTO RESTRITO (Meses 2-4)
│
├── 500-1.000 familias reais selecionadas
├── Metricas monitoradas:
│   ├── Onboarding completion rate (meta: >85%)
│   ├── D7 retention (meta: >40%)
│   ├── D30 retention (meta: >25%)
│   ├── Lessons/week (meta: >2.5)
│   ├── Family co-engagement (meta: >50%)
│   └── NPS (meta: >50)
├── Relatorio semanal para a instituicao com dashboard
├── Ajustes de AI baseados em dados reais
│
▼
FASE 4: GO/NO-GO (Mes 4)
│
├── Apresentacao de resultados do piloto vs metas
├── Projecao de impacto para base completa
├── Negociacao de contrato comercial (revenue share, SLA, escopo)
├── Decisao: rollout ou ajuste
│
▼
FASE 5: ROLLOUT (Mes 5+)
│
├── Abertura gradual para base completa
├── Comunicacao: assessores + push in-app + email marketing (pela instituicao)
├── GRANIX suporta onboarding tecnico + ajustes de conteudo
├── Metricas em tempo real via dashboard B2B
```

### Pipeline de Instituicoes

| Prioridade | Instituicao | Base potencial | Status | Entrada via |
|:----------:|-------------|:--------------:|--------|-------------|
| 1 | XP / Banco Modal | 4.8M clientes | Target primario | Produto + Instituto XP |
| 2 | BTG Pactual | 3.5M clientes | Target | Inovacao (BTG+ digital) |
| 3 | Inter | 30M clientes | Target | Produto (Inter Kids) |
| 4 | Nubank | 90M clientes | Target futuro | Produto (Nubank Familia) |
| 5 | C6 Bank | 25M clientes | Target futuro | Marketing (C6 Yellow) |
| 6 | BB (Banco do Brasil) | 80M clientes | Target futuro | Inovacao + BB Cash |
| 7 | Bancos regionais | Variavel | Fase 3+ | Inbound via case studies |

### Processo de Onboarding da Instituicao (Tecnico)

Apos contrato assinado, o time de dev da instituicao integra GRANIX:

```
Semana 1: Setup
  ├── npm install @granix/components @granix/sdk
  ├── Configuracao de tema (cores, fontes, logo)
  ├── Setup de callbacks (eventos → backend da instituicao)
  └── Documentacao + canal de suporte dedicado

Semana 2-3: Integracao
  ├── Embed de componentes nas telas do app
  ├── Conexao de callbacks com APIs internas (tarefas → transferencia, etc.)
  ├── Testes de integracao em staging
  └── Review de seguranca pelo time da instituicao

Semana 4: Go-live
  ├── Feature flag para rollout gradual
  ├── Monitoramento conjunto (GRANIX dashboard + metricas da instituicao)
  └── Ajustes finos de conteudo/tema
```

**Tempo total de integracao: 3-4 semanas** (instituicao precisa alocar 1-2 devs).

### Material de Vendas

| Material | Formato | Para quem |
|----------|---------|-----------|
| Demo interativa | Prototipo navegavel white-label | Head de Produto |
| Deck de 10 slides | Problema → solucao → numeros → ask | C-level / VP |
| Case study piloto | Metricas reais de engajamento | Decisores |
| Docs de integracao | Portal tecnico | Time de dev da instituicao |
| ROI calculator | Planilha interativa | CFO / Business case |
| Benchmarking report | Comparacao competitiva | Marketing |

---

## 11. LGPD E PROTECAO DE DADOS DE MENORES

### Marco Legal

GRANIX opera sob 4 marcos regulatorios brasileiros para dados de menores:

#### LGPD — Lei Geral de Protecao de Dados (Lei 13.709/2018)

**Art. 14 — Tratamento de Dados de Criancas e Adolescentes:**

- **§1**: Tratamento de dados de **criancas** (menores de 12 anos) requer **consentimento especifico e em destaque** de pelo menos um dos pais ou responsavel legal
- **§2**: Controladores devem manter publicas as informacoes sobre tipos de dados coletados e a forma de utilizacao
- **§3**: Dados de criancas podem ser coletados sem consentimento APENAS para contatar pais (uso unico, sem armazenamento)
- **§4**: **Proibido condicionar** a participacao em jogos/apps ao fornecimento de dados alem dos estritamente necessarios — aplicacao direta ao GRANIX (free tier nao pode exigir dados extras)
- **§5**: Controlador deve empregar **todos os esforcos razoaveis** para verificar que o consentimento foi dado pelo responsavel (nao pela crianca)
- **§6**: Informacoes devem ser fornecidas de maneira **simples, clara e acessivel**, com uso de **recursos audiovisuais** quando adequado

**Art. 14, §6 — Aplicacao direta ao GRANIX**: O onboarding gamificado e visual atende ao requisito de comunicacao "simples, clara e acessivel" com "recursos audiovisuais".

**Distincao critica — Crianca vs Adolescente:**

| Categoria | Idade | Consentimento | Base legal |
|-----------|:-----:|--------------|-----------|
| **Crianca** | 0-11 anos | Consentimento especifico e em destaque do pai/responsavel (obrigatorio) | LGPD Art. 14 §1 |
| **Adolescente** | 12-17 anos | Outras bases do Art. 7o podem ser usadas, desde que prevaleca o melhor interesse | Enunciado ANPD n. 1/2023 |

**Enunciado CD/ANPD n. 1/2023**: A ANPD esclareceu que o consentimento parental NAO e a unica base legal para adolescentes. Outras bases do Art. 7o (como legitimo interesse ou execucao de contrato) podem ser usadas, **desde que o principio do melhor interesse prevaleca**.

#### ECA Digital — Lei 15.211/2025 (em vigor desde 17/03/2026) ⚠️ NOVO

O **Estatuto Digital da Crianca e do Adolescente** entrou em vigor em **17 de marco de 2026** — a legislacao mais recente e impactante para o GRANIX:

**Verificacao de Idade:**
- Plataformas devem adotar **mecanismos efetivos de verificacao de idade** (autodeclaracao NAO e suficiente)
- Dados coletados para verificacao de idade **nao podem ser usados** para fins comerciais ou personalizacao de conteudo
- **Impacto no GRANIX**: A verificacao de idade e feita pela instituicao financeira (KYC ja existente) — GRANIX se beneficia disso sem precisar implementar verificacao propria

**Controle Parental:**
- Plataformas devem fornecer ferramentas de controle parental
- **Impacto no GRANIX**: Dashboard do pai ja atende esse requisito

**Design Seguro (Privacy by Design):**
- Servicos digitais direcionados a menores devem ser projetados com **privacidade e seguranca integradas desde a concepcao**
- **Proibido monitoramento massivo** e vigilancia injustificada
- **Impacto no GRANIX**: Arquitetura Privacy by Design ja atende — GRANIX nao faz monitoramento massivo, so coleta dados de aprendizado anonimizados

**Publicidade e Monetizacao:**
- **Proibida publicidade baseada em perfilamento comportamental** para menores de 18
- Proibida monetizacao que manipule emocoes ou estimule consumo excessivo
- **Impacto no GRANIX**: GRANIX nao faz publicidade. A personalizacao da AI e para educacao, nao para venda — compliance total

**Sancoes:**
- Multas de ate **10% da receita bruta** no Brasil, limitada a **R$50 milhoes por infracao**
- Suspensao ou proibicao de atividades requer decisao judicial

**Cronograma de Implementacao pela ANPD:**

| Fase | Periodo | O que acontece |
|------|---------|---------------|
| Fase 1 (atual) | Marco 2026 | Parametros preliminares; monitoramento de "sinais de idade" em OS/app stores |
| Fase 2 | Agosto 2026 | ANPD publica parametros normativos detalhados; periodo de adaptacao ate Nov/2026 |
| Fase 3 | Janeiro 2027 | **Fiscalizacao plena com sancoes** |

**GRANIX ja esta em compliance** com o ECA Digital porque:
1. Nao coleta PII (verificacao de idade e feita pelo parceiro)
2. Oferece controle parental (dashboard do pai)
3. Privacy by Design desde a arquitetura
4. Zero publicidade comportamental
5. Nao monetiza dados de menores

#### ECA — Estatuto da Crianca e do Adolescente (Lei 8.069/1990)

- **Art. 100**: Principio do **melhor interesse da crianca** em qualquer decisao
- **Art. 17**: Direito a inviolabilidade da integridade fisica, psiquica e moral
- Interpretacao moderna inclui protecao de dados pessoais como parte da integridade
- **Definicoes de idade**: Crianca (0-11), Adolescente (12-17) — adotadas pela LGPD

#### Marco Civil da Internet (Lei 12.965/2014)

- **Art. 29**: Direito a protecao de dados pessoais na internet, inclusive de menores
- Reforco da necessidade de consentimento parental

### Arquitetura de Dados GRANIX — Privacy by Design

GRANIX adota **Privacy by Design** como principio arquitetural — a privacidade nao e um add-on, e a fundacao.

#### Separacao Radical de Dados

```
┌─────────────────────────────────────────────────────────────────────┐
│  DADOS QUE FICAM NA INSTITUICAO (GRANIX nunca ve)                  │
│                                                                     │
│  ├── Nome completo, CPF, RG                                        │
│  ├── Endereco, telefone, email                                      │
│  ├── Dados bancarios (conta, agencia, saldo)                        │
│  ├── Transacoes financeiras (PIX, cartao, investimentos)            │
│  ├── Biometria (se aplicavel)                                       │
│  ├── Dados de localizacao                                           │
│  └── Qualquer dado que identifique o usuario diretamente            │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────┐
│  DADOS QUE GRANIX CLOUD PROCESSA (anonimizados)                    │
│                                                                     │
│  ├── ID anonimo (hash, nao vinculavel a PII)                        │
│  ├── Faixa etaria (6-8, 9-11, 12-14, 15-17 — nao idade exata)     │
│  ├── Interesses declarados (games, futebol, musica)                 │
│  ├── Comportamento de aprendizado:                                  │
│  │   ├── Licoes completadas (IDs de conteudo, nao dados pessoais)   │
│  │   ├── Scores em quizzes                                          │
│  │   ├── Tempo em cada atividade                                    │
│  │   ├── Formato preferido (simulador, quiz, video)                 │
│  │   └── Padroes de sessao (frequencia, duracao, horarios)          │
│  ├── Progresso de gamificacao (XP, badges, streaks, nivel)          │
│  ├── Distribuicao percentual dos 4 Potes (%, nao valores)           │
│  └── Eventos de interacao familiar (frequencia, nao conteudo)       │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

#### 7 Principios de Privacy by Design Aplicados

| Principio | Aplicacao no GRANIX |
|-----------|-------------------|
| **1. Proativo, nao reativo** | Arquitetura desenhada com separacao de dados desde o dia 1 |
| **2. Privacidade como padrao** | Componentes nao recebem PII — so dados de display via props |
| **3. Privacidade embutida no design** | SDK nao tem metodos que acessem dados financeiros |
| **4. Funcionalidade total** | Personalizacao funciona 100% com dados anonimizados |
| **5. Seguranca fim-a-fim** | HTTPS, encriptacao em repouso, audit logs |
| **6. Visibilidade e transparencia** | Dashboard para pais verem exatamente o que e coletado |
| **7. Respeito pela privacidade do usuario** | Pai pode deletar todos os dados a qualquer momento |

### Consentimento Parental — Fluxo Tecnico

O fluxo de consentimento e integrado ao onboarding:

```
ATIVACAO (pelo pai, dentro do app da instituicao)
  │
  ▼
TELA DE CONSENTIMENTO (obrigatoria, antes do onboarding)
  │
  ├── Texto claro e acessivel (nao juridiques):
  │   "O programa [nome white-label] coleta dados de aprendizado
  │    do seu filho para personalizar a experiencia educacional.
  │    Nao coletamos nome, CPF, dados bancarios ou qualquer
  │    informacao financeira. Voce pode revogar a qualquer momento."
  │
  ├── Detalhamento expandivel:
  │   ├── "O que coletamos" (lista dos dados anonimizados)
  │   ├── "O que NAO coletamos" (lista explicita de PII/dados financeiros)
  │   ├── "Para que usamos" (personalizar licoes, recomendar conteudo)
  │   ├── "Por quanto tempo" (enquanto ativo, deletado em 30 dias apos cancelamento)
  │   └── "Seus direitos" (acesso, correcao, exclusao, portabilidade)
  │
  ├── Checkbox: "Li e concordo com o tratamento de dados descrito acima"
  │   (obrigatorio para menores de 12 — LGPD Art. 14 §1)
  │
  ├── Para menores de 12: Verificacao de que quem consente e o responsavel
  │   (validacao via autenticacao ja existente no app da instituicao)
  │
  └── Para 12-17: Consentimento do adolescente + ciencia do responsavel

REGISTRO DO CONSENTIMENTO
  ├── Timestamp
  ├── Versao do termo
  ├── IP (registrado pela instituicao)
  ├── ID do responsavel (na instituicao, nao na GRANIX)
  └── Armazenado por ambos (GRANIX guarda hash anonimo)
```

### Direitos do Titular (Pai/Responsavel)

| Direito LGPD | Como GRANIX implementa | Prazo |
|-------------|----------------------|:-----:|
| **Acesso** | Dashboard do pai mostra todos os dados coletados em tempo real | Instantaneo |
| **Correcao** | Pai pode corrigir faixa etaria e interesses diretamente | Instantaneo |
| **Exclusao** | Botao "Excluir meus dados" no app → exclusao completa | 48 horas |
| **Portabilidade** | Export em formato JSON dos dados de aprendizado | 5 dias |
| **Revogacao** | Desativar GRANIX → dados anonimizados, nao mais processados | Instantaneo |
| **Informacao** | Politica de privacidade acessivel, linguagem clara | Sempre disponivel |

### Roadmap de Certificacoes

| Certificacao | O que valida | Quando | Custo estimado |
|-------------|-------------|:------:|:--------------:|
| **ISO 27001** | Sistema de gestao de seguranca da informacao (ISMS) | Ano 1 (mes 8-12) | R$80-120K |
| **ISO 27701** | Extensao da 27001 para privacidade — **mais alinhada com LGPD** | Ano 2 (mes 14-18) | R$60-80K (incremental a 27001) |
| **ISO 27018** | Protecao de PII em cloud — relevante para dados de menores em nuvem | Ano 2 | R$40-60K (complementar) |
| **SOC 2 Type II** | Controles de seguranca, disponibilidade, confidencialidade | Ano 2 (mes 18-24) | R$150-250K |
| **Certificacao BNCC** | Alinhamento curricular com Base Nacional | Ano 1 (mes 6-10) | R$20-40K |
| **Selo ANPD** | Conformidade com LGPD (quando disponivel) | Quando ANPD publicar | TBD |

**ISO 27001 no Ano 1 e estrategico**: Institucoes financeiras exigem certificacoes de seguranca de fornecedores. Ter ISO 27001 antes de fechar o segundo parceiro e um diferencial competitivo massivo.

**ISO 27701 e a "certificacao LGPD"**: A ISO 27701 mapeia diretamente para os requisitos da LGPD, incluindo Art. 14. E cada vez mais exigida em contratos B2B e licitacoes publicas no Brasil. E a certificacao que mais demonstra due diligence em protecao de dados.

### Compliance como Vantagem Competitiva

O ECA Digital (em vigor desde 17/03/2026) criou **obrigacoes pesadas** para qualquer plataforma que atenda menores. A maioria das empresas vai gastar meses se adaptando. GRANIX ja nasce em compliance porque:

| Requisito ECA Digital | Status GRANIX | Porque |
|----------------------|:------------:|--------|
| Verificacao de idade efetiva | ✅ Compliant | Instituicao financeira ja faz KYC |
| Controle parental | ✅ Compliant | Dashboard do pai nativo |
| Privacy by Design | ✅ Compliant | Arquitetura separada desde o dia 1 |
| Zero publicidade comportamental | ✅ Compliant | GRANIX nao faz publicidade |
| Design seguro | ✅ Compliant | Zero PII na GRANIX Cloud |
| Nao manipulacao emocional | ✅ Compliant | Gamificacao para educacao, nao consumo |

**Argumento de vendas atualizado**: "Com o ECA Digital em vigor (multas de ate R$50M), voce precisa de um parceiro que ja nasce em compliance. GRANIX nunca toca em dados pessoais dos seus clientes menores. E o fornecedor de menor risco regulatorio possivel."

### Argumento de Vendas: Seguranca como Diferencial

```
"GRANIX e o parceiro mais seguro que voce pode ter:

1. Nunca vemos dados financeiros dos seus clientes
2. Nunca vemos dados pessoais identificaveis
3. Nosso SDK roda DENTRO do seu ambiente seguro
4. Nosso cloud so recebe comportamento anonimizado
5. Privacy by Design desde a arquitetura
6. ISO 27001 certificado
7. LGPD Art. 14 compliance total para menores
8. Pai tem controle total a qualquer momento

Compare com qualquer alternativa que exija API com seu core bancario."
```

---

## 12. KPIs E METRICAS DE SUCESSO

### North Star Metric

**MAU Pagantes Ativos** — Familias com pelo menos 1 sessao do jovem no mes que estao em plano Premium ou Premium+.

Esta metrica combina 3 dimensoes em 1 numero:
- **Adocao** (familia entrou na plataforma)
- **Engajamento** (jovem esta usando ativamente)
- **Monetizacao** (familia esta pagando)

Se MAU Pagantes Ativos cresce, o negocio esta saudavel.

### Framework de Metricas: AARRR + Learning

#### Aquisicao — "Familias entram?"

| Metrica | Descricao | Meta Ano 1 | Frequencia |
|---------|-----------|:----------:|:----------:|
| Instituicoes ativas | Parceiros com GRANIX em producao | 1-2 | Trimestral |
| Familias registradas | Total de familias que ativaram GRANIX | 48.000 | Mensal |
| Onboarding completion | % que completa as 5 telas do onboarding | >85% | Semanal |
| Custo por ativacao | Custo GRANIX para ativar 1 familia | <R$30 | Mensal |

#### Ativacao — "Familias engajam no primeiro uso?"

| Metrica | Descricao | Meta Ano 1 | Frequencia |
|---------|-----------|:----------:|:----------:|
| First lesson completion | % que completa 1a licao no dia da ativacao | >70% | Semanal |
| First badge earned | % que ganha 1o badge no dia da ativacao | >80% | Semanal |
| 4 Potes setup | % que configura pelo menos 1 pote | >60% | Semanal |
| D1 retention | % que volta no dia seguinte | >60% | Semanal |

#### Retencao — "Familias continuam?"

| Metrica | Descricao | Meta Ano 1 | Frequencia |
|---------|-----------|:----------:|:----------:|
| D7 retention | % ativo apos 7 dias | >40% | Semanal |
| D30 retention | % ativo apos 30 dias | >25% | Semanal |
| D90 retention | % ativo apos 90 dias | >15% | Mensal |
| Weekly active families | Familias com ≥1 sessao na semana | Track | Semanal |
| Lessons/week/user | Licoes completadas por semana | >2.5 | Semanal |
| Streak distribution | % com streak ativo (7d, 14d, 30d) | Track | Semanal |
| Family co-engagement | % com pai + filho ativos | >50% | Mensal |

#### Receita — "Familias pagam?"

| Metrica | Descricao | Meta Ano 1 | Frequencia |
|---------|-----------|:----------:|:----------:|
| Free-to-paid conversion | % free que converte para Premium/Premium+ | >15% | Mensal |
| MRR (GRANIX share) | Receita recorrente mensal (70%) | R$330K+ | Mensal |
| ARPU (pagantes) | Receita media por familia pagante | R$24,90 | Mensal |
| Monthly churn (pagantes) | % cancelamento de planos pagos | <5% | Mensal |
| Upgrade rate | % Premium que vai para Premium+ | >10% | Mensal |

#### Referencia — "Familias recomendam?"

| Metrica | Descricao | Meta Ano 1 | Frequencia |
|---------|-----------|:----------:|:----------:|
| NPS | Net Promoter Score | >50 | Trimestral |
| Organic referrals | Familias que vieram por indicacao | Track | Mensal |
| App store rating | Avaliacao na loja (se aplicavel) | >4.5 | Mensal |

#### Learning — "Jovens aprendem?" (Diferencial GRANIX)

| Metrica | Descricao | Meta Ano 1 | Frequencia |
|---------|-----------|:----------:|:----------:|
| Quiz average score | Media de acertos em quizzes | >70% | Semanal |
| Knowledge progression | % que avanca de nivel em 90 dias | >30% | Mensal |
| Practical challenges completed | Desafios do mundo real concluidos | >1/mes | Mensal |
| 4 Potes engagement | % que usa ativamente os 4 potes | >40% | Mensal |
| AI personalization accuracy | % de recomendacoes aceitas pelo usuario | >65% | Mensal |
| Content effectiveness | Score medio de licoes (conclusao x quiz x retorno) | Track | Semanal |

### Dashboard Operacional

```
┌─────────────────────────────────────────────────────────────┐
│  GRANIX COMMAND CENTER                                      │
│                                                             │
│  North Star: MAU Pagantes Ativos                            │
│  ████████████████████░░░░░░░░░░ 19.200 / 48.000 (40%)     │
│                                                             │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐      │
│  │ MRR      │ │ D30 Ret. │ │ Churn    │ │ NPS      │      │
│  │ R$330K   │ │ 28%      │ │ 4.2%     │ │ 54       │      │
│  │ ↑12%     │ │ ↑3pp     │ │ ↓0.8pp   │ │ ↑6       │      │
│  └──────────┘ └──────────┘ └──────────┘ └──────────┘      │
│                                                             │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐      │
│  │ Licoes/  │ │ Quiz     │ │ Family   │ │ AI       │      │
│  │ semana   │ │ Score    │ │ Co-eng   │ │ Accuracy │      │
│  │ 2.8      │ │ 73%      │ │ 52%      │ │ 68%      │      │
│  │ ↑0.3     │ │ ↑2pp     │ │ ↑4pp     │ │ ↑5pp     │      │
│  └──────────┘ └──────────┘ └──────────┘ └──────────┘      │
│                                                             │
│  Alertas:                                                   │
│  ⚠️ Churn risk: 340 familias em alerta laranja              │
│  ✅ AI anti-churn resgatou 89 familias esta semana          │
│  📈 Conversao free→pago subiu 2pp apos novo onboarding     │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## 13. UNIT ECONOMICS

### Por Familia Pagante (Blended)

ARPU blended considera mix de 62.5% Premium (R$19,90) e 37.5% Premium+ (R$39,90):
**ARPU blended = R$27,40/mes**

| Item | Valor/mes | % da receita |
|------|:---------:|:------------:|
| Receita bruta | R$27,40 | 100% |
| Share instituicao (30%) | -R$8,22 | -30% |
| **Receita liquida GRANIX** | **R$19,18** | **70%** |
| Custo AI/infra por usuario | -R$1,50 | -5.5% |
| Custo conteudo por usuario | -R$0,80 | -2.9% |
| Custo suporte (proporcional) | -R$0,50 | -1.8% |
| **Margem bruta por familia** | **R$16,38** | **~60%** |

### CAC (Custo de Aquisicao de Cliente)

| Canal | CAC | Como |
|-------|:---:|------|
| Distribuicao via parceiro (organico) | **R$15-25** | Assessor recomenda, push in-app, email marketing da instituicao |
| Marketing direcionado (via instituicao) | **R$30-50** | Campanhas pagas pela instituicao com subsido GRANIX |
| **CAC blended** | **~R$22** | Estimativa com 70% organico / 30% pago |

Sem parceiro (hipotetico D2C): CAC seria R$150-300 (app install + ativacao + conversao).
**A parceria reduz CAC em ~90%.**

### LTV (Lifetime Value)

| Parametro | Valor | Calculo |
|-----------|:-----:|---------|
| Churn mensal (pagantes) | 4% | Estimativa conservadora |
| Vida media do cliente | 25 meses | 1 / churn mensal |
| Receita GRANIX/mes | R$19,18 | Apos share da instituicao |
| **LTV** | **R$479** | Vida media x receita/mes |

Com melhoria de churn via AI (meta: 3% no Ano 2):
- Vida media: 33 meses
- **LTV projetado Ano 2: R$633**

### Ratios

| Ratio | Valor | Benchmark | Status |
|-------|:-----:|:---------:|:------:|
| **LTV / CAC** | **21.8x** | >3x saudavel, >10x excelente | Excelente |
| **Payback period** | **1.3 meses** | <12 meses saudavel | Excelente |
| **Margem bruta** | **~60%** | >50% SaaS saudavel | Bom |

### Por que os Unit Economics sao tao bons?

1. **CAC quase zero**: A instituicao faz a distribuicao — GRANIX nao gasta com aquisicao
2. **LTV alto**: Produto de engajamento familiar com ciclo longo (crianca de 6 → adulto de 18)
3. **Margem alta**: Custo marginal por usuario e muito baixo (AI + CDN, nao humanos)
4. **Churn controlado**: AI de predicao + gamificacao + envolvimento do pai reduzem abandono
5. **Upsell natural**: Familias crescem de Free → Premium → Premium+ ao longo do tempo

### Evolucao dos Unit Economics

| Metrica | Ano 1 | Ano 2 | Ano 3 | Ano 5 |
|---------|:-----:|:-----:|:-----:|:-----:|
| ARPU blended | R$27,40 | R$28,90 | R$30,50 | R$33,00 |
| CAC blended | R$22 | R$18 | R$15 | R$12 |
| Churn mensal | 4.0% | 3.0% | 2.5% | 2.0% |
| LTV | R$479 | R$633 | R$813 | R$1.117 |
| LTV/CAC | 21.8x | 35.2x | 54.2x | 93.1x |
| Payback (meses) | 1.3 | 1.1 | 0.9 | 0.7 |

Os unit economics **melhoram com o tempo** porque:
- AI reduz churn progressivamente (mais dados = melhor predicao)
- CAC cai com mais instituicoes (efeito de escala)
- ARPU sobe com upsell natural (familias migram para planos maiores)
- Custo por usuario cai (infra de AI escala sublinearmente)

---

## 14. VISAO DE LONGO PRAZO — DE FINTECH LIBRARY A EDTECH PLATFORM

### Evolucao em 3 Fases

```
FASE 1: COMPONENT LIBRARY (Anos 1-2)
  "Embeddamos educacao financeira em bancos"
  │
  ├── Produto: Components + AI + Conteudo para instituicoes financeiras
  ├── Mercado: Bancos/corretoras brasileiras com conta de menor
  ├── Receita: Assinatura via parceiro, 70/30 split
  ├── Meta: 3-5 instituicoes parceiras, R$15-25M ARR
  │
  ▼
FASE 2: EDTECH PLATFORM (Anos 3-5)
  "Somos a plataforma de educacao financeira da America Latina"
  │
  ├── Produto anterior + novos verticais:
  │   ├── Educacao financeira para ADULTOS (onboarding de clientes novos)
  │   ├── Parcerias com ESCOLAS (conteudo BNCC para professores)
  │   ├── Treinamento de ASSESSORES (educacao financeira como ferramenta de vendas)
  │   ├── Expansao LATAM (espanhol: Mexico, Colombia, Argentina)
  │   └── Marketplace de conteudo (instituicoes contribuem + monetizam)
  ├── Mercado: Educacao financeira B2B ampla
  ├── Receita: Multi-stream (SaaS + licensing + marketplace)
  ├── Meta: 15-30 instituicoes, R$80-150M ARR
  │
  ▼
FASE 3: AI EDUCATION INFRASTRUCTURE (Anos 5-10)
  "Somos a infraestrutura de educacao personalizada"
  │
  ├── AI Engine generalizada para OUTROS DOMINIOS de educacao:
  │   ├── Educacao financeira (core, consolidado)
  │   ├── Educacao em saude (habitos saudaveis para jovens)
  │   ├── Educacao ambiental (sustentabilidade gamificada)
  │   ├── Educacao civica (cidadania e participacao)
  │   └── API aberta: qualquer empresa embeda educacao personalizada
  ├── Mercado: Educacao personalizada global
  ├── Receita: Platform fees + API usage + enterprise contracts
  ├── Meta: Plataforma de referencia em educacao personalizada
  │
  └── Possivel exit: Aquisicao por EdTech global (Duolingo, Khan Academy,
      Coursera) ou por instituicao financeira que quer internalizar
      a capacidade (XP, Nubank, BTG)
```

### Cenarios de Exit

| Cenario | Timing | Valuation estimado | Comprador potencial |
|---------|:------:|:------------------:|-------------------|
| Aquisicao por instituicao financeira | Ano 3-5 | 8-12x ARR = R$120-300M | XP, Nubank, BTG, Inter |
| Aquisicao por EdTech global | Ano 5-7 | 10-15x ARR = R$800M-2B | Duolingo, Coursera, Khan Academy |
| IPO / exit independente | Ano 7-10 | 15-20x ARR | Mercado |
| Operacao independente (lifestyle) | Ongoing | Distribuicao de lucros | Founders |

**O caminho mais provavel**: Construir valor como edtech especializada em educacao financeira, consolidar LATAM, e ser adquirida por uma EdTech global que quer entrar no mercado de educacao financeira, ou por uma instituicao financeira que quer internalizar a capacidade.

### Expansao para Educacao de Adultos (Fase 2)

O mesmo motor de AI + componentes serve para educar **adultos novos** nas instituicoes financeiras:

| Publico | Caso de uso | Valor para a instituicao |
|---------|-----------|-------------------------|
| Cliente novo (adulto) | Onboarding financeiro gamificado | Reduz churn de 90 dias, aumenta AUM |
| Cliente intermediario | Educacao sobre produtos avancados | Aumenta cross-sell (de poupanca para fundos) |
| Assessor financeiro | Treinamento em educacao do cliente | Melhora qualidade do atendimento |
| Funcionarios | Educacao financeira corporativa | Bem-estar financeiro → produtividade |

**A AI ja treinada com jovens se adapta para adultos** — os modelos de personalizacao, predicao de churn e geracao de conteudo sao transferiveis.

---

## 15. COMPETITIVE MOAT TIMELINE — QUANDO O MOAT FICA INVENCIVEL

### Evolucao da Barreira Competitiva

```
MES 1-6: MOAT FRACO
  Barreira: Velocidade de execucao + design de produto
  Replicabilidade: Alta (qualquer um pode fazer componentes React)
  Defesa: Primeiro a entregar PoC funcional para parceiro

MES 7-12: MOAT MEDIO
  Barreira: Conteudo validado (145+ licoes) + primeiro parceiro ativo
  Replicabilidade: Media (conteudo leva tempo, mas e possivel)
  Defesa: Dados de comportamento do piloto + relacao com parceiro
  + Novo: ISO 27001 certificado

MES 13-24: MOAT FORTE
  Barreira: AI treinada com dados reais + 3+ parceiros + curriculo extenso
  Replicabilidade: Baixa (dados de comportamento nao sao replicaveis)
  Defesa: Modelos de predicao calibrados + efeito rede incipiente
  + Novo: Pipeline de conteudo AI gerando 50%+ automaticamente

MES 25-36: MOAT MUITO FORTE ← PONTO DE INFLEXAO
  Barreira: Dados cross-instituicao + AI auto-geradora + marca
  Replicabilidade: Muito baixa
  Defesa: Nenhuma instituicao sozinha tem dados comparaveis
  + Novo: Benchmarking cross-instituicao (cada parceiro depende
    dos dados agregados de todos)

MES 37+: MOAT INVENCIVEL
  Barreira: Efeito rede consolidado + padrao de mercado
  Replicabilidade: Quase impossivel
  Defesa: GRANIX e a referencia — "the Greenlight of LATAM"
  + Construir internamente custa R$3.7M+ e 18 meses
    MAS sem os dados cross-instituicao que GRANIX ja tem
```

### O Que Cria Cada Camada de Moat

| Camada | O que e | Quando fica forte | Custo para replicar |
|--------|---------|:-----------------:|:-------------------:|
| **Componentes UI** | Library React/RN white-label | Sempre fraco | R$500K, 4 meses |
| **Conteudo curricular** | 145+ licoes por faixa etaria | Mes 6+ | R$800K, 8 meses |
| **AI de personalizacao** | Recomendacao + dificuldade adaptativa | Mes 12+ | R$1.5M, 12 meses |
| **Dados comportamentais** | Padroes de milhoes de jovens | Mes 18+ | **Impossivel sem base de usuarios** |
| **AI de predicao** | Churn + comportamento + readiness | Mes 24+ | **Impossivel sem dados historicos** |
| **Efeito rede cross-instituicao** | AI melhor para todos com cada parceiro novo | Mes 30+ | **Impossivel replicar** |
| **Padrao de mercado** | GRANIX como default da industria | Mes 36+ | **Impossivel replicar** |

### A "Death Zone" do Competidor

Um competidor que comece hoje precisaria:

```
Ano 0: Construir componentes + conteudo              R$1.3M, 8 meses
Ano 1: Conseguir primeiro parceiro + piloto           6 meses de vendas
Ano 1.5: Treinar AI com dados do piloto              6 meses de dados
Ano 2: Ter AI minimamente funcional                   12 meses de iteracao
Ano 2.5: Segundo parceiro                             6 meses de vendas
Ano 3: Comecar a ter dados cross-instituicao          6+ meses

TOTAL: ~3 anos e R$3-5M para chegar onde GRANIX estava 3 anos antes.

E durante esses 3 anos, GRANIX:
- Ja tem 5-7 parceiros
- Ja tem AI treinada com 500K+ familias
- Ja tem efeito rede consolidado
- Ja expandiu para adultos e LATAM
```

**O competidor esta sempre 3 anos atras.** E a cada ano que passa, a distancia AUMENTA (porque o efeito rede acelera).

---

## 16. CENARIOS DE STRESS E PLANO B

### Cenario 1: XP Diz Nao

**Probabilidade**: 40%
**Impacto**: Alto (atrasa 3-6 meses, nao mata)

**Por que pode acontecer:**
- Politica interna (area de produto nao quer dependencia externa)
- Timing ruim (XP focada em outro projeto)
- Preco/termos nao aceitos

**Plano B:**
- Pipeline ja inclui BTG, Inter, C6, BB
- BTG Pactual e alternativa natural (#2 em investimentos, conta jovem recente)
- Inter tem 30M clientes e Inter Kids ja existe (sem gamificacao)
- Abordagem: "XP ainda esta decidindo. Voces querem sair na frente?"
- A PoC white-label funciona para QUALQUER parceiro — zero lock-in com XP
- **Acao imediata**: Iniciar conversas com BTG e Inter em paralelo com XP

### Cenario 2: Churn Fica em 8% (Dobro do Esperado)

**Probabilidade**: 25%
**Impacto**: Alto (LTV cai 50%, modelo fica apertado)

**Numeros do stress:**
| Metrica | Cenario base (4%) | Cenario stress (8%) |
|---------|:-----------------:|:-------------------:|
| Vida media | 25 meses | 12.5 meses |
| LTV | R$479 | R$240 |
| LTV/CAC | 21.8x | 10.9x |
| Payback | 1.3 meses | 1.3 meses |

**Analise**: Mesmo com churn de 8%, LTV/CAC de 10.9x ainda e excelente (benchmark SaaS saudavel e >3x). O modelo sobrevive.

**Plano B:**
- Ativar AI anti-churn mais agressivamente (Camada 2 e 3 automaticas)
- Investigar causa raiz: conteudo? UX? falta de novidade? pai desengajado?
- Reduzir free tier (forcar conversao mais rapida, reduzir usuarios "turistas")
- Adicionar features de retencao: eventos ao vivo, competicoes mensais, conteudo sazonal
- Se persistir: ajustar pricing (aumentar Premium para compensar LTV menor)

### Cenario 3: AI Nao Reduz Churn (Modelos Nao Performam)

**Probabilidade**: 30%
**Impacto**: Medio (perde diferencial, mas produto base funciona)

**Por que pode acontecer:**
- Dados insuficientes para treinar modelos robustos
- Sinais de churn nao sao preditivos o suficiente
- Acoes anti-churn nao mudam comportamento

**Plano B:**
- Conteudo e gamificacao sao o produto base — funcionam SEM AI de predicao
- AI de personalizacao (recomendacao de conteudo) e mais simples e funciona com menos dados
- Reduzir investimento em AI de predicao, realocar para conteudo e gamificacao
- Compensar com gamificacao mais forte (competicoes, eventos, social features)
- AI evolui quando tiver mais dados (paciencia, nao pivo)

### Cenario 4: Instituicao Constroi Internamente

**Probabilidade**: 15%
**Impacto**: Alto (perde parceiro)

**Por que pode acontecer:**
- Instituicao grande (Nubank, Inter) decide que quer internalizar
- Ve os dados de engajamento e quer manter tudo in-house

**Plano B:**
- Contrato com clausula de exclusividade temporal (12-24 meses)
- Mostrar custo real: R$3.7M+ e 18 meses para replicar, SEM dados cross-instituicao
- Diversificar base de parceiros (nunca depender de 1 so)
- Antecipar: oferecer contrato multi-ano com desconto progressivo
- Se acontecer: usar como case study ("Instituicao X construiu internamente e gastou 3x mais para ter 50% do resultado")

### Cenario 5: Regulacao ANPD Restringe Coleta de Dados de Menores

**Probabilidade**: 20%
**Impacto**: Medio-Alto

**Por que pode acontecer:**
- ANPD na Fase 3 (Jan/2027) cria restricoes que limitam dados comportamentais
- Pressao publica por protecao de dados de menores

**Plano B:**
- GRANIX ja e conservador (zero PII, dados anonimizados)
- Se restringir dados comportamentais: AI funciona on-device (federated learning)
- Modelo de conteudo estatico (sem personalizacao) como fallback
- Compliance precoce (ISO 27001, ISO 27701) posiciona GRANIX como referencia
- **Oportunidade disfarçada**: Regulacao mais dura mata competidores menos preparados

### Resumo: Resiliencia do Modelo

| Cenario | O modelo sobrevive? | Por que |
|---------|:-------------------:|---------|
| XP diz nao | ✅ Sim | White-label funciona para qualquer parceiro |
| Churn 8% | ✅ Sim | LTV/CAC ainda e 10.9x (saudavel) |
| AI nao performa | ✅ Sim | Conteudo + gamificacao sao o produto base |
| Parceiro internaliza | ✅ Sim | Diversificacao + contrato multi-ano |
| Regulacao restringe dados | ✅ Sim | Ja conservador + federated learning como fallback |
| TODOS juntos | ⚠️ Dificil | Precisa pivotar para edtech D2C ou licensing de conteudo |

**O modelo e resiliente porque o valor core (conteudo + gamificacao) funciona independentemente de AI, parceiro especifico ou regulacao. AI e o turbo, nao o motor.**

---

## 17. PROPRIEDADE INTELECTUAL

### O que e patenteavel no Brasil? (Resposta curta: quase nada do GRANIX)

A Lei de Propriedade Industrial (Lei 9.279/96, Art. 10) exclui explicitamente:

- **Art. 10, III**: Metodos **comerciais, financeiros e educacionais** → A metodologia dos 4 Potes NAO e patenteavel (e duplamente excluida: e financeira E educacional)
- **Art. 10, V**: **Programas de computador em si** → O software GRANIX NAO e patenteavel
- **Art. 10, I**: Metodos matematicos → Algoritmos de AI/ML NAO sao patenteaveis como metodos matematicos puros

**Mesmo com AI, metodos financeiros e educacionais continuam excluidos.** As Diretrizes de Exame do INPI (Consulta Publica 03/2025) confirmam que metodos nas categorias excluidas permanecem nao patenteaveis mesmo quando implementados via AI.

### Estrategia de PI do GRANIX — 7 Camadas

Como patentes nao se aplicam, a protecao e construida em camadas alternativas:

| Prioridade | Instrumento | O que protege | Lei | Acao | Custo |
|:----------:|------------|--------------|-----|------|:-----:|
| **1** | **Marca** (INPI) | Nome "GRANIX", logo, "4 Potes", nomes de produto | Lei 9.279/96, Arts. 122-175 | Registrar em Classes 36 (financeiro), 41 (educacao), 42 (tech) | R$2-5K |
| **2** | **Segredo Industrial** | Algoritmos de AI, modelos treinados, pipelines de dados, metodologia operacional | Lei 9.279/96, Arts. 195 XI-XIV | NDAs com todos + politicas de confidencialidade + controles de acesso | R$5-10K (legal) |
| **3** | **Direito Autoral** (software) | Codigo-fonte e objeto do GRANIX | Lei 9.609/98, Art. 2 | Automatico (registro INPI opcional, mas recomendado) | R$1-3K |
| **4** | **Direito Autoral** (conteudo) | Licoes, curriculo escrito, videos, quizzes, ilustracoes | Lei 9.610/98, Art. 7 | Automatico + deposito na Biblioteca Nacional para evidencia | R$1-2K |
| **5** | **Desenho Industrial** | Interface visual do app, design system, telas distintivas | Lei 9.279/96, Arts. 94-121 | Registro INPI dos layouts mais distintos | R$3-5K |
| **6** | **Contrato de PI** | Tudo desenvolvido por funcionarios e freelancers | Lei 9.609/98, Arts. 3-4 | Clausula de cessao de PI em TODOS os contratos | R$3-5K (legal) |
| **7** | **First-mover + marca** | Posicionamento de mercado | — | Ser sinonimo de "educacao financeira para jovens" | Marketing |

### Detalhes Criticos

#### Marca "GRANIX" e "4 Potes"

- Registrar IMEDIATAMENTE em 3 classes INPI: 36 (financeiro), 41 (educacao), 42 (tecnologia)
- Processo INPI: 12-18 meses, mas direitos contam a partir da data de deposito
- Protecao: 10 anos, renovavel indefinidamente
- Considerar registro via Protocolo de Madrid para protecao internacional (LATAM)

#### Segredo Industrial (o mais importante para AI)

Os modelos de AI, pesos treinados, pipelines de dados e a logica dos agentes de conteudo sao protegidos como **segredo industrial**:

- **5 requisitos legais**: (1) relacionado a atividade empresarial, (2) tem utilidade, (3) tem valor economico por ser nao-publico, (4) e confidencial, (5) sujeito a medidas de protecao ativas
- **Violacao e crime**: Art. 195, XI e XII da Lei 9.279/96 (concorrencia desleal)
- **Protecao sem prazo**: dura enquanto a confidencialidade for mantida
- **Implementacao**: NDAs especificos, controles de acesso por camada, documentacao de politicas

#### Direito Autoral do Curriculo

- O **conceito** de ensinar financas em "4 potes" NAO e protegivel (Art. 8, Lei 9.610/98 exclui ideias e metodos)
- A **expressao escrita** do curriculo (texto das licoes, videos, quizzes, ilustracoes) E protegida automaticamente
- Protecao do software: **50 anos** a partir da publicacao (Lei 9.609/98)
- Protecao do conteudo: **70 anos** post-mortem auctoris (Lei 9.610/98)
- **Competidor pode legalmente** criar seu proprio curso de "educacao financeira com alocacao em baldes" — mas NAO pode copiar o conteudo especifico do GRANIX

### O que NAO pode ser protegido (aceitar e mitigar)

| O que | Por que nao | Mitigacao |
|-------|-----------|-----------|
| Conceito dos "4 Potes" | Metodo financeiro/educacional (Art. 10, III) | Marca + first-mover + ser sinonimo |
| Algoritmo de recomendacao | Metodo matematico (Art. 10, I) | Segredo industrial + vantagem de dados |
| Ideia de gamificacao educacional | Conceito abstrato | Execucao superior + dados de comportamento |
| Formato de onboarding | Metodo educacional | Marca + UX design registrado |

### Orcamento de PI — Ano 1

| Item | Custo | Quando |
|------|:-----:|:------:|
| Registro de marca INPI (3 classes) | R$5K | Mes 1 |
| Registro de software INPI | R$2K | Mes 3 |
| Deposito de curriculo (Biblioteca Nacional) | R$1K | Mes 4 |
| Registro de desenho industrial (UI) | R$3K | Mes 6 |
| Contratos de PI (funcionarios + freelancers) | R$5K | Mes 1 |
| NDAs e politicas de segredo industrial | R$5K | Mes 1 |
| Assessoria PI especializada | R$10K | Mes 1-12 |
| **Total** | **~R$31K** | |

---

## 18. RISCOS E MITIGACOES

| Risco | Prob. | Impacto | Mitigacao | Ver cenario |
|-------|:-----:|:-------:|-----------|:-----------:|
| XP diz nao | 40% | Alto | Pipeline diversificado (BTG, Inter, C6) | §16.1 |
| Churn alto (>6%) | 25% | Alto | AI anti-churn 3 camadas + gamificacao | §16.2 |
| AI nao performa | 30% | Medio | Human-in-the-loop + conteudo como fallback | §16.3 |
| Instituicao build in-house | 15% | Alto | Custo vs buy (R$3.7M+) + contrato multi-ano | §16.4 |
| ANPD restringe dados de menores | 20% | Medio-Alto | Privacy by Design + federated learning | §16.5 |
| Adocao baixa | 30% | Alto | Free tier agressivo + distribuicao via assessores + AI anti-churn |  |
| Ciclo de vendas longo | 50% | Medio | PoC sem custo + piloto com metricas + ROI calculator |  |
| Dependencia de poucas instituicoes | 30% | Alto | White-label escalavel + pipeline diversificado + nunca >40% receita de 1 parceiro |  |
| Competidor internacional (Greenlight) | 15% | Medio | Localizacao + BNCC + regulacao brasileira como barreira de entrada |  |
| Key person risk | 30% | Medio | Documentacao de processos + AI reduz dependencia de individuos |  |

---

## 19. PROXIMOS PASSOS

### Imediato (Proximo mes)

1. **Finalizar strategy document** — validar com advisors e potenciais parceiros
2. **Pitch deck v2** — 10-12 slides para o novo modelo (component library + AI)
3. **Financial model interativo v2** — atualizado com fee/MAU e cenarios multi-instituicao
4. **Prototipo navegavel** — onboarding completo + 1 licao + 4 potes (para demo)

### Curto prazo (Meses 1-3)

5. **PoC tecnica** — 3-4 componentes funcionais em Storybook (React + React Native)
6. **AI prototype** — motor de recomendacao basico com dados sinteticos
7. **Conteudo MVP** — 20 licoes por faixa (80 total) produzidas com pipeline AI + pedagogo
8. **LGPD compliance** — politica de privacidade + fluxo de consentimento implementado
9. **Primeiro contato institucional** — XP (Produto + Instituto XP) e/ou BTG

### Medio prazo (Meses 3-6)

10. **PoC com primeiro parceiro** — componentes rodando em staging
11. **Piloto restrito** — 500-1.000 familias reais
12. **ISO 27001 kickoff** — inicio do processo de certificacao
13. **Pipeline de vendas** — contato com 2o e 3o parceiros potenciais

---

## FONTES

### Benchmarks B2B2C
- Greenlight for Banks: 150+ parceiros (greenlight.com/banks)
- Greenlight Revenue US$228.5M (2024): sacra.com/c/greenlight/
- Banzai: 750+ bancos parceiros (banzai.org)
- GoHenry/Acorns: subscription model validado

### Mercado Brasileiro
- XP Inc: 4.8M clientes ativos, R$1.2 trilhao AUM
- IBGE 2022: 53.7M menores de 18 anos
- CETIC 2024: 93% dos jovens 9-17 sao usuarios de internet
- BCB: regulacao de contas de menor

### AI em Edtech
- Duolingo AI: personalizacao aumentou retencao em 12%
- Khan Academy Khanmigo: AI tutor com curriculo adaptativo
- Squirrel AI: predicao de aprendizado com 85% de acuracia

### Propriedade Intelectual
- Lei 9.279/96 (LPI) — Art. 10: exclusoes de patenteabilidade (metodos financeiros, educacionais, software)
- Lei 9.609/98 (Lei do Software) — Art. 2: protecao de software como obra literaria (50 anos)
- Lei 9.610/98 (LDA) — Art. 7-8: direito autoral (expressao protegida, ideias nao)
- INPI Consulta Publica 03/2025 — Diretrizes de Exame de Patentes de AI
- Portaria INPI/DIRPA 16/2024 — Diretrizes gerais de exame de patentes

### Legal e Compliance
- LGPD — Lei 13.709/2018, Art. 14 (dados de criancas e adolescentes)
- ECA Digital — Lei 15.211/2025 (em vigor desde 17/03/2026) — planalto.gov.br/ccivil_03/_ato2023-2026/2025/lei/L15211.htm
- ECA — Lei 8.069/1990 (Estatuto da Crianca e do Adolescente)
- Marco Civil da Internet — Lei 12.965/2014
- Enunciado CD/ANPD n. 1/2023 — bases legais para dados de criancas e adolescentes
- ANPD — Orientacoes preliminares para afericao de idade (Marco 2026)
- ANPD — Mapa de temas prioritarios 2026-2027 (protecao digital de menores)
- ANPD — Cronograma ECA Digital: Fase 1 (Mar/2026), Fase 2 (Ago/2026), Fase 3 (Jan/2027)
- Guia Orientativo MPCE 2023 — tratamento de dados de criancas e adolescentes
- ISO 27001:2022 — Sistema de gestao de seguranca da informacao
- ISO 27701:2019 — Extensao de privacidade (alinhamento LGPD)
- ISO 27018 — Protecao de PII em servicos de cloud

# Modelo Financeiro Conservador - Fintech Educacao Financeira Familiar Brasil

> **Documento**: Modelo Financeiro Completo (Cenario Conservador) | Versao 1.0 | Janeiro 2026
>
> **Projeto**: Mesada Digital + Cartao Debito para Menores (6-17 anos)
> **Horizonte**: 5 Anos (2026-2030)
> **Cenario**: Conservador
> **Meta SOM Ano 5**: 300.000 familias ativas

---

## Resumo Executivo

### Highlights Financeiros (Cenario Conservador)

| Metrica | Ano 1 | Ano 2 | Ano 3 | Ano 4 | Ano 5 |
|---------|-------|-------|-------|-------|-------|
| Familias Ativas | 15.000 | 45.000 | 100.000 | 180.000 | 300.000 |
| ARR | R$ 4,1M | R$ 12,2M | R$ 27,0M | R$ 48,7M | R$ 81,1M |
| Receita Total | R$ 4,1M | R$ 12,2M | R$ 27,0M | R$ 48,7M | R$ 81,1M |
| EBITDA | -R$ 1,7M | R$ 0,4M | R$ 7,5M | R$ 19,6M | R$ 39,7M |
| Margem EBITDA | -42% | 4% | 28% | 40% | 49% |

### Necessidade de Capital Total

| Rodada | Timing | Valor | Objetivo |
|--------|--------|-------|----------|
| Pre-Seed | M0 | R$ 1,5M | MVP e primeiros 5K usuarios |
| Seed | M12 | R$ 4,0M | Escala para 50K usuarios |
| Serie A | M30 | R$ 15,0M | Expansao e 200K usuarios |
| **Total** | - | **R$ 20,5M** | - |

### Tese de Investimento

1. **Mercado Grande:** 15M+ familias classe AB no Brasil
2. **Unit Economics Solidos:** LTV/CAC > 3x desde Ano 2
3. **Escalabilidade:** Margem bruta de 85% permite escala eficiente
4. **Break-Even Rapido:** 18 meses com gestao disciplinada
5. **Multiplas Receitas:** Subscriptions + Interchange + Float
6. **Defensibilidade:** Dados familiares + habitos financeiros

---

## 1. Premissas Fundamentais

### 1.1 Estrutura de Pricing

| Plano | Preco Mensal | Features | Mix Esperado |
|-------|--------------|----------|--------------|
| **Gratuito** | R$ 0 | Cartao virtual basico, funcoes limitadas | 50% |
| **Familia** | R$ 29,00 | Cartao fisico, mesada automatica, metas, relatorios | 35% |
| **Familia+** | R$ 49,00 | + Investimentos, cashback, multi-filhos, conteudo premium | 15% |

**ARPU Medio Ponderado (sobre usuarios pagantes):**
```
ARPU = (35% x R$ 29,00) + (15% x R$ 49,00)
ARPU = R$ 10,15 + R$ 7,35
ARPU = R$ 17,50/mes (sobre pagantes)
```

**Nota:** 50% da base e composta por usuarios gratuitos, servindo como funil de conversao. O ARPU considera apenas os 50% pagantes, resultando em um ticket medio conservador frente ao mercado.

### 1.2 Evolucao do ARPU por Ano

| Ano | ARPU Mensal | Justificativa |
|-----|-------------|---------------|
| Ano 1 | R$ 17,50 | Base inicial com mix estavel |
| Ano 2 | R$ 17,50 | Manutencao do pricing, foco em volume |
| Ano 3 | R$ 17,50 | Sem reajuste, priorizando retencao |
| Ano 4 | R$ 17,50 | Estabilidade no pricing |
| Ano 5 | R$ 17,50 | Conservadoramente sem aumentos |

**Premissa conservadora:** Nao consideramos reajustes de preco ou migracao de planos ao longo dos 5 anos, diferente de cenarios mais otimistas onde upsell e reajuste inflacionario aumentariam o ARPU progressivamente.

### 1.3 Premissas de Retencao

| Ano | Churn Mensal | Churn Anual | Lifetime (meses) |
|-----|--------------|-------------|------------------|
| Ano 1 | 0,58% | 7,0% | 172 |
| Ano 2 | 0,50% | 6,0% | 200 |
| Ano 3 | 0,42% | 5,0% | 238 |
| Ano 4 | 0,33% | 4,0% | 303 |
| Ano 5 | 0,29% | 3,5% | 345 |

**Nota sobre churn:** As taxas de churn anual sao conservadoras para o segmento de fintechs familiares. O Greenlight (EUA) reporta churn anual de ~3-4% em maturidade. Nossas premissas partem de 7% no Ano 1, refletindo fase de aprendizado do produto.

### 1.4 Premissas de Interchange

| Metrica | Valor |
|---------|-------|
| Filhos por familia | 1,8 |
| Transacoes/mes/crianca | 8 |
| Ticket medio por transacao | R$ 25 |
| Volume transacao mensal/crianca | R$ 200 |
| Volume transacao mensal/familia | R$ 360 |
| Taxa interchange bruta | 1,50% |
| Revenue share (fintech recebe) | 60% |
| **Interchange liquido** | **0,90%** |
| **Receita interchange/familia/mes** | **R$ 3,24** |

### 1.5 Premissas de Float (Saldo em Conta)

| Parametro | Valor |
|-----------|-------|
| Saldo medio por crianca | R$ 150 |
| Rendimento CDI | 10% a.a. |
| Repasse para fintech | 80% |
| **Rendimento efetivo** | **8% a.a.** |
| **Float/crianca/mes** | **R$ 1,00** |

---

## 2. Projecao de Usuarios (5 Anos)

### 2.1 Evolucao da Base

| Metrica | Ano 1 | Ano 2 | Ano 3 | Ano 4 | Ano 5 |
|---------|-------|-------|-------|-------|-------|
| **Familias Inicio Ano** | 0 | 15.000 | 45.000 | 100.000 | 180.000 |
| **Novas Aquisicoes** | 16.050 | 32.700 | 60.000 | 87.200 | 130.500 |
| **Churn (familias)** | -1.050 | -2.700 | -5.000 | -7.200 | -10.500 |
| **Familias Fim Ano** | 15.000 | 45.000 | 100.000 | 180.000 | 300.000 |
| **Crescimento YoY** | - | 200% | 122% | 80% | 67% |

### 2.2 Metricas de Usuarios

| Metrica | Ano 1 | Ano 2 | Ano 3 | Ano 4 | Ano 5 |
|---------|-------|-------|-------|-------|-------|
| Familias Ativas (media) | 7.500 | 30.000 | 72.500 | 140.000 | 240.000 |
| Filhos por familia | 1,8 | 1,8 | 1,8 | 1,8 | 1,8 |
| Total criancas ativas | 27.000 | 81.000 | 180.000 | 324.000 | 540.000 |
| Cartoes emitidos (acum.) | 13.500 | 40.500 | 90.000 | 162.000 | 270.000 |
| DAU/MAU | 45% | 50% | 55% | 58% | 60% |

### 2.3 Funil de Conversao

```
+-----------------------------------------------------------------------+
|                    FUNIL DE USUARIOS - ANO 3                           |
+-----------------------------------------------------------------------+
|                                                                       |
|   Familias Registradas           200.000                              |
|   Familias Ativas                100.000  (50%)                       |
|   Usuarios Gratuitos              50.000  (50% das ativas)            |
|   Usuarios Pagantes               50.000  (50% das ativas)            |
|     - Plano Familia (R$29)        35.000  (35%)                       |
|     - Plano Familia+ (R$49)       15.000  (15%)                       |
|   Criancas Ativas                180.000  (1,8x)                      |
|                                                                       |
+-----------------------------------------------------------------------+
```

---

## 3. P&L - Demonstracao de Resultados (5 Anos)

### 3.1 Receitas

| Linha | Ano 1 | Ano 2 | Ano 3 | Ano 4 | Ano 5 |
|-------|-------|-------|-------|-------|-------|
| **Assinaturas** | | | | | |
| Familias ativas (media) | 15.000 | 45.000 | 100.000 | 180.000 | 300.000 |
| Familias pagantes (50%) | 7.500 | 22.500 | 50.000 | 90.000 | 150.000 |
| ARPU mensal | R$ 17,50 | R$ 17,50 | R$ 17,50 | R$ 17,50 | R$ 17,50 |
| **Receita Assinaturas** | R$ 3,15M | R$ 9,45M | R$ 21,00M | R$ 37,80M | R$ 63,00M |
| | | | | | |
| **Interchange** | | | | | |
| Criancas ativas | 27.000 | 81.000 | 180.000 | 324.000 | 540.000 |
| TPV (Total Payment Volume) | R$ 64,8M | R$ 194,4M | R$ 432,0M | R$ 777,6M | R$ 1.296,0M |
| Taxa liquida (0,9%) | R$ 0,58M | R$ 1,75M | R$ 3,89M | R$ 7,00M | R$ 11,66M |
| | | | | | |
| **Float** | | | | | |
| Saldo total em contas | R$ 4,05M | R$ 12,15M | R$ 27,00M | R$ 48,60M | R$ 81,00M |
| Rendimento efetivo (8% a.a.) | R$ 0,32M | R$ 0,97M | R$ 2,16M | R$ 3,89M | R$ 6,48M |
| | | | | | |
| **RECEITA BRUTA** | **R$ 4,06M** | **R$ 12,17M** | **R$ 27,05M** | **R$ 48,69M** | **R$ 81,14M** |

**Mix de Receita:**

| Fonte | Ano 1 | Ano 3 | Ano 5 |
|-------|-------|-------|-------|
| Assinaturas | 78% | 78% | 78% |
| Interchange | 14% | 14% | 14% |
| Float | 8% | 8% | 8% |

### 3.2 ARR - Receita Recorrente Anual

| Componente | Ano 1 | Ano 2 | Ano 3 | Ano 4 | Ano 5 |
|------------|-------|-------|-------|-------|-------|
| MRR Assinaturas (fim ano) | R$ 263K | R$ 788K | R$ 1,75M | R$ 3,15M | R$ 5,25M |
| MRR Interchange (fim ano) | R$ 49K | R$ 146K | R$ 324K | R$ 583K | R$ 972K |
| MRR Float (fim ano) | R$ 27K | R$ 81K | R$ 180K | R$ 324K | R$ 540K |
| **MRR Total** | R$ 338K | R$ 1,01M | R$ 2,25M | R$ 4,06M | R$ 6,76M |
| **ARR (MRR x 12)** | **R$ 4,1M** | **R$ 12,2M** | **R$ 27,0M** | **R$ 48,7M** | **R$ 81,1M** |

### 3.3 Custos e Despesas

| Categoria | Ano 1 | Ano 2 | Ano 3 | Ano 4 | Ano 5 |
|-----------|-------|-------|-------|-------|-------|
| | | | | | |
| **COGS - Custo dos Servicos** | | | | | |
| Custo por usuario/mes (R$ 3,50) | R$ 0,63M | R$ 1,89M | R$ 4,20M | R$ 7,56M | R$ 12,60M |
| *Inclui: BaaS, cartoes, KYC, cloud, suporte basico* | | | | | |
| **Total COGS** | **R$ 0,63M** | **R$ 1,89M** | **R$ 4,20M** | **R$ 7,56M** | **R$ 12,60M** |
| | | | | | |
| **LUCRO BRUTO** | **R$ 3,43M** | **R$ 10,28M** | **R$ 22,85M** | **R$ 41,13M** | **R$ 68,54M** |
| **Margem Bruta** | **84,5%** | **84,5%** | **84,5%** | **84,5%** | **84,5%** |
| | | | | | |
| **OPEX** | | | | | |
| | | | | | |
| **Pessoal** | | | | | |
| Headcount | 20 | 35 | 50 | 65 | 80 |
| Custo medio/pessoa/mes | R$ 12.000 | R$ 12.000 | R$ 12.000 | R$ 12.000 | R$ 12.000 |
| **Total Pessoal** | **R$ 2,88M** | **R$ 5,04M** | **R$ 7,20M** | **R$ 9,36M** | **R$ 11,52M** |
| | | | | | |
| **Marketing (CAC)** | | | | | |
| % da Receita | 30% | 25% | 20% | 17% | 15% |
| **Total Marketing** | **R$ 1,22M** | **R$ 3,04M** | **R$ 5,41M** | **R$ 8,28M** | **R$ 12,17M** |
| | | | | | |
| **Outros OPEX** | | | | | |
| Infraestrutura Tech | R$ 0,40M | R$ 0,70M | R$ 1,20M | R$ 1,80M | R$ 2,50M |
| Juridico/Compliance | R$ 0,30M | R$ 0,45M | R$ 0,60M | R$ 0,80M | R$ 1,00M |
| Escritorio/Admin | R$ 0,20M | R$ 0,35M | R$ 0,50M | R$ 0,70M | R$ 0,90M |
| Outros (contingencia) | R$ 0,15M | R$ 0,25M | R$ 0,40M | R$ 0,60M | R$ 0,80M |
| **Total Outros OPEX** | **R$ 1,05M** | **R$ 1,75M** | **R$ 2,70M** | **R$ 3,90M** | **R$ 5,20M** |
| | | | | | |
| **TOTAL OPEX** | **R$ 5,15M** | **R$ 9,83M** | **R$ 15,31M** | **R$ 21,54M** | **R$ 28,89M** |

### 3.4 EBITDA e Resultado

| Linha | Ano 1 | Ano 2 | Ano 3 | Ano 4 | Ano 5 |
|-------|-------|-------|-------|-------|-------|
| Receita Bruta | R$ 4,06M | R$ 12,17M | R$ 27,05M | R$ 48,69M | R$ 81,14M |
| (-) COGS | R$ 0,63M | R$ 1,89M | R$ 4,20M | R$ 7,56M | R$ 12,60M |
| **Lucro Bruto** | R$ 3,43M | R$ 10,28M | R$ 22,85M | R$ 41,13M | R$ 68,54M |
| (-) OPEX Total | R$ 5,15M | R$ 9,83M | R$ 15,31M | R$ 21,54M | R$ 28,89M |
| **EBITDA** | **-R$ 1,72M** | **R$ 0,45M** | **R$ 7,54M** | **R$ 19,59M** | **R$ 39,65M** |
| **Margem EBITDA** | **-42%** | **4%** | **28%** | **40%** | **49%** |
| | | | | | |
| (-) D&A | R$ 0,10M | R$ 0,20M | R$ 0,40M | R$ 0,60M | R$ 0,80M |
| **EBIT** | -R$ 1,82M | R$ 0,25M | R$ 7,14M | R$ 18,99M | R$ 38,85M |
| | | | | | |
| (+/-) Resultado Financeiro | R$ 0,05M | R$ 0,10M | R$ 0,20M | R$ 0,30M | R$ 0,50M |
| **EBT** | -R$ 1,77M | R$ 0,35M | R$ 7,34M | R$ 19,29M | R$ 39,35M |
| | | | | | |
| (-) IR/CSLL (34%) | R$ 0 | R$ 0,12M | R$ 2,50M | R$ 6,56M | R$ 13,38M |
| **LUCRO LIQUIDO** | **-R$ 1,77M** | **R$ 0,23M** | **R$ 4,84M** | **R$ 12,73M** | **R$ 25,97M** |
| **Margem Liquida** | -44% | 2% | 18% | 26% | 32% |

### 3.5 Evolucao Visual do EBITDA

```
Ano 1: R$ -1,72M  |========== PREJUIZO
Ano 2: R$  0,45M  |= BREAK-EVEN
Ano 3: R$  7,54M  |=============== CRESCIMENTO
Ano 4: R$ 19,59M  |=============================== ESCALA
Ano 5: R$ 39,65M  |============================================== MATURIDADE
```

---

## 4. Unit Economics

### 4.1 CAC - Custo de Aquisicao de Cliente

| Metrica | Ano 1 | Ano 2 | Ano 3 | Ano 4 | Ano 5 |
|---------|-------|-------|-------|-------|-------|
| Investimento Marketing | R$ 1,22M | R$ 3,04M | R$ 5,41M | R$ 8,28M | R$ 12,17M |
| Novas Familias | 16.050 | 32.700 | 60.000 | 87.200 | 130.500 |
| **CAC** | **R$ 76** | **R$ 93** | **R$ 90** | **R$ 95** | **R$ 93** |
| Benchmark Mercado | R$ 120 | R$ 120 | R$ 120 | R$ 120 | R$ 120 |

**Evolucao do CAC:**
- Ano 1: CAC mais baixo por aproveitamento de canais organicos iniciais (early adopters)
- Anos 2-3: Crescimento do CAC com aumento de escala e competicao por atencao
- Anos 4-5: Estabilizacao com maturidade dos canais e programa de referral

### 4.2 LTV - Lifetime Value

| Componente | Ano 1 | Ano 2 | Ano 3 | Ano 4 | Ano 5 |
|------------|-------|-------|-------|-------|-------|
| Receita/Familia/Mes (total) | R$ 22,55 | R$ 22,55 | R$ 22,55 | R$ 22,55 | R$ 22,55 |
| (-) COGS/usuario/mes | R$ 3,50 | R$ 3,50 | R$ 3,50 | R$ 3,50 | R$ 3,50 |
| **Margem Bruta/usuario/mes** | R$ 19,05 | R$ 19,05 | R$ 19,05 | R$ 19,05 | R$ 19,05 |
| Churn Anual | 7,0% | 6,0% | 5,0% | 4,0% | 3,5% |
| Lifetime estimado (meses) | 36 | 36 | 36 | 36 | 36 |
| **LTV (3 anos)** | **R$ 648** | **R$ 702** | **R$ 756** | **R$ 783** | **R$ 799** |

*LTV calculado com horizonte de 3 anos e margem bruta, considerando churn medio do periodo.*

### 4.3 LTV/CAC Ratio

| Metrica | Ano 1 | Ano 2 | Ano 3 | Ano 4 | Ano 5 | Benchmark |
|---------|-------|-------|-------|-------|-------|-----------|
| LTV | R$ 648 | R$ 702 | R$ 756 | R$ 783 | R$ 799 | - |
| CAC | R$ 76 | R$ 93 | R$ 90 | R$ 95 | R$ 93 | < R$ 120 |
| **LTV/CAC** | **8,5x** | **7,5x** | **8,4x** | **8,2x** | **8,6x** | > 3x |

**Interpretacao:**
- Ano 1 (8,5x): Forte desde o inicio por CAC baixo (early adopters)
- Anos 2-3: Leve reducao com crescimento do CAC em escala
- Anos 4-5: Estabilizacao em ~8x, bem acima do benchmark de 3x

### 4.4 Payback Period

| Metrica | Ano 1 | Ano 2 | Ano 3 | Ano 4 | Ano 5 |
|---------|-------|-------|-------|-------|-------|
| CAC | R$ 76 | R$ 93 | R$ 90 | R$ 95 | R$ 93 |
| Margem Bruta/mes | R$ 19,05 | R$ 19,05 | R$ 19,05 | R$ 19,05 | R$ 19,05 |
| **Payback (meses)** | **4,0** | **4,9** | **4,7** | **5,0** | **4,9** |
| Benchmark | < 12 | < 12 | < 12 | < 12 | < 12 |

### 4.5 Metricas Unitarias por Usuario

| Metrica | Ano 1 | Ano 2 | Ano 3 | Ano 4 | Ano 5 |
|---------|-------|-------|-------|-------|-------|
| Receita/Usuario/Ano | R$ 270 | R$ 270 | R$ 270 | R$ 270 | R$ 270 |
| COGS/Usuario/Ano | R$ 42 | R$ 42 | R$ 42 | R$ 42 | R$ 42 |
| OPEX/Usuario/Ano | R$ 343 | R$ 219 | R$ 153 | R$ 120 | R$ 96 |
| EBITDA/Usuario/Ano | R$ -115 | R$ 10 | R$ 75 | R$ 109 | R$ 132 |

### 4.6 Resumo Unit Economics

```
+-----------------------------------------------------------------------+
|                    UNIT ECONOMICS - ANO 5                              |
+-----------------------------------------------------------------------+
|                                                                       |
|   Receita/Familia/Mes        R$ 22,55                                 |
|   (-) COGS                   R$  3,50                                 |
|   (=) Margem Bruta           R$ 19,05  (84,5%)                        |
|                                                                       |
|   Churn Anual                3,5%                                     |
|   LTV (3 anos)               R$ 799                                   |
|                                                                       |
|   CAC                        R$ 93                                    |
|   LTV:CAC                    8,6x                                     |
|   Payback                    4,9 meses                                |
|                                                                       |
|   EBITDA/Usuario/Ano         R$ 132                                   |
|                                                                       |
+-----------------------------------------------------------------------+
```

---

## 5. Custos Operacionais Detalhados

### 5.1 COGS - Custo dos Servicos Prestados

| Componente | Custo/Usuario/Mes | Descricao |
|------------|-------------------|-----------|
| BaaS (Banking as a Service) | R$ 1,50 | Emissao de contas, processamento |
| Cartoes (producao e envio) | R$ 0,80 | Producao, personalizacao, correio |
| KYC/Compliance | R$ 0,30 | Verificacao de identidade |
| Cloud/Infraestrutura | R$ 0,50 | AWS/GCP, CDN, storage |
| Suporte Basico | R$ 0,40 | Atendimento nivel 1 |
| **Total COGS/Usuario/Mes** | **R$ 3,50** | |

| Ano | Familias | COGS Anual | % Receita |
|-----|----------|------------|-----------|
| Ano 1 | 15.000 | R$ 0,63M | 15,5% |
| Ano 2 | 45.000 | R$ 1,89M | 15,5% |
| Ano 3 | 100.000 | R$ 4,20M | 15,5% |
| Ano 4 | 180.000 | R$ 7,56M | 15,5% |
| Ano 5 | 300.000 | R$ 12,60M | 15,5% |

### 5.2 Pessoal por Area

| Area | Ano 1 | Ano 2 | Ano 3 | Ano 4 | Ano 5 |
|------|-------|-------|-------|-------|-------|
| **Headcount** | | | | | |
| Engenharia | 7 | 12 | 18 | 23 | 28 |
| Produto/Design | 3 | 5 | 8 | 10 | 12 |
| Operacoes/Suporte | 4 | 7 | 10 | 13 | 16 |
| Comercial/Marketing | 3 | 5 | 8 | 10 | 12 |
| G&A (Admin/Finance/Legal) | 3 | 6 | 6 | 9 | 12 |
| **Total Headcount** | **20** | **35** | **50** | **65** | **80** |
| | | | | | |
| **Custo Medio/Pessoa** | | | | | |
| Salario medio mensal (com encargos) | R$ 12.000 | R$ 12.000 | R$ 12.000 | R$ 12.000 | R$ 12.000 |
| **Custo total pessoal/ano** | R$ 2,88M | R$ 5,04M | R$ 7,20M | R$ 9,36M | R$ 11,52M |

### 5.3 Marketing por Canal

| Canal | Ano 1 | Ano 2 | Ano 3 | Ano 4 | Ano 5 |
|-------|-------|-------|-------|-------|-------|
| Performance Digital (Meta/Google) | 40% | 38% | 35% | 32% | 30% |
| Influenciadores | 20% | 18% | 16% | 14% | 12% |
| Referral Program | 10% | 15% | 18% | 22% | 25% |
| Conteudo/SEO | 15% | 14% | 14% | 14% | 15% |
| Parcerias Escolas | 5% | 8% | 10% | 12% | 13% |
| Branding/PR | 10% | 7% | 7% | 6% | 5% |
| **Total** | 100% | 100% | 100% | 100% | 100% |

**Evolucao da Estrategia:**
- Anos 1-2: Foco em performance digital e influenciadores para construir base
- Anos 3-4: Crescimento do referral program e parcerias com escolas
- Ano 5: Mix equilibrado com forte presenca organica e referral maduro

### 5.4 Marketing - Investimento por Canal (R$)

| Canal | Ano 1 | Ano 2 | Ano 3 | Ano 4 | Ano 5 |
|-------|-------|-------|-------|-------|-------|
| Performance Digital | R$ 487K | R$ 1,16M | R$ 1,89M | R$ 2,65M | R$ 3,65M |
| Influenciadores | R$ 243K | R$ 548K | R$ 866K | R$ 1,16M | R$ 1,46M |
| Referral Program | R$ 122K | R$ 456K | R$ 974K | R$ 1,82M | R$ 3,04M |
| Conteudo/SEO | R$ 183K | R$ 426K | R$ 757K | R$ 1,16M | R$ 1,83M |
| Parcerias Escolas | R$ 61K | R$ 243K | R$ 541K | R$ 993K | R$ 1,58M |
| Branding/PR | R$ 122K | R$ 213K | R$ 379K | R$ 497K | R$ 609K |
| **Total** | **R$ 1,22M** | **R$ 3,04M** | **R$ 5,41M** | **R$ 8,28M** | **R$ 12,17M** |

---

## 6. Runway e Necessidade de Funding

### 6.1 Fluxo de Caixa Projetado

| Metrica | Ano 1 | Ano 2 | Ano 3 | Ano 4 | Ano 5 |
|---------|-------|-------|-------|-------|-------|
| **Operacional** | | | | | |
| EBITDA | -R$ 1,72M | R$ 0,45M | R$ 7,54M | R$ 19,59M | R$ 39,65M |
| (+/-) Var. Cap. Giro | -R$ 0,30M | -R$ 0,50M | -R$ 0,80M | -R$ 1,00M | -R$ 1,20M |
| **FCO** | -R$ 2,02M | -R$ 0,05M | R$ 6,74M | R$ 18,59M | R$ 38,45M |
| | | | | | |
| **Investimentos** | | | | | |
| CAPEX | -R$ 0,20M | -R$ 0,35M | -R$ 0,50M | -R$ 0,70M | -R$ 1,00M |
| Software/Intangivel | -R$ 0,30M | -R$ 0,50M | -R$ 0,80M | -R$ 1,00M | -R$ 1,20M |
| **FCI** | -R$ 0,50M | -R$ 0,85M | -R$ 1,30M | -R$ 1,70M | -R$ 2,20M |
| | | | | | |
| **Financiamentos** | | | | | |
| Aporte Equity | R$ 5,50M | R$ 15,00M | R$ 0 | R$ 0 | R$ 0 |
| | | | | | |
| **Variacao Caixa** | R$ 2,98M | R$ 14,10M | R$ 5,44M | R$ 16,89M | R$ 36,25M |
| **Caixa Inicial** | R$ 0 | R$ 2,98M | R$ 17,08M | R$ 22,52M | R$ 39,41M |
| **Caixa Final** | R$ 2,98M | R$ 17,08M | R$ 22,52M | R$ 39,41M | R$ 75,66M |

### 6.2 Fluxo de Caixa Trimestral - Ano 1 e 2

| Periodo | EBITDA | Caixa Acumulado |
|---------|--------|-----------------|
| Ano 1 | -R$ 1,72M | -R$ 1,72M |
| Ano 2 Q1 | -R$ 0,30M | -R$ 2,02M |
| Ano 2 Q2 | R$ 0,05M | -R$ 1,97M |
| Ano 2 Q3 | R$ 0,30M | -R$ 1,67M |
| Ano 2 Q4 | R$ 0,40M | -R$ 1,27M |
| Ano 3+ | Positivo | Recuperacao |

### 6.3 Necessidade de Capital por Rodada

| Rodada | Timing | Valor | Objetivo | Diluicao Est. |
|--------|--------|-------|----------|---------------|
| **Pre-Seed** | M0 | R$ 1,5M | MVP, time core (8 pessoas), beta com 2K usuarios | 15-20% |
| **Seed** | M12 | R$ 4,0M | Escala para 50K usuarios, time 35 pessoas | 15-20% |
| **Serie A** | M30 | R$ 15,0M | Expansao nacional, 200K usuarios, time 65+ | 15-20% |
| **Total** | - | **R$ 20,5M** | | |

### 6.4 Uso dos Recursos - Seed (R$ 4,0M)

| Categoria | Valor | % |
|-----------|-------|---|
| Time (18 meses runway) | R$ 2,20M | 55% |
| Marketing/Aquisicao | R$ 1,00M | 25% |
| Infraestrutura/Tech | R$ 0,50M | 13% |
| Legal/Compliance | R$ 0,20M | 5% |
| Buffer/Contingencia | R$ 0,10M | 2% |
| **Total** | **R$ 4,00M** | 100% |

### 6.5 Capital Minimo Necessario

| Componente | Valor |
|------------|-------|
| Queima Operacional (Ano 1-2) | R$ 2.020.000 |
| Capital de Giro | R$ 500.000 |
| Reserva de Contingencia (20%) | R$ 504.000 |
| **Total Minimo** | **R$ 3.024.000** |
| **Recomendado (com buffer)** | **R$ 4.000.000** |

### 6.6 Runway por Fase

| Fase | Burn Mensal | Caixa | Runway |
|------|-------------|-------|--------|
| Pos-Pre-Seed | R$ 143K | R$ 1,5M | 10 meses |
| Pos-Seed | R$ 250K | R$ 4,0M | 16 meses |
| Pos-Serie A | R$ 500K | R$ 15,0M | 30 meses |
| Breakeven+ | Cash positive | - | Indefinido |

---

## 7. Break-even Analysis

### 7.1 Break-even Operacional

| Metrica | Calculo |
|---------|---------|
| Custos Fixos Mensais (Ano 2) | R$ 567K |
| Margem Contribuicao/Familia/Mes | R$ 19,05 |
| **Break-even Familias** | **~32.000 familias** |
| **Timing Break-even** | **Mes 18 (Q2 do Ano 2)** |

### 7.2 Calculo Detalhado do Break-even

```
Ponto de Equilibrio = Custos Fixos / (Receita/Usuario - Custo Variavel/Usuario)

Custos Fixos Anuais (Ano 2): ~R$ 6,8M (Equipe + Outros)
Margem de Contribuicao/Usuario: R$ 270 - R$ 42 - R$ 68* = R$ 160
*Marketing por usuario no Ano 2

Break-Even = R$ 6.800.000 / R$ 160 = ~42.500 usuarios
Considerando mix de custos variavel: ~32.000 usuarios
```

### 7.3 Evolucao para Break-even

| Mes | Familias | Receita Mensal | Custos Mensais | Resultado | Acumulado |
|-----|----------|----------------|----------------|-----------|-----------|
| 6 | 7.500 | R$ 169K | R$ 305K | -R$ 136K | -R$ 816K |
| 12 | 15.000 | R$ 338K | R$ 429K | -R$ 91K | -R$ 1,72M |
| **18** | **32.000** | **R$ 722K** | **R$ 722K** | **R$ 0** | -R$ 2,02M |
| 24 | 45.000 | R$ 1,01M | R$ 820K | R$ 194K | -R$ 1,27M |
| 36 | 100.000 | R$ 2,25M | R$ 1,28M | R$ 978K | R$ 7,54M |
| 48 | 180.000 | R$ 4,06M | R$ 1,79M | R$ 2,27M | R$ 27,1M |
| 60 | 300.000 | R$ 6,76M | R$ 2,41M | R$ 4,35M | R$ 66,7M |

### 7.4 Grafico Break-even

```
Resultado Mensal (R$ milhoes)

  5  |                                                    ████
  4  |                                              ██████████
  3  |                                        ██████████████████
  2  |                                  ██████████████████████████
  1  |                            ██████████████████████████████████
  0  |----------------████████████████████████████████████████████  <- Break-even M18
 -1  |████████████████████████████████████████████████████████████
     +------------------------------------------------------------
       M6   M12   M18   M24   M30   M36   M42   M48   M54   M60
```

### 7.5 Cash Position ao Longo do Tempo

```
Caixa (R$ milhoes)

  76 |                                                    ████
  64 |                                              ██████████
  52 |                                        ██████████████████
  40 |                            ████████████████████████████████
  28 |              ██████████████████████████████████████████████
  16 |    ████████████████████████████████████████████████████████
   4 |████████████████████████████████████████████████████████████
     +------------------------------------------------------------
       M6   M12   M18   M24   M30   M36   M42   M48   M54   M60
```

### 7.6 Sensibilidade ao Break-even

| Cenario | Usuarios p/ Break-Even | Tempo |
|---------|------------------------|-------|
| Otimista (+20% conversao) | 27.000 | Mes 15 |
| **Base (conservador)** | **32.000** | **Mes 18** |
| Pessimista (-20% conversao) | 40.000 | Mes 22 |

---

## 8. Cenarios (Pessimista / Conservador / Otimista)

### 8.1 Definicao dos Cenarios

| Variavel | Pessimista | Conservador (Base) | Otimista |
|----------|------------|---------------------|----------|
| Crescimento Usuarios | -30% | 0% | +30% |
| ARPU | -10% | 0% | +10% |
| Churn | +20% | 0% | -20% |
| CAC | +25% | 0% | -15% |
| Custos Pessoal | +10% | 0% | -5% |

### 8.2 Cenario Pessimista

**Premissas:**
- Concorrencia mais acirrada (bancos entram agressivamente)
- Aquisicao mais lenta e cara
- Retencao abaixo do esperado

| Metrica | Ano 1 | Ano 2 | Ano 3 | Ano 4 | Ano 5 |
|---------|-------|-------|-------|-------|-------|
| Familias Ativas | 10.500 | 31.500 | 70.000 | 126.000 | 210.000 |
| ARR | R$ 2,8M | R$ 8,5M | R$ 18,9M | R$ 34,1M | R$ 56,8M |
| Receita Total | R$ 2,8M | R$ 8,5M | R$ 18,9M | R$ 34,1M | R$ 56,8M |
| EBITDA | -R$ 2,8M | -R$ 2,5M | R$ 2,5M | R$ 10,0M | R$ 22,0M |
| Margem EBITDA | -100% | -29% | 13% | 29% | 39% |
| Break-even | Mes 24 | - | - | - | - |
| Funding Adicional | +R$ 3M | - | - | - | - |

### 8.3 Cenario Conservador (Base)

| Metrica | Ano 1 | Ano 2 | Ano 3 | Ano 4 | Ano 5 |
|---------|-------|-------|-------|-------|-------|
| Familias Ativas | 15.000 | 45.000 | 100.000 | 180.000 | 300.000 |
| ARR | R$ 4,1M | R$ 12,2M | R$ 27,0M | R$ 48,7M | R$ 81,1M |
| Receita Total | R$ 4,1M | R$ 12,2M | R$ 27,0M | R$ 48,7M | R$ 81,1M |
| EBITDA | -R$ 1,7M | R$ 0,4M | R$ 7,5M | R$ 19,6M | R$ 39,7M |
| Margem EBITDA | -42% | 4% | 28% | 40% | 49% |
| Break-even | Mes 18 | - | - | - | - |

### 8.4 Cenario Otimista

**Premissas:**
- Produto viral (forte boca-a-boca)
- Parcerias estrategicas com escolas e redes
- Execucao excepcional do time

| Metrica | Ano 1 | Ano 2 | Ano 3 | Ano 4 | Ano 5 |
|---------|-------|-------|-------|-------|-------|
| Familias Ativas | 19.500 | 58.500 | 130.000 | 234.000 | 390.000 |
| ARR | R$ 5,3M | R$ 15,8M | R$ 35,1M | R$ 63,3M | R$ 105,5M |
| Receita Total | R$ 5,3M | R$ 15,8M | R$ 35,1M | R$ 63,3M | R$ 105,5M |
| EBITDA | -R$ 0,8M | R$ 2,5M | R$ 14,0M | R$ 31,0M | R$ 65,0M |
| Margem EBITDA | -15% | 16% | 40% | 49% | 62% |
| Break-even | Mes 14 | - | - | - | - |

### 8.5 Comparativo Visual - ARR Ano 5

```
ARR (R$ milhoes) - Ano 5

Otimista       |██████████████████████████████████████████████████  R$ 105,5M
Conservador    |██████████████████████████████████████              R$ 81,1M
Pessimista     |██████████████████████████                          R$ 56,8M
               +------------------------------------------------------
                 0     20     40     60     80     100    120
```

### 8.6 Comparativo Visual - EBITDA Ano 5

```
EBITDA (R$ milhoes) - Ano 5

Otimista       |████████████████████████████████████████████████████  R$ 65,0M
Conservador    |███████████████████████████████                       R$ 39,7M
Pessimista     |█████████████████                                     R$ 22,0M
               +------------------------------------------------------
                 0     10     20     30     40     50     60     70
```

### 8.7 Probabilidade Ponderada

| Cenario | Probabilidade | ARR Ano 5 | EBITDA Ano 5 |
|---------|---------------|-----------|--------------|
| Pessimista | 25% | R$ 56,8M | R$ 22,0M |
| Conservador | 55% | R$ 81,1M | R$ 39,7M |
| Otimista | 20% | R$ 105,5M | R$ 65,0M |
| | | | |
| **Valor Esperado** | 100% | **R$ 79,9M** | **R$ 37,9M** |

---

## 9. Metricas de Eficiencia

### 9.1 Metricas SaaS Chave

| Metrica | Ano 1 | Ano 2 | Ano 3 | Ano 4 | Ano 5 | Benchmark |
|---------|-------|-------|-------|-------|-------|-----------|
| **Crescimento** | | | | | | |
| ARR Growth YoY | - | 200% | 122% | 80% | 67% | > 100% (early) |
| Net Revenue Retention | 93% | 94% | 95% | 96% | 96,5% | > 100% |
| | | | | | | |
| **Eficiencia** | | | | | | |
| CAC Payback (meses) | 4,0 | 4,9 | 4,7 | 5,0 | 4,9 | < 12 |
| LTV/CAC | 8,5x | 7,5x | 8,4x | 8,2x | 8,6x | > 3x |
| | | | | | | |
| **Escala** | | | | | | |
| Receita/Funcionario | R$ 203K | R$ 348K | R$ 541K | R$ 749K | R$ 1,01M | > R$ 300K |
| Usuarios/Funcionario | 750 | 1.286 | 2.000 | 2.769 | 3.750 | - |
| | | | | | | |
| **Rentabilidade** | | | | | | |
| Margem Bruta | 84,5% | 84,5% | 84,5% | 84,5% | 84,5% | > 70% |
| Margem EBITDA | -42% | 4% | 28% | 40% | 49% | > 20% (mature) |
| Rule of 40* | 158% | 204% | 150% | 120% | 116% | > 40% |

*Rule of 40 = Crescimento % + Margem EBITDA %*

### 9.2 Metricas de Engajamento

| KPI | Ano 1 | Ano 2 | Ano 3 | Ano 4 | Ano 5 |
|-----|-------|-------|-------|-------|-------|
| DAU/MAU | 45% | 50% | 55% | 58% | 60% |
| Transacoes/Crianca/Mes | 8 | 8 | 9 | 9 | 10 |
| NPS | 45 | 50 | 55 | 60 | 65 |
| Churn Mensal | 0,58% | 0,50% | 0,42% | 0,33% | 0,29% |

### 9.3 Comparativo com Greenlight (EUA)

| Metrica | Greenlight Ano 3 | Nossa Projecao Ano 3 (Conserv.) |
|---------|------------------|--------------------------------|
| Usuarios | ~500K | 100K |
| ARR | ~$30M | R$ 27M (~$5,4M) |
| Funding Acumulado | ~$80M | R$ 20,5M (~$4,1M) |
| Headcount | ~150 | 50 |
| Margem Bruta | ~75% | 84,5% |

**Nota:** Operacao significativamente mais enxuta que a Greenlight, com 5x menos capital necessario, refletindo a premissa conservadora de crescimento gradual e organico.

---

## 10. Analise de Sensibilidade

### 10.1 Sensibilidade ao Churn (Impacto no LTV)

| Churn Anual | Churn Mensal | LTV (3 anos) | vs Base |
|-------------|--------------|--------------|---------|
| 3,0% | 0,25% | R$ 822 | +9% |
| 3,5% | 0,29% | R$ 799 | +6% |
| **5,0% (Base Ano 3)** | **0,42%** | **R$ 756** | **-** |
| 6,0% | 0,50% | R$ 702 | -7% |
| 7,0% | 0,58% | R$ 648 | -14% |
| 8,0% | 0,67% | R$ 594 | -21% |

### 10.2 Sensibilidade ao ARPU (Impacto no ARR Ano 5)

| ARPU Mensal | ARR Ano 5 | vs Base |
|-------------|-----------|---------|
| R$ 21,00 | R$ 97,4M | +20% |
| R$ 19,25 | R$ 89,2M | +10% |
| **R$ 17,50 (Base)** | **R$ 81,1M** | **-** |
| R$ 15,75 | R$ 73,0M | -10% |
| R$ 14,00 | R$ 64,9M | -20% |

### 10.3 Impacto de Variacoes nas Premissas (EBITDA Ano 3)

| Variavel | -20% | Base | +20% | Impacto EBITDA Ano 3 |
|----------|------|------|------|---------------------|
| Usuarios | 80K | 100K | 120K | +/- R$ 3,0M |
| Conversao Paga | 40% | 50% | 60% | +/- R$ 2,5M |
| ARPU | R$ 14 | R$ 17,50 | R$ 21 | +/- R$ 4,2M |
| Churn | 6% | 5% | 4% | +/- R$ 1,2M |
| CAC | R$ 195 | R$ 162 | R$ 130 | +/- R$ 1,1M |

### 10.4 Matriz de Sensibilidade (Usuarios x ARPU)

**ARR Ano 5 (R$ milhoes):**

| Usuarios \ ARPU | R$ 14 | R$ 15,75 | R$ 17,50 | R$ 19,25 | R$ 21 |
|-----------------|-------|----------|----------|----------|-------|
| 210K | 35,3 | 39,7 | 44,1 | 48,5 | 52,9 |
| 255K | 42,8 | 48,2 | 53,6 | 58,9 | 64,3 |
| **300K** | 50,4 | 56,7 | **81,1** | 69,3 | 75,6 |
| 345K | 58,0 | 65,2 | 72,4 | 79,7 | 86,9 |
| 390K | 65,5 | 73,7 | 81,9 | 90,1 | 98,3 |

### 10.5 Tornado Chart - EBITDA Ano 5

```
Impacto no EBITDA Ano 5 (+/- 20% em cada variavel)

ARPU            |████████████████████████████████████████| +/- R$ 9,5M
Usuarios        |██████████████████████████████████      | +/- R$ 8,0M
Marketing       |██████████████████████████████          | +/- R$ 6,5M
Churn           |████████████████████████                | +/- R$ 5,0M
Custo Pessoal   |██████████████████                      | +/- R$ 3,5M
COGS            |████████████████                        | +/- R$ 2,5M
                +----------------------------------------+
                -10M   -8M   -6M   -4M   -2M   0   +2M   +4M   +6M   +8M   +10M
```

---

## 11. Riscos e Mitigacoes

### 11.1 Matriz de Riscos

| Risco | Prob. | Impacto | Score | Mitigacao |
|-------|-------|---------|-------|-----------|
| Regulatorio Bacen | Media | Critico | 15 | Parceria com IFs licenciadas, compliance desde MVP |
| Entrada grandes bancos | Alta | Alto | 16 | Diferenciacao por experiencia educacional, UX superior |
| Churn acima esperado | Media | Alto | 12 | Produto sticky, gamificacao, conteudo educacional |
| CAC insustentavel | Media | Alto | 12 | Growth organico, referral program, parcerias escolas |
| Falha de execucao time | Media | Alto | 12 | Time enxuto e senior, advisors experientes |
| Fraude/Seguranca | Baixa | Critico | 10 | KYC robusto, monitoramento, antifraude |
| Economia brasileira | Media | Medio | 9 | Foco classes A/B, pricing acessivel |
| Custos BaaS acima | Media | Medio | 9 | Negociar volume, avaliar multi-provider |

### 11.2 Plano de Contingencia

| Trigger | Acao Imediata | Responsavel |
|---------|---------------|-------------|
| Usuarios < 70% da meta por 3 meses | Reduzir headcount 20%, cortar marketing para 15% | CEO/CFO |
| CAC > R$ 150 por 3 meses | Pausar performance, dobrar organico/referral | CMO |
| Churn > 8% anual por 2 trimestres | Task force retencao, entrevistas usuarios | CPO |
| Runway < 9 meses | Cortar 25% custos, estender runway 6 meses | CEO/CFO |
| NPS < 40 | Revisao produto, sprint de qualidade | CPO |
| Conversao gratuito->pago < 15% | A/B testing, onboarding redesign, ajuste pricing | Growth |

### 11.3 Gatilhos para Revisao do Modelo

| Metrica | Alerta Amarelo | Alerta Vermelho | Acao |
|---------|----------------|-----------------|------|
| Crescimento usuarios | < 80% meta | < 60% meta | Revisao de canais |
| Churn anual | > 7% | > 10% | Task force produto |
| CAC | > R$ 120 | > R$ 150 | Corte performance |
| Margem bruta | < 80% | < 75% | Renegociar BaaS |
| Burn rate | > 120% planejado | > 150% planejado | Cortes imediatos |

---

## 12. Valuation e Retorno Investidores

### 12.1 Multiplos de Mercado (Fintechs Similares - Desconto Conservador)

| Empresa | ARR | Multiplo | Valuation |
|---------|-----|----------|-----------|
| Greenlight (2024) | $80M | 28x | $2.3B |
| Step (2023) | $40M | 25x | $1.0B |
| GoHenry (2022) | $35M | 20x | $700M |
| **Media Fintechs Kids** | - | **24x** | - |
| **Desconto Brasil (40%)** | - | **14x** | - |

**Nota:** Aplicamos desconto de 40% nos multiplos internacionais para refletir risco-pais, menor liquidez e estagio mais inicial da operacao brasileira.

### 12.2 Projecao de Valuation

| Momento | ARR | Multiplo | Valuation |
|---------|-----|----------|-----------|
| Pre-Seed (M0) | R$ 0 | - | R$ 5M (pre-revenue) |
| Seed (M12) | R$ 4,1M | 5x | R$ 20M |
| Serie A (M30) | R$ 20M | 5x | R$ 100M |
| Exit potencial (Ano 5) | R$ 81M | 6x | R$ 486M |

### 12.3 Retorno para Investidores (Cenario Exit Ano 5 - R$ 486M)

| Investidor | Investimento | % Pos-Diluicao | Valor Exit | Multiplo | IRR |
|------------|--------------|----------------|------------|----------|-----|
| Fundadores | - | 42% | R$ 204M | - | - |
| Pre-Seed | R$ 1,5M | 8% | R$ 39M | 26x | 92% |
| Seed | R$ 4,0M | 12% | R$ 58M | 14,5x | 72% |
| Serie A | R$ 15,0M | 15% | R$ 73M | 4,9x | 48% |
| ESOP | - | 10% | R$ 49M | - | - |
| Outros | - | 13% | R$ 63M | - | - |
| **Total** | **R$ 20,5M** | 100% | **R$ 486M** | - | - |

**Nota:** Valuation de exit conservador (6x ARR) comparado com multiplos de mercado de 14-28x para fintechs kids. Em cenario de multiplos mais altos, retornos seriam significativamente maiores.

### 12.4 Cenarios de Exit

| Cenario | Multiplo | Valuation | Multiplo Pre-Seed | Multiplo Seed |
|---------|----------|-----------|-------------------|---------------|
| Conservador | 4x ARR | R$ 324M | 17x | 10x |
| Base | 6x ARR | R$ 486M | 26x | 14,5x |
| Otimista | 10x ARR | R$ 811M | 43x | 24x |
| Premium (M&A) | 15x ARR | R$ 1,22B | 65x | 36x |

---

## Anexos

### A. Glossario

| Termo | Definicao |
|-------|-----------|
| ARR | Annual Recurring Revenue = MRR x 12 |
| MRR | Monthly Recurring Revenue |
| ARPU | Average Revenue Per User |
| CAC | Customer Acquisition Cost |
| LTV | Lifetime Value |
| TPV | Total Payment Volume |
| Churn | Taxa de cancelamento (mensal ou anual) |
| Payback | Meses para recuperar CAC |
| NRR | Net Revenue Retention |
| Rule of 40 | Growth Rate + EBITDA Margin |
| DAU/MAU | Daily Active Users / Monthly Active Users |
| NPS | Net Promoter Score |
| BaaS | Banking as a Service |
| KYC | Know Your Customer |
| Float | Rendimento sobre saldos em conta |

### B. Diferencas vs Modelo Base (Otimista)

| Metrica | Modelo Base | Este Modelo (Conservador) | Diferenca |
|---------|-------------|---------------------------|-----------|
| Familias Ano 5 | 1.200.000 | 300.000 | -75% |
| ARR Ano 5 | R$ 363M | R$ 81M | -78% |
| EBITDA Ano 5 | R$ 147M | R$ 40M | -73% |
| Headcount Ano 5 | 380 | 80 | -79% |
| Funding Total | R$ 123M | R$ 20,5M | -83% |
| Break-even | Mes 28 | Mes 18 | -10 meses |
| Plano Gratuito | Nao | Sim (50%) | Funil conversao |
| Reajuste ARPU | Sim (anual) | Nao | Premissa fixa |

### C. Premissas Conservadoras Adotadas

1. **Sem reajuste de precos:** ARPU fixo em R$ 17,50 por 5 anos
2. **50% usuarios gratuitos:** Funil de conversao com metade da base sem pagar
3. **Crescimento moderado:** 300K familias em 5 anos (vs 1,2M no cenario base)
4. **Time enxuto:** Maximo 80 pessoas (vs 380 no cenario base)
5. **Funding reduzido:** R$ 20,5M total (vs R$ 123M no cenario base)
6. **Sem receitas B2B/White-label:** Nao projetadas receitas de parcerias B2B
7. **Sem cashback/parcerias comerciais:** Receita limitada a assinaturas + interchange + float
8. **Revenue share menor:** 60% do interchange (vs 65% no cenario base)

### D. Fontes

1. IBGE 2024 - Dados demograficos familias brasileiras
2. Greenlight Financial Reports 2024 - Benchmark metricas
3. CB Insights Fintech Report 2025 - Multiplos de mercado
4. Pesquisa TIC Domicilios 2024 - Penetracao digital
5. Entrevistas com operadores BaaS Brasil (Dock, Pismo, Zoop)
6. Analise interna de mercado Classe AB Brasil

---

*Documento elaborado para fins de planejamento estrategico e captacao de investimentos.*
*Cenario conservador - projecoes com premissas prudentes para mitigar risco.*
*As projecoes sao estimativas baseadas em premissas que podem variar.*
*Versao 1.0 | Janeiro 2026*

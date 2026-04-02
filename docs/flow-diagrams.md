# GRANIX — Diagramas de Fluxo

> **Versão:** 1.0 | **Data:** Abril 2026
> **Formato:** Mermaid (renderiza no GitHub, Notion, GitBook)

---

## 1. Arquitetura de Sistema — Visão Geral (C4 Nível Sistema)

```mermaid
graph TB
    subgraph FAMILIAS["👨‍👩‍👧 FAMÍLIAS"]
        APP_F["📱 App do Filho\niOS/Android"]
        APP_P["📱 App dos Pais\niOS/Android"]
        ADMIN["🖥️ Admin Dashboard\nWeb (banco parceiro)"]
    end

    subgraph GRANIX["🟢 GRANIX (Middleware)"]
        GW["API Gateway\nRate Limiting · Auth · mTLS"]
        CORE["Core Engine\nVirtual Pots · AI · Gamification"]
        DB[("PostgreSQL\nMulti-tenant RLS")]
        KAFKA["Kafka\nAudit Log Imutável"]
    end

    subgraph BANCO["🏦 BANCO PARCEIRO"]
        CORE_BANK["Core Banking\nPIX · TED · Cartão"]
        KYC["KYC / Compliance\n(responsabilidade do banco)"]
        CONTA["Conta Corrente\ndo Menor (real)"]
    end

    APP_F --> GW
    APP_P --> GW
    ADMIN --> GW
    GW --> CORE
    CORE --> DB
    CORE --> KAFKA
    CORE <-->|"mTLS · REST/Webhook"| CORE_BANK
    CORE_BANK --> KYC
    CORE_BANK --> CONTA

    style GRANIX fill:#e8f5e9,stroke:#388e3c
    style BANCO fill:#e3f2fd,stroke:#1565c0
    style FAMILIAS fill:#fff3e0,stroke:#e65100
```

**Princípio:** GRANIX orquestra comandos ao banco — nunca toca no dinheiro diretamente.

---

## 2. Modelo B2B2C — Fluxo Comercial

```mermaid
graph LR
    BANCO["🏦 Banco Parceiro\n(cliente pagante)"]
    GRANIX["🟢 GRANIX\n(SaaS)"]
    FAMILIA["👨‍👩‍👧 Família\n(usuário final)"]

    BANCO -->|"💰 SaaS fee + revenue share"| GRANIX
    GRANIX -->|"🎮 UI/UX educacional\nGamificação · AI · Potes"| FAMILIA
    BANCO -->|"🏦 Conta · Cartão · PIX · KYC"| FAMILIA
    FAMILIA -->|"📈 Engajamento · Retenção"| BANCO
```

---

## 3. Fluxo de Alocação de Mesada (Saga Pattern)

```mermaid
sequenceDiagram
    actor Pai
    participant GRANIX_API as GRANIX Core
    participant DB as GRANIX DB
    participant BANCO as Banco Parceiro
    actor Filho

    Pai->>GRANIX_API: Confirmar mesada R$100
    GRANIX_API->>BANCO: POST /bank-commands {type: ALLOWANCE_RELEASE, amount: 10000}
    BANCO-->>GRANIX_API: 202 Accepted {command_id: xyz}

    Note over BANCO: Banco executa PIX internamente

    BANCO->>GRANIX_API: Webhook {event: credit_received, amount: 10000}
    GRANIX_API->>GRANIX_API: Calcular split da família

    Note over GRANIX_API,DB: Transação atômica nos 4 potes
    GRANIX_API->>DB: UPDATE virtual_pots
    Note right of DB: Gastar: +R$40\nGuardar: +R$30\nInvestir: +R$20\nDoar: +R$10

    DB-->>GRANIX_API: OK
    GRANIX_API->>Filho: 🔔 Push: "Mesada chegou! R$100"
    GRANIX_API->>Pai: 🔔 Push: "Mesada enviada ✅"

    Note over GRANIX_API: Compensação: se webhook não chegar\nem 30s → polling 5min por 24h
```

---

## 4. Fluxo de Gasto (Compra com Cartão)

```mermaid
sequenceDiagram
    actor Filho
    participant BANCO as Banco Parceiro
    participant GRANIX_API as GRANIX Core
    participant DB as GRANIX DB
    actor Pai

    Filho->>BANCO: Usa cartão débito (R$15)
    BANCO->>BANCO: Autoriza transação\n(sistema próprio do banco)
    BANCO->>GRANIX_API: Webhook {event: debit, amount: 1500, pot: "gastar"}

    GRANIX_API->>DB: Verificar saldo pote "Gastar"

    alt Saldo >= R$15
        DB-->>GRANIX_API: OK (saldo R$40)
        GRANIX_API->>DB: UPDATE virtual_pot Gastar -R$15
        GRANIX_API->>GRANIX_API: Atualizar score AI (padrão de gasto)
        GRANIX_API->>Filho: 🔔 "Você gastou R$15 em Alimentação"
        GRANIX_API->>Pai: 🔔 "Felipe gastou R$15" (se limite atingido)
    else Saldo < R$15 (pote zerado)
        DB-->>GRANIX_API: Saldo insuficiente
        GRANIX_API->>DB: flag pote_negativo
        GRANIX_API->>Pai: 🚨 "Pote Gastar ficou negativo — revisar regras"
        GRANIX_API->>Filho: 📚 Conteúdo educacional sobre planejamento
    end

    Note over GRANIX_API: GRANIX não bloqueia nem autoriza.\nApenas contabiliza e notifica.
```

---

## 5. Fluxo de Onboarding — Família + Banco

```mermaid
flowchart TD
    A[Banco parceiro\noferece GRANIX no app] --> B{Pai já tem\nconta no banco?}

    B -->|Sim| C[SSO: banco autentica pai\nGRANIX recebe token]
    B -->|Não| D[Banco abre conta\nKYC obrigatório]
    D --> C

    C --> E[GRANIX: criar perfil família]
    E --> F[Pai adiciona filho/a\nNome + data nascimento + foto]
    F --> G{Filho < 16 anos?}

    G -->|Sim| H[Consentimento parental\nem destaque — LGPD Art.14\n+ ECA Digital Lei 15.211/2025]
    G -->|Não, 16-17 anos| I[Consentimento simplificado\n+ responsável legal notificado]

    H --> J[Banco: abrir sub-conta\nmenos de 18 anos]
    I --> J

    J --> K[GRANIX: criar potes virtuais\nGastar · Guardar · Investir · Doar]
    K --> L[Pai configura regras\nSplit % + limites por categoria]
    L --> M[✅ Família ativa!\nPrimeira missão educacional desbloqueada]

    style H fill:#fff3e0,stroke:#e65100
    style I fill:#fff3e0,stroke:#e65100
    style M fill:#e8f5e9,stroke:#388e3c
```

---

## 6. Fluxo Multi-tenant — Deploy SDK no Banco

```mermaid
flowchart LR
    subgraph BANCO_APP["App do Banco (React Native)"]
        ROOT["App Root"]
        SDK["@granix/sdk\nGranixProvider"]
        TELAS["Telas GRANIX\n(branding banco)"]
    end

    subgraph GRANIX_INFRA["GRANIX Infra"]
        CONFIG["GET /tenants/bradesco-prod/config\nBranding · Features · Regras"]
        CORE2["Core Engine"]
        DB2[("DB Multi-tenant\nRow-Level Security")]
    end

    ROOT --> SDK
    SDK -->|"tenantId + theme"| TELAS
    SDK -->|"Bootstrap"| CONFIG
    CONFIG --> CORE2
    CORE2 --> DB2

    style BANCO_APP fill:#e3f2fd,stroke:#1565c0
    style GRANIX_INFRA fill:#e8f5e9,stroke:#388e3c
```

---

## 7. Fluxo de Reconciliação Diária (02h BRT)

```mermaid
flowchart TD
    CRON["⏰ Cron Job 02:00 BRT"] --> FETCH["GRANIX → Banco\nGET /accounts/{id}/balance"]
    FETCH --> COMPARE{"Saldo real ==\nΣ potes virtuais?"}

    COMPARE -->|"✅ OK"| LOG["Log reconciliação OK\n+ timestamp"]
    COMPARE -->|"❌ Divergência"| ALERT["🚨 Alerta para time Ops\n+ registro inconsistência"]

    ALERT --> AUDIT["Kafka: event audit_divergence\n{family_id, delta, timestamp}"]
    AUDIT --> REVIEW["Revisão manual em até 24h"]

    LOG --> DONE["✅ Reconciliação concluída"]
    REVIEW --> DONE
```

---

## 8. Modelo de Dados — Potes Virtuais

```mermaid
erDiagram
    TENANT {
        uuid id PK
        string bank_name
        string slug
        jsonb branding_config
        jsonb features_enabled
    }

    FAMILY {
        uuid id PK
        uuid tenant_id FK
        string parent_external_id
        jsonb split_rules
    }

    CHILD {
        uuid id PK
        uuid family_id FK
        string name
        date birth_date
        string bank_external_account_id
        boolean parental_consent_given
        timestamp consent_given_at
    }

    VIRTUAL_POT {
        uuid id PK
        uuid child_id FK
        string pot_type
        bigint balance_cents
        timestamp last_updated
    }

    POT_TRANSACTION {
        uuid id PK
        uuid pot_id FK
        string type
        bigint amount_cents
        string bank_event_id
        timestamp created_at
        jsonb metadata
    }

    TENANT ||--o{ FAMILY : "has"
    FAMILY ||--o{ CHILD : "has"
    CHILD ||--|| VIRTUAL_POT : "Gastar"
    CHILD ||--|| VIRTUAL_POT : "Guardar"
    CHILD ||--|| VIRTUAL_POT : "Investir"
    CHILD ||--|| VIRTUAL_POT : "Doar"
    VIRTUAL_POT ||--o{ POT_TRANSACTION : "records"
```

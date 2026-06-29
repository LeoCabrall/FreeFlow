# Database Model

## Introdução

Este documento descreve a estrutura do banco de dados do FreeFlow.

O modelo foi projetado para suportar:

- Gestão financeira pessoal
- Open Finance
- Inteligência Artificial
- Investimentos
- Metas financeiras
- Cartões
- Patrimônio

---

# USER

| Campo | Tipo |
|--------|------|
| id | UUID |
| name | VARCHAR(150) |
| email | VARCHAR(150) |
| password | VARCHAR(255) |
| phone | VARCHAR(20) |
| photo | VARCHAR(255) |
| plan | VARCHAR(30) |
| created_at | TIMESTAMP |

---

# BANK_ACCOUNT

| Campo | Tipo |
|--------|------|
| id | UUID |
| user_id | UUID |
| bank_name | VARCHAR(100) |
| account_type | VARCHAR(30) |
| agency | VARCHAR(20) |
| account_number | VARCHAR(30) |
| balance | DECIMAL(15,2) |
| currency | VARCHAR(10) |
| open_finance | BOOLEAN |

Relacionamento:

USER (1) -------- (N) BANK_ACCOUNT

---

# CARD

| Campo | Tipo |
|--------|------|
| id | UUID |
| user_id | UUID |
| bank_account_id | UUID |
| name | VARCHAR(100) |
| brand | VARCHAR(30) |
| type | VARCHAR(20) |
| limit_total | DECIMAL(15,2) |
| limit_available | DECIMAL(15,2) |
| closing_day | INTEGER |
| due_day | INTEGER |

Relacionamento:

USER (1) -------- (N) CARD

---

# CATEGORY

| Campo | Tipo |
|--------|------|
| id | UUID |
| user_id | UUID |
| name | VARCHAR(80) |
| type | VARCHAR(20) |
| color | VARCHAR(20) |
| icon | VARCHAR(50) |

---

# TRANSACTION

| Campo | Tipo |
|--------|------|
| id | UUID |
| account_id | UUID |
| category_id | UUID |
| card_id | UUID |
| description | VARCHAR(255) |
| amount | DECIMAL(15,2) |
| transaction_type | VARCHAR(20) |
| transaction_date | DATE |
| notes | TEXT |
| recurring | BOOLEAN |

Relacionamentos:

BANK_ACCOUNT (1) ---- (N) TRANSACTION

CATEGORY (1) ---- (N) TRANSACTION

CARD (1) ---- (N) TRANSACTION

---

# GOAL

| Campo | Tipo |
|--------|------|
| id | UUID |
| user_id | UUID |
| title | VARCHAR(150) |
| target_amount | DECIMAL(15,2) |
| current_amount | DECIMAL(15,2) |
| deadline | DATE |

---

# INVESTMENT

| Campo | Tipo |
|--------|------|
| id | UUID |
| user_id | UUID |
| type | VARCHAR(50) |
| broker | VARCHAR(80) |
| invested_amount | DECIMAL(15,2) |
| current_amount | DECIMAL(15,2) |
| profitability | DECIMAL(8,2) |

---

# NOTIFICATION

| Campo | Tipo |
|--------|------|
| id | UUID |
| user_id | UUID |
| title | VARCHAR(150) |
| message | TEXT |
| read | BOOLEAN |
| created_at | TIMESTAMP |

---

# AI_ANALYSIS

| Campo | Tipo |
|--------|------|
| id | UUID |
| user_id | UUID |
| type | VARCHAR(50) |
| description | TEXT |
| recommendation | TEXT |
| created_at | TIMESTAMP |

---

# OPEN_FINANCE_SYNC

| Campo | Tipo |
|--------|------|
| id | UUID |
| user_id | UUID |
| institution | VARCHAR(100) |
| status | VARCHAR(30) |
| last_sync | TIMESTAMP |

---

# Relacionamentos Gerais

USER
│
├── BANK_ACCOUNT
│      └── TRANSACTION
│
├── CARD
│      └── TRANSACTION
│
├── CATEGORY
│      └── TRANSACTION
│
├── GOAL
│
├── INVESTMENT
│
├── NOTIFICATION
│
├── AI_ANALYSIS
│
└── OPEN_FINANCE_SYNC

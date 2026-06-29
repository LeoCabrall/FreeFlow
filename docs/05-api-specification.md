# API Specification

## Introdução

Este documento descreve todos os endpoints REST do FreeFlow.

Base URL

/api/v1

---

# Authentication

POST /auth/register

Cadastrar usuário.

POST /auth/login

Realizar login.

POST /auth/refresh

Renovar Token JWT.

POST /auth/logout

Encerrar sessão.

---

# Users

GET /users/me

Retorna usuário logado.

PUT /users/me

Atualiza usuário.

DELETE /users/me

Excluir conta.

---

# Bank Accounts

GET /accounts

Lista contas.

POST /accounts

Cadastrar conta.

GET /accounts/{id}

Detalhes.

PUT /accounts/{id}

Atualizar.

DELETE /accounts/{id}

Excluir.

---

# Transactions

GET /transactions

Listar.

POST /transactions

Cadastrar.

GET /transactions/{id}

Detalhes.

PUT /transactions/{id}

Editar.

DELETE /transactions/{id}

Excluir.

---

# Categories

GET /categories

POST /categories

PUT /categories/{id}

DELETE /categories/{id}

---

# Goals

GET /goals

POST /goals

PUT /goals/{id}

DELETE /goals/{id}

---

# Investments

GET /investments

POST /investments

PUT /investments/{id}

DELETE /investments/{id}

---

# Cards

GET /cards

POST /cards

PUT /cards/{id}

DELETE /cards/{id}

---

# Dashboard

GET /dashboard

Retorna:

• saldo

• patrimônio

• receitas

• despesas

• investimentos

• metas

• gráficos

---

# Open Finance

POST /open-finance/connect

GET /open-finance/status

POST /open-finance/sync

DELETE /open-finance/disconnect

---

# Artificial Intelligence

POST /ai/chat

Perguntas ao assistente financeiro.

GET /ai/insights

Recebe análises.

GET /ai/recommendations

Sugestões automáticas.

POST /ai/analyze

Executa análise financeira.

---

# Notifications

GET /notifications

PUT /notifications/read

DELETE /notifications/{id}

# Domain Model

## Introdução

Este documento descreve todas as entidades que compõem o domínio do FreeFlow.

Cada entidade representa um objeto importante do sistema e servirá de base para:

- Banco de Dados
- API REST
- Backend
- Frontend
- Inteligência Artificial
- Open Finance

---

# Entidades Principais

## Usuário (User)

Representa o proprietário da conta.

Atributos:

- id
- nome
- e-mail
- senha
- telefone
- foto
- dataCadastro
- plano

Relacionamentos:

- possui Contas Bancárias
- possui Cartões
- possui Metas
- possui Investimentos
- possui Transações
- possui Notificações

---

## Conta Bancária (Bank Account)

Representa uma conta financeira do usuário.

Atributos:

- id
- banco
- agência
- conta
- tipo
- saldoAtual
- saldoInicial
- moeda
- sincronizadaOpenFinance

Relacionamentos:

- pertence a Usuário
- possui Transações

---

## Cartão

Representa cartão de crédito ou débito.

Atributos:

- id
- banco
- bandeira
- limite
- limiteDisponível
- vencimento
- fechamento

Relacionamentos:

- pertence ao Usuário
- possui Parcelas

---

## Transação

Representa qualquer movimentação financeira.

Atributos:

- id
- descrição
- valor
- tipo
- categoria
- data
- observação

Tipos:

- Receita
- Despesa
- Transferência

Relacionamentos:

- pertence a Conta
- pertence ao Usuário
- pertence a Categoria

---

## Categoria

Classifica receitas e despesas.

Exemplos:

- Alimentação
- Transporte
- Moradia
- Educação
- Saúde
- Lazer
- Investimentos

---

## Meta Financeira

Objetivo financeiro.

Atributos:

- nome
- valorObjetivo
- valorAtual
- prazo

---

## Investimento

Representa ativos financeiros.

Tipos:

- Tesouro Direto
- CDB
- LCI
- LCA
- Fundos
- Ações
- ETFs
- Criptoativos

---

## Patrimônio

Calculado automaticamente.

Fórmula

Patrimônio =
Ativos - Passivos

---

## Open Finance

Responsável pela sincronização automática das contas.

Funções:

- importar contas
- importar cartões
- importar saldo
- importar transações

---

## Inteligência Artificial

Responsável pelas análises.

Funções:

- identificar desperdícios
- prever gastos
- sugerir economia
- recomendar investimentos
- responder perguntas

---

# Relacionamentos

Usuário
│
├── Contas Bancárias
│
├── Cartões
│
├── Transações
│
├── Metas
│
├── Investimentos
│
└── Notificações

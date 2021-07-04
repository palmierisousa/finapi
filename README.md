# FinAPI - Financeira
A simple node.js API to control personal financial operations. It´s possible to create and delete an account, create withdrawals, create deposities and get statements.

The app was build with Node.js and Express and stores all the information in memory.

## Running
- Install all the dependencies: `yarn`
- Run in dev mode: `yarn dev`

## Routes

### Create account
HTTP Method: `post`

Route: `/account`

Request body:
```json
{
  "cpf": "11111111111",
  "name": "Marcelo"
}
```

Return: No return

---

### List account statement
HTTP Method: `get`

Route: `/statement`

Header: `cpf = 11111111111`

Return:
```json
[
  {
    "description": "Depósito do Ignite",
    "amount": 1500,
    "created_at": "2021-07-04T19:02:08.063Z",
    "type": "credit"
  }
]
```

---

### Create a deposity
HTTP Method: `post`

Route: `/deposity`

Header: `cpf = 11111111111`

Request body:
```json
{
	"description": "Depósito do Ignite",
	"amount": 1500.00
}
```

Return: No return

---

### Create a withdraw
HTTP Method: `post`

Route: `/withdraw`

Header: `cpf = 11111111111`

Request body:
```json
{
	"amount": 100
}
```

Return: No return

---

### List statements by date
HTTP Method: `get`

Route: `/statement/date`

Header: `cpf = 11111111111`

Return:
```json
[
  {
    "description": "Depósito do Ignite",
    "amount": 1500,
    "created_at": "2021-07-04T19:02:08.063Z",
    "type": "credit"
  },
  {
    "description": "Withdraw",
    "amount": 100,
    "created_at": "2021-07-04T19:05:045.063Z",
    "type": "debit"
  }
]
```

---

### Update account
HTTP Method: `put`

Route: `/account`

Header: `cpf = 11111111111`

Requet body:
```json
{
	"name": "Marcelo Palmieri"
}
```

Return: no return

---

### Get account
HTTP Method: `get`

Route: `/account`

Header: `cpf = 11111111111`

Return:
```json
{
  "cpf": "11111111111",
  "name": "Marcelo",
  "id": "02ce9cbd-c4cb-4ab1-acfa-5c8ca3f091e2",
  "statement": []
}
```

---

### Delete account
HTTP Method: `delete`

Route: `/account`

Header: `cpf = 11111111111`

Return:
Return all other accounts in the memory database.
```json
{
  "cpf": "22222222222",
  "name": "Marcelo",
  "id": "02ce9cbd-c4cb-4ab1-acfa-5c8ca3f091e2",
  "statement": []
}
```

---

### Get balance
HTTP Method: `get`

Route: `/balance`

Header: `cpf = 11111111111`

Return: Return the account balance, like 1400.

---


### Requeriments

- [x] Deve ser possível criar uma conta
- [x] Deve ser possível buscar o extrato bancário do cliente
- [x] Deve ser possível realizar um depósito
- [x] Deve ser possível realizar um saque
- [x] Deve ser possível buscar o extrato bancário do cliente por data
- [x] Deve ser possível atualizar dados da conta do cliente
- [x] Deve ser possível obter dados da conta do cliente
- [x] Deve ser possível deletar uma conta
- [x] Deve ser possível retonar o balance

---

### Business Rules

- [x] Não deve ser possível cadastrar uma conta com CPF já existente
- [x] Não deve ser possível fazer depósito em uma conta não existente
- [x] Não deve ser possível buscar extrato em uma conta não existente
- [x] Não deve ser possível fazer saque em uma conta não existente
- [x] Não deve ser possível fazer saque quando o saldo for insuficiente
- [x] Não deve ser possível excluir uma conta não existente

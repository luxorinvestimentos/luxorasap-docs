# 🔌 Módulo `btgapi`

O módulo **`btgapi`** provê um wrapper autenticado para integração com as APIs do **BTG Pactual**, incluindo funcionalidades para:
- Autenticação JWT
- Solicitação e consulta de relatórios
- Processamento de arquivos retornados
- Envio e acompanhamento de boletas offshore

Este módulo faz parte do [LuxorASAP (PyPI)](../pypi/index.md) e é utilizado principalmente para automação de fluxos de marcação, controle e reporting.

---

## 📌 Autenticação

### `get_access_token`
Obtém um **token JWT** válido (~1h) para autenticação nas APIs do BTG.

```python
from luxorasap.btgapi import get_access_token

token = get_access_token(test_env=True)

```

**Parâmetros:**
- `client_id` (`str`, opcional): ID do cliente. Se `None`, será lido de variável de ambiente.
- `client_secret` (`str`, opcional): Segredo do cliente. Se `None`, será lido de variável de ambiente.
- `test_env` (`bool`): Define se usa ambiente de testes. Default: `True`.
- `timeout` (`int`): Tempo máximo de espera (em segundos). Default: `20`.

**Retorna:** `str` — Token de autenticação.  
**Erros:** `BTGApiError` em caso de falha.

---

## 📑 Relatórios

### `request_portfolio`
Solicita **relatório de carteira** para um fundo.

```python
ticket = request_portfolio(token, "FUND NAME", start_date, end_date)
```

**Parâmetros:**
- `token` (`str`): Token JWT.
- `fund_name` (`str`): Nome do fundo.
- `start_date`, `end_date` (`datetime.date`): Período do relatório.
- `format` (`str`): `"excel"`, `"xml5"` ou `"pdf"`.

**Retorna:** `str` — Ticket da requisição.

---

### `check_report_ticket`
Verifica se um **ticket de relatório** foi processado.

**Retorna:** `bytes` — Conteúdo do arquivo se pronto.  
**Erros:** `BTGApiError` em caso de pendência ou erro.

---

### `await_report_ticket_result`
Aguarda até que o ticket esteja pronto e retorna o conteúdo binário.

```python
zip_bytes = await_report_ticket_result(token, ticket)
```

---

### `process_zip_to_dfs`
Extrai todos os arquivos de um `.zip` e retorna como DataFrames.

```python
dfs = process_zip_to_dfs(zip_bytes)
```

**Retorna:** `dict[str, pd.DataFrame]`.

---

### `request_investors_transactions_report`
Solicita **relatório de movimentações por cotistas (RTA)**.

---

### `request_fundflow_report`
Gera relatório **FundFlow (RTA)** com base em datas e fundo.

```python
ticket = request_fundflow_report(token, start_date, end_date, fund_name="FUND")
```

---

## 📥 Trades Offshore

### `submit_offshore_equity_trades`
Submete uma lista de trades offshore (equities).

```python
ticket = submit_offshore_equity_trades(token, trades=[{...}], test_env=True)
```

---

### `await_transaction_ticket_result`
Consulta e aguarda o resultado de uma **boleta enviada**.

```python
df = await_transaction_ticket_result(token, ticket)
```

**Retorna:** `pd.DataFrame` com colunas como:
- `status`
- `ticket`
- `referencia`
- `mensagens`

---

## ⚠️ Exceções

### `BTGApiError`
Exceção customizada lançada em qualquer falha de:
- Autenticação
- Requisição
- Processamento de ticket ou relatório

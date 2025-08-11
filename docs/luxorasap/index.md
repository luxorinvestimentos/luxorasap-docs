# 🧠 LuxorASAP (PyPI)

**Luxor Automatic System for Assets and Portfolios** é o **toolbox oficial** da Luxor para manipulação de dados de investimento, integração com provedores externos (ex.: BTG Pactual) e gerenciamento de pipelines de dados para análise, marcação e reporting.

Este módulo faz parte do ecossistema **[LuxorASAP](../index.md)**, que centraliza diferentes ferramentas e pipelines utilizados pelo time de gestão e analytics.  
Enquanto o repositório `luxorASAP-onedrive` representa o formato legado, e o `Luxor Data Pipelines` concentra os processos de ETL, o **LuxorASAP (PyPI)** é o **formato moderno e versionado via Git** — recomendado para novas implementações.

---

## 📌 Principais Funcionalidades

- ✅ Consulta de tabelas financeiras em **Parquet** no ADLS  
- ✅ Wrapper para utilização da **API do BTG Pactual**
- ✅ Gravação incremental e consistente no **Azure Blob Storage**  
- ✅ Utilitários para **DataFrames** e manipulação de **schemas**  

---

## 📦 Estrutura de Módulos

- [`btgapi`](luxorasap/btgapi.md) → Wrapper para utilização da API do BTG  
- [`datareader`](luxorasap/datareader.md) → Consulta a dados de mercado e fundos  
- [`ingest`](luxorasap/ingest.md) → Salvamento e atualização de tabelas no ADLS  
- [`utils`](luxorasap/utils.md) → Leitura de arquivos binários e acesso ao Blob  

---

## 🔑 Autenticação e Ambiente

O uso de funcionalidades que acessam dados sensíveis exige credenciais configuradas.  
As integrações com **Azure Blob Storage** e **BTG API** requerem:

### ✅ Variáveis de ambiente (recomendado)

Crie um arquivo `.env` na raiz do projeto:

```bash
# Azure Blob Storage
AZURE_STORAGE_CONNECTION_STRING="DefaultEndpointsProtocol=...;AccountName=..."

# BTG API
BTG_CLIENT_ID="seu_client_id"
BTG_CLIENT_SECRET="seu_client_secret"
```

### 🧪 Alternativa

Passe os parâmetros diretamente nas funções:

```python
get_access_token(client_id="...", client_secret="...", test_env=False)
```

---

## 🛠️ Exemplo de Uso

```python
from luxorasap.datareader import LuxorQuery
from luxorasap.ingest import save_table
from luxorasap.btgapi import get_access_token, request_portfolio

lq = LuxorQuery()
df = lq.get_table("trades")
save_table("trades_backup", df)

token = get_access_token()
ticket = request_portfolio(token, "FUNDO XPTO", start_date, end_date)
```

---

## 📄 Licença

Este módulo é **de uso interno** da Luxor Investimentos e está disponível para a equipe via instalação pelo [PyPI](https://pypi.org/project/luxorasap/).

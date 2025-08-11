# 🚀 Luxor Data Pipelines

O **Luxor Data Pipelines** é o repositório oficial da Luxor Investimentos para **processos de ETL (Extract, Transform, Load)** que alimentam o nosso datalake e sustentam análises, marcação de portfólio e reporting.  
Ele foi concebido para centralizar e padronizar a ingestão de dados de diversas fontes internas e externas, seguindo as boas práticas de arquitetura **Medallion** (*Bronze → Silver → Gold*).

Este repositório é o destino natural para a **migração dos pipelines atualmente no `luxorASAP-onedrive`**, permitindo melhor versionamento, modularização e integração contínua.

---

## 📌 Objetivos

- **Centralizar** todos os pipelines de dados em um ambiente versionado.
- **Padronizar** a ingestão, transformação e carga de dados.
- **Garantir rastreabilidade** e reprodutibilidade nos fluxos de ETL.
- **Facilitar a manutenção** e evolução das rotinas de dados.
- **Integrar** com o ecossistema do **LuxorASAP (PyPI)** para reaproveitar módulos e utilitários.

---

## 🏗 Arquitetura

O **Luxor Data Pipelines** segue o padrão **Medallion Architecture**:

1. **Bronze**  
   - Dados brutos (*raw*) provenientes de fontes externas ou internas.  
   - Armazenamento fiel ao formato original, com mínima transformação.  

2. **Silver**  
   - Dados tratados e normalizados.  
   - Limpeza de inconsistências, aplicação de schemas, padronização de chaves e formatos.  

3. **Gold**  
   - Dados prontos para consumo analítico e dashboards.  
   - Enriquecimento, agregações e junções otimizadas para consultas.

```mermaid
flowchart LR
    A[Bronze: Dados Brutos] --> B[Silver: Dados Tratados]
    B --> C[Gold: Dados Prontos para Análise]
```

---

## 🔌 Fontes de Dados Típicas

- **Planilhas e arquivos** armazenados no OneDrive (dados mestres, input manual)
- **APIs de mercado** (Bloomberg, BTG Pactual)
- **Dados do administrador de fundos**
- **Bases internas** de marcação e precificação

---

## 🛠 Ferramentas e Integrações

- **LuxorASAP (PyPI)** para ingestão e utilitários de DataFrames.
- **Azure Data Lake Storage (ADLS)** para armazenamento em Parquet.
- **Power BI** para consumo das camadas Gold.
- **Automação** via scripts Python e orquestração agendada.

---

## 📂 Organização da Documentação

Esta documentação está dividida em:

1. **Arquitetura** → Visão geral dos pipelines e seus fluxos.
2. **Pipelines** → Detalhes de cada processo ETL (extração, transformação, carga).
3. **How To** → Guias rápidos para manutenção e criação de novos pipelines.
4. **Boas Práticas** → Padrões de nomenclatura, versionamento e tratamento de dados.

---

## 📄 Licença

Este repositório é **de uso interno** da Luxor Investimentos.

# 📊 Visão Geral — Luxor Data Pipelines

O **Luxor Data Pipelines** é a plataforma centralizada da Luxor para **orquestrar e executar processos de ETL** (Extração, Transformação e Carga) relacionados a dados de investimentos.  
Todos os pipelines são executados **no Azure**, utilizando **Azure Functions** como mecanismo de agendamento e disparo, garantindo **escalabilidade, flexibilidade e baixo custo operacional**.

---

## 🎯 Objetivo

O projeto foi criado para:

- Automatizar rotinas de atualização de dados de mercado, fundos e operações.
- Garantir **consistência e reprodutibilidade** no processamento de dados.
- Facilitar a **manutenção** e **evolução** dos pipelines.
- Integrar de forma nativa com **Azure Blob Storage (ADLS)** e outras fontes internas.

---

## 🏗 Estrutura do Projeto

O repositório é organizado em duas áreas principais:

1. **`pipelines/`** → Scripts contendo a lógica de cada processo de ETL, sempre com um método `run()` que pode receber parâmetros de execução.
2. **`run_[NOME_DO_PIPELINE]/`** → Diretórios que representam Azure Functions, responsáveis por orquestrar e agendar a execução dos scripts de `pipelines/`.

> Para detalhes completos da organização interna, consulte a seção [Arquitetura](architecture.md).

---

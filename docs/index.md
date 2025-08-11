# LuxorASAP — Documentação Central

Bem-vindo à documentação unificada do **LuxorASAP**, o ecossistema de ferramentas, scripts e pipelines de dados da Luxor Investimentos.  
Aqui você encontrará, em um único local, toda a informação técnica necessária para entender, manter e evoluir as soluções que suportam nossas rotinas de dados e automações internas.

---

## 📌 Visão Geral

O LuxorASAP nasceu para centralizar e padronizar **processos de ETL, automações e ferramentas de análise** utilizadas em nossas operações.  
Hoje, nossa documentação cobre **três repositórios principais**, com diferentes estágios de maturidade e propósitos complementares:

| Repositório | Status | Descrição |
|-------------|--------|-----------|
| **luxorASAP-onedrive** | **Legado** (em uso, mas em descontinuação) | Conjunto original de scripts do LuxorASAP, armazenados no OneDrive. Contém pipelines, automações e ferramentas operacionais. Embora seja o formato atualmente em produção, está sendo gradualmente migrado para os repositórios mais modernos. |
| **luxorASAP (PyPI)** | **Ativo** (formato moderno) | Toolbox modular, publicada no [PyPI](https://pypi.org/project/luxorasap/), contendo módulos do luxorASAP-onedrive e novas funcionalidades. Segue versionamento via Git e é o padrão para novas implementações e atualizações. |
| **Luxor Data Pipelines** | **Ativo** (foco em ETL) | Repositório dedicado à criação de pipelines de dados, estruturados segundo a arquitetura *Medallion* (Bronze, Silver, Gold). Centraliza processos de ingestão, transformação e carga no datalake, substituindo gradualmente pipelines do luxorASAP-onedrive. |

---

## 🎯 Objetivos da Unificação

A unificação da documentação visa:

- **Centralizar** as informações técnicas dos três repositórios.
- **Facilitar a transição** de processos do formato legado para o moderno.
- **Padronizar** boas práticas de desenvolvimento, versionamento e publicação.
- **Manter a rastreabilidade** entre o código legado e sua nova implementação.

---

## 📂 Estrutura da Documentação

A documentação está dividida em seções que refletem cada repositório e seus propósitos:

1. **[luxorASAP-onedrive](luxorasap_onedrive/)**  
   Scripts legados, fluxos atuais em produção, estrutura de diretórios e orientações para manutenção até a migração completa.

2. **[luxorASAP (PyPI)](luxorasap/)**  
   Guia de instalação, módulos disponíveis, exemplos de uso e padrões de versionamento.

3. **[Luxor Data Pipelines](luxor_data_pipelines/)**  
   Descrição dos pipelines, diagramas de arquitetura, exemplos de ETL e integração com o ADLS.

---

## 🔄 Plano de Migração

A migração segue a lógica:

1. **Mapeamento** dos scripts legados no `luxorASAP-onedrive`.
2. **Refatoração** e integração no `luxorASAP (PyPI)` ou no `Luxor Data Pipelines`, conforme o tipo de funcionalidade.
3. **Descontinuação** dos módulos legados após testes e homologação no ambiente moderno.

---

## 🚀 Começando

- Para novos desenvolvimentos, utilize preferencialmente o **luxorASAP (PyPI)** ou o **Luxor Data Pipelines**.
- Para manutenção de fluxos já em produção, consulte a seção do **luxorASAP-onedrive**.
- Para dúvidas ou contribuições, siga as orientações da seção **Contribuindo**.

---

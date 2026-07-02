# Case Técnico | Engenharia de Dados

## Objetivo

Este projeto apresenta uma solução de Engenharia de Dados desenvolvida no Databricks Community Edition com o objetivo de transformar dados provenientes de diferentes fontes em uma base analítica organizada e preparada para consumo por ferramentas de Business Intelligence.

A proposta contempla as etapas de ingestão, armazenamento em Delta Lake, tratamento dos dados e modelagem analítica utilizando a arquitetura em camadas (Bronze, Silver e Gold).

---

# Arquitetura da Solução

Foi adotada uma arquitetura em camadas (Medallion Architecture), separando claramente as etapas de ingestão, tratamento e disponibilização dos dados.

## Bronze

Responsável por armazenar os dados provenientes das fontes originais em Delta Tables, realizando apenas padronizações técnicas necessárias para o processamento.

## Silver

Responsável pelos tratamentos de qualidade dos dados, padronização de formatos, normalização das informações e preparação das tabelas para consumo analítico.

## Gold

Camada destinada à construção do modelo analítico (tabelas fato e dimensões). A estrutura foi planejada, porém sua implementação não foi concluída dentro do prazo do desafio.

---

# Tecnologias Utilizadas

- Databricks Community Edition
- PySpark
- Spark SQL
- Delta Lake
- Git
- GitHub

---

# Fontes de Dados

Foram utilizadas nove fontes de dados disponibilizadas para o desafio:

| Arquivo | Formato |
|---------|---------|
| erp_pedidos_cabecalho_2025 | CSV |
| erp_pedidos_itens_2025 | CSV |
| vendedores | CSV |
| cadastro_produtos_api_dump | JSON |
| logistica_entregas | JSON |
| atendimento_ocorrencias | NDJSON |
| legado_regioes_pipe | TXT |
| comercial_canais | XLSX |
| crm_clientes_export | XLSX |

---

> **Observação:** Devido ao prazo do case, parte da implementação foi concluída. A arquitetura proposta, as decisões técnicas e a organização da solução foram documentadas para demonstrar a abordagem adotada e facilitar sua continuidade.

---

# Autor

**Janaina Queiroz**

Engenharia de Dados | Analytics | Business Intelligence

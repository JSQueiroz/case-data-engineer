# Case Técnico | Engenharia de Dados

## Objetivo

Este projeto apresenta uma solução de Engenharia de Dados desenvolvida no Databricks Community Edition com o objetivo de transformar dados provenientes de diferentes fontes em uma base analítica organizada e preparada para consumo por ferramentas de Business Intelligence.

A proposta contempla as etapas de ingestão, armazenamento em Delta Lake, tratamento dos dados e modelagem analítica utilizando a arquitetura em camadas (Bronze, Silver e Gold).

> **Observação:** Devido ao prazo do case, parte da implementação foi concluída. A arquitetura proposta, as decisões técnicas e a organização da solução foram documentadas para demonstrar a abordagem adotada e facilitar sua continuidade.

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

# Organização do Projeto

```
case_data_engineer/

01_ingestao
02_bronze
03_silver
04_gold

sources/
```

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

# Status da Implementação

## Notebook 01 - Ingestão

**Concluído (100%)**

Atividades realizadas:

- Leitura de todas as fontes
- Análise exploratória
- Identificação dos schemas
- Validação dos dados
- Registro de observações sobre qualidade e tratamentos necessários

---

## Notebook 02 - Bronze

**Implementação parcial (3 de 9 bases)**

Tabelas Delta criadas:

- bronze_tb_regioes_pipe
- bronze_tb_erp_pedidoscabecalho2025
- bronze_tb_erp_pedidositens2025

---

## Notebook 03 - Silver

**Implementação parcial (3 de 9 bases)**

Tabelas Delta criadas:

- silver_tb_regioes_pipe
- silver_tb_erp_pedidoscabecalho2025
- silver_tb_erp_pedidositens2025

Nesta etapa foram aplicados tratamentos de qualidade e padronização dos dados para as bases implementadas.

---

## Notebook 04 - Gold

Estrutura criada.

A modelagem analítica foi planejada, porém não implementada dentro do prazo disponível.

---

# Qualidade dos Dados

Durante a análise das fontes foram identificados diferentes tipos de inconsistências, por exemplo:

- padronização de nomes de colunas;
- diferentes formatos de datas;
- padronização de valores categóricos;
- registros incompletos;
- campos nulos;
- necessidade de normalização;
- padronização de tipos de dados.

Os tratamentos foram implementados nas tabelas da camada Silver desenvolvidas durante o case.

---

# Próximos Passos

Caso houvesse maior disponibilidade de tempo, seriam implementadas as seguintes evoluções:

- conclusão da camada Bronze para todas as fontes;
- conclusão da camada Silver para todas as fontes;
- implementação completa da camada Gold;
- construção do modelo dimensional;
- criação das tabelas fato e dimensões;
- validações automatizadas de qualidade dos dados;
- documentação técnica complementar.

---

# Considerações Finais

O desenvolvimento priorizou a organização da solução, definição da arquitetura, análise das fontes e implementação das principais etapas do pipeline de dados.

Mesmo com a implementação parcial, a estrutura proposta permite a continuidade do desenvolvimento seguindo o mesmo padrão adotado durante o projeto.

---

# Autor

**Janaina Queiroz**

Engenharia de Dados | Analytics | Business Intelligence
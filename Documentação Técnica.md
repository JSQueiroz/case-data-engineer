# Documentação Técnica

## 1. Visão Geral da Solução

Este projeto tem como objetivo construir um pipeline de dados utilizando **Databricks**, **PySpark** e **Delta Lake**, seguindo a arquitetura **Medallion (Bronze, Silver e Gold)**.

---

A solução foi estruturada para separar as etapas de ingestão, armazenamento, tratamento e disponibilização dos dados, garantindo organização, rastreabilidade e facilidade de evolução do pipeline.

### Etapas da solução

Fontes de Dados
       │
       ▼
    Bronze
(dados brutos)
       │
       ▼
    Silver
(dados limpos e padronizados)
       │
       ▼
     Gold
(dados analíticos)


- **Ingestão:** leitura dos arquivos disponibilizados, análise exploratória dos dados e identificação de inconsistências.
- **Bronze:** armazenamento dos dados em formato Delta, preservando a estrutura e os valores originais.
- **Silver:** aplicação de regras de qualidade, padronização dos dados e tratamento das inconsistências identificadas.
- **Gold:** organização dos dados para consumo analítico, facilitando consultas e geração de indicadores.

---

## 2. Regras e Premissas Adotadas

Durante o desenvolvimento foram adotadas as seguintes premissas:

- Preservar os dados originais na camada Bronze.
- Separar as etapas de ingestão, tratamento e consumo analítico.
- Padronizar nomes de colunas para facilitar manutenção e consultas.
- Converter os tipos de dados para seus formatos adequados sempre que possível.
- Utilizar o formato Delta como padrão de armazenamento.
- Aplicar transformações apenas após a ingestão dos dados, preservando a rastreabilidade.

---

## 3. Principais Problemas Encontrados nos Dados e Como Foram Tratados

Durante a análise exploratória foram identificados alguns pontos de atenção.

| Problema identificado | Tratamento adotado |
|------------------------|--------------------|
| Nomes de colunas sem padronização | Renomeação utilizando padrão único de nomenclatura |
| Tipos de dados inconsistentes | Conversão para tipos apropriados (string, date, integer, etc.) |
| Datas em formatos diferentes | Padronização para um único formato |
| Valores nulos e "N/A" | Tratamento conforme o contexto de cada coluna |
| Campos estruturados (`Struct`) | Planejamento para achatamento (flatten) na camada Silver |

As transformações foram planejadas para manter a integridade dos dados e preservar sua rastreabilidade.
Os tratamentos foram implementados nas tabelas da camada Silver desenvolvidas durante o case.

---

## 4. Decisões de Modelagem e Justificativas

As principais decisões de modelagem adotadas foram:

### Arquitetura Medallion

A divisão em camadas permite separar responsabilidades entre ingestão, tratamento e consumo analítico, facilitando manutenção e reprocessamento.

### Uso do Delta Lake

O armazenamento em formato Delta oferece benefícios como:

- suporte a transações ACID;
- evolução de schema;
- melhor desempenho nas consultas;
- maior confiabilidade na persistência dos dados.

### Preservação dos dados brutos

Os dados são mantidos sem alterações na camada Bronze, permitindo auditoria e reprocessamento quando necessário.

### Estruturas aninhadas

Os campos do tipo `Struct` foram mantidos durante a ingestão e deverão ser transformados em colunas independentes (flatten) na camada Silver para facilitar consultas analíticas.

---

## 5. Validações Aplicadas

Durante o processo foram realizadas validações para compreender a qualidade dos dados e identificar possíveis inconsistências.

As principais validações incluem:

- verificação do schema dos arquivos;
- análise dos tipos de dados;
- identificação de valores nulos;
- validação dos formatos de datas;
- inspeção de campos estruturados;
- análise exploratória para identificação de inconsistências.

Essas validações serviram como base para definir os tratamentos necessários nas etapas seguintes do pipeline.

---

## 6. Limitações da Solução

Devido ao tempo disponível para desenvolvimento do case, algumas funcionalidades ficaram previstas para evolução futura:

- implementação completa da camada Silver;
- construção da camada Gold;
- automação das validações de qualidade dos dados;
- orquestração do pipeline;
- monitoramento da execução.

A arquitetura proposta, entretanto, permite que essas evoluções sejam incorporadas sem necessidade de mudanças estruturais.

---

## 7. Sugestões de Evolução

Como continuidade do projeto, recomenda-se:

- conclusão da camada Bronze para todas as fontes;
- conclusão da camada Silver para todas as fontes;
- implementação completa da camada Gold;
- validações automatizadas de qualidade dos dados, para garantir que os dados atendem aos requisitos mínimos antes de serem disponibilizados para consumo;
- construção do modelo dimensional;
- criação das tabelas fato e dimensões;
- implementar orquestração utilizando Databricks Workflows;
- documentar regras de negócio e catálogo de dados;


---

## Considerações Finais

O desenvolvimento priorizou a organização da solução, definição da arquitetura, análise das fontes e implementação das principais etapas do pipeline de dados.

Mesmo com a implementação parcial, a estrutura proposta permite a continuidade do desenvolvimento seguindo o mesmo padrão adotado durante o projeto.

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

---

## Notebook 04 - Gold

Estrutura criada.

A modelagem analítica foi planejada, porém não implementada dentro do prazo disponível.


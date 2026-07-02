# Documentação Técnica

## 1. Visão Geral da Solução

Este projeto tem como objetivo construir um pipeline de dados utilizando **Databricks**, **PySpark** e **Delta Lake**. 
Os dados foram organizados em camadas para separar as etapas de ingestão, armazenamento, tratamento e disponibilização dos dados, facilitando a manutenção e futuras evoluções.

---

### Etapas da solução

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
| Valores nulos e "N/A" | Tratamento conforme o contexto de cada coluna e informações da Área de Negócio |
| Campos com estrutura aninhada | Transformar em colunas simples |
| Valores negativos | Tratamento conforme informações da Área de Negócio |
| Valores duplicados | Desconsiderados conforme orientação da Área de Negócio |


As transformações foram planejadas para manter a integridade dos dados e preservar sua rastreabilidade.
Os tratamentos foram implementados nas tabelas da camada Silver desenvolvidas durante o case.

---

## 4. Decisões de Modelagem e Justificativas

As principais decisões de modelagem adotadas foram:

### Arquitetura

A divisão em camadas permite separar responsabilidades entre ingestão, tratamento e consumo analítico, facilitando manutenção e reprocessamento.

### Uso do Delta Lake

O formato Delta foi utilizado por ser o padrão recomendado no Databricks para armazenamento de dados. Além de oferecer maior confiabilidade na gravação das informações, ele facilita futuras evoluções da solução e melhora o desempenho das consultas em comparação com arquivos brutos.

### Preservação dos dados brutos

Os dados são mantidos sem alterações na camada Bronze, permitindo auditoria e reprocessamento quando necessário.

### Estruturas aninhadas

Os campos com essa estrutura foram mantidos durante a ingestão e posteriormente transformados em colunas independentes na camada Silver para facilitar consultas analíticas.

---

## 5. Validações Aplicadas

Durante o processo foram realizadas validações para compreender a qualidade dos dados e identificar possíveis inconsistências.

As principais validações incluem:

- verificação do schema dos arquivos;
- análise dos tipos de dados;
- identificação de valores nulos;
- análise exploratória para identificação de inconsistências.

Essas validações serviram como base para definir os tratamentos necessários.

---

## 6. Limitações da Solução

Durante o desenvolvimento do case foram encontradas algumas limitações que impactaram a implementação completa do pipeline.

- Tempo reduzido para desenvolvimento, o que levou à priorização das etapas de ingestão e estruturação da camada Bronze, para entender
os dados em profundidade, seus formatos, conteúdos e relacionamentos.
- Necessidade de analisar diferentes formatos de arquivos e compreender suas estruturas antes da definição das regras de transformação.
- Presença de dados com formatos distintos (como datas, valores nulos e campos aninhados), exigindo maior esforço na etapa de análise exploratória.
- A camada Silver e a modelagem analítica da camada Gold foram planejadas, mas não puderam ser concluídas dentro do prazo disponível.
  
---

## 7. Sugestões de Evolução

Como continuidade do projeto, recomenda-se:

- conclusão da camada Bronze para todas as fontes;
- conclusão da camada Silver para todas as fontes;
- implementação completa da camada Gold;
- validações automatizadas de qualidade dos dados, para garantir que os dados atendem aos requisitos mínimos antes de serem disponibilizados para consumo;
- construção do modelo dimensional;
- criação das tabelas fato e dimensões;
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


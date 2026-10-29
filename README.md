
# Análise de Atrasos em Entregas | E-Commerce 2026

**Projeto de Análise de Dados** | Python • Pandas • Databricks • SQL • Power BI

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)
![Databricks](https://img.shields.io/badge/Databricks-FF3621?style=flat&logo=databricks&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-003B57?style=flat&logo=DB2&logoColor=white)
![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=flat&logo=powerbi&logoColor=black)
![Git](https://img.shields.io/badge/Git-F05032?style=flat&logo=git&logoColor=white)

---

## Sumário

1. [Contexto e Problema de Negócio](#1-contexto-e-problema-de-negócio)
2. [Perguntas de Negócio](#2-perguntas-de-negócio)
3. [Tecnologias Utilizadas](#3-tecnologias-utilizadas)
4. [Arquitetura e Processamento dos Dados](#4-arquitetura-e-processamento-dos-dados)
5. [Principais Resultados e Insights](#5-principais-resultados-e-insights)
6. [Dashboard Interativo — Power BI](#6-dashboard-interativo--power-bi)
7. [Recomendações de Negócio](#7-recomendações-de-negócio)
8. [Estrutura do Repositório](#8-estrutura-do-repositório)
9. [Como Explorar o Projeto](#9-como-explorar-o-projeto)
10. [Escopo e Limitações](#10-escopo-e-limitações)
11. [Conclusão](#11-conclusão)

---

## 1. Contexto e Problema de Negócio

Uma empresa de e-commerce apresenta um número elevado de entregas fora do prazo e precisa entender quais fatores estão associados a esses atrasos.

Foram analisados **50.000 pedidos**, considerando o tempo de processamento nos armazéns, as transportadoras, a distância percorrida e as condições climáticas.

**Objetivo:** identificar onde os atrasos se concentram e fornecer informações para a empresa avaliar parceiros logísticos, revisar processos e definir prioridades de melhoria.

---

## 2. Perguntas de Negócio

A análise buscou responder às seguintes perguntas:

1. **Dimensão dos atrasos:** Qual é a taxa global de pedidos entregues fora do prazo e qual é a duração média desses atrasos?
2. **Evolução temporal:** Como a taxa de atrasos se comporta ao longo dos meses?
3. **Eficiência operacional:** Existe diferença no tempo médio de processamento entre pedidos entregues no prazo e pedidos atrasados?
4. **Desempenho logístico:** Quais transportadoras e armazéns apresentam maiores taxas de atraso?
5. **Comparação entre parceiros:** As diferenças de desempenho entre transportadoras permanecem quando consideradas faixas semelhantes de distância e prazo prometido?
6. **Distância percorrida:** Como a extensão das rotas se relaciona com a pontualidade?
7. **Condições climáticas:** Quais condições meteorológicas estão associadas às maiores taxas de atraso?

---

## 3. Tecnologias Utilizadas

| Tecnologia | Aplicação no projeto |
| :--- | :--- |
| **Python** | Leitura, inspeção, validação e transformação dos dados |
| **Pandas** | Tratamento de valores ausentes, padronização e verificações de qualidade |
| **Databricks** | Ambiente de processamento, armazenamento e execução dos notebooks |
| **Unity Catalog** | Catalogação e disponibilização da tabela tratada |
| **SQL** | Análises exploratórias, agregações, cálculo de indicadores e comparação de variáveis |
| **Power BI** | Desenvolvimento do dashboard interativo e visualização dos indicadores |
| **Git e GitHub** | Versionamento do código e documentação técnica |

---

## 4. Arquitetura e Processamento dos Dados

Os dados foram organizados em duas camadas, **Raw** e **Silver**, no Databricks. O tratamento foi feito com Python e Pandas.

### 4.1. Camada Raw — Dados Brutos

A Raw guarda o arquivo original, sem alterações.

- **Fonte:** Dataset estático `E-commerce_Delivery_Shipping_Data_2026.csv`.
- **Armazenamento:** Databricks Volume, no diretório `/Volumes/.../raw/`.
- **Finalidade:** Preservar os dados brutos para rastreabilidade e utilização nas etapas posteriores.

### 4.2. Camada Silver — Tratamento e Qualidade dos Dados

Na Silver, os dados passaram por verificações de qualidade, limpeza e padronização com Python e Pandas.

**Verificações de integridade**

- Análise de duplicidades na coluna `order_id`.
- Resultado: 0 identificadores duplicados.
- Confirmação da granularidade de um registro por pedido.

**Padronização temporal**

- Conversão de `order_date` para o tipo `datetime64[ns]`.
- Normalização para granularidade diária utilizando `.dt.floor('d')`.

**Tratamento de valores ausentes**

- Preenchimento de `return_reason` com `'N/A'` nos registros em que `return_requested = 'No'`.

**Validação das regras de negócio**

- Verificação de valores negativos em `delivery_delay_days`: nenhum registro identificado.
- Validação cruzada entre `delivery_delay_days > 0` e `late_delivery = 'Yes'`.
- Resultado: 100% de consistência entre os critérios avaliados.

**Persistência e disponibilização**

Após o tratamento e as verificações de qualidade:

- Os dados tratados foram armazenados em formato CSV no Volume Silver.
- A tabela `workspace.default.entregas_tratadas` foi disponibilizada no Unity Catalog.
- A tabela foi utilizada nas consultas SQL para exploração dos dados, cálculo de indicadores e análises dos fatores associados aos atrasos.

### 4.3. Fluxo de Processamento

```text
Dataset CSV
    |
    v
Raw (dados originais)
    |
    v
Silver (tratamento e validação)
    |
    v
Tabela no Unity Catalog
    |
    v
Análises SQL
    |
    v
Power BI
```

O projeto não contempla a implementação de uma camada Gold. As análises foram realizadas diretamente sobre os dados tratados disponibilizados na Silver.

---

## 5. Principais Resultados e Insights

Os principais números da análise estão resumidos abaixo.

| Categoria | Indicador | Resultado |
| :--- | :--- | :--- |
| Geral | Total de pedidos | 50.000 |
| Geral | Pedidos atrasados | 28.162 |
| Geral | Taxa global de atrasos | 56,32% |
| Geral | Duração média dos atrasos | 2,27 dias |
| Geral | Mediana dos atrasos | 2 dias |
| Geral | Maior atraso registrado | 13 dias |
| Armazém | Processamento médio — pedidos atrasados | 16,59 horas |
| Armazém | Processamento médio — pedidos no prazo | 11,60 horas |
| Transportadoras | GlobalExpress | 65,75% de atraso |
| Transportadoras | SwiftShip | 47,34% de atraso |
| Distância | Rotas inferiores a 499 km | 36,55% de atraso |
| Distância | Rotas de 1.500 km ou mais | 63,89% de atraso |
| Clima | Neve | 93,51% de atraso |
| Clima | Tempestades | 91,00% de atraso |

### 5.1. Panorama Geral das Entregas

Dos **50.000 pedidos analisados**, **28.162 apresentaram atraso**, correspondendo a **56,32% da operação**.

Entre os pedidos atrasados, a duração média foi de **2,27 dias**, com mediana de **2 dias** e máximo registrado de **13 dias**.

Mais da metade dos pedidos chegou depois do prazo previsto.

### 5.2. Tempo de Processamento dos Pedidos

Os pedidos atrasados apresentaram tempo médio de processamento de **16,59 horas**, enquanto os pedidos entregues no prazo registraram **11,60 horas**.

A diferença observada foi de **4,99 horas**.

Os pedidos atrasados levaram, em média, mais tempo para ser processados. Essa diferença merece investigação, mas não é suficiente para afirmar que o processamento causou o atraso.

### 5.3. Desempenho das Transportadoras

Foram identificadas diferenças nas taxas de atraso entre os parceiros logísticos.

- **GlobalExpress:** 65,75% dos pedidos entregues com atraso.
- **SwiftShip:** 47,34% dos pedidos entregues com atraso.
- **Diferença:** 18,41 pontos percentuais.

A diferença entre as transportadoras é relevante, mas a comparação precisa considerar também distância, modalidade de envio e prazo prometido.

### 5.4. Distância Percorrida

A análise por faixas de distância apresentou os seguintes resultados:

- **Rotas inferiores a 499 km:** 36,55% de atraso.
- **Rotas de 1.500 km ou mais:** 63,89% de atraso.

As rotas mais longas apresentaram maior proporção de entregas atrasadas.

Vale verificar se os prazos prometidos para rotas longas estão adequados às condições dessas entregas.

### 5.5. Condições Climáticas

As maiores taxas de atraso identificadas nas condições climáticas analisadas foram:

- **Neve:** 93,51%.
- **Tempestades:** 91,00%.

As maiores taxas apareceram em condições climáticas adversas. O resultado pode orientar análises mais detalhadas por região e tipo de rota.

---

## 6. Dashboard Interativo — Power BI

O dashboard no Power BI reúne os indicadores em duas páginas: uma visão geral e outra dedicada aos fatores operacionais.

### 6.1. Página 1 — Visão Geral

Apresenta os indicadores consolidados da operação.

**Indicadores de desempenho (KPIs)**

- Total de pedidos: 50.000.
- Percentual de atrasos: 56,32%.
- Média de dias de atraso: 2,27.
- Maior atraso registrado: 13 dias.

**Análise temporal**

- Gráfico de linhas apresentando a evolução mensal da taxa de atrasos.

A primeira página mostra o tamanho do problema e sua evolução mensal.

### 6.2. Página 2 — Análise Operacional

A segunda página permite comparar os resultados por transportadora, armazém, clima e tempo de processamento.

**Transportadoras e armazéns**

- Comparação das taxas de atraso por transportadora.
- Análise do desempenho dos centros de distribuição.

**Fatores externos**

- Comparação do percentual de atrasos por condição climática.

**Processamento dos pedidos**

- Comparação do tempo médio de processamento entre pedidos entregues no prazo e pedidos atrasados.

**Filtros interativos**

- Transportadora.
- Modalidade de envio.
- Mês.
- País.

Os filtros permitem consultar os indicadores em diferentes recortes.

**Arquivo:** `powerbi/relatorio_analise_atrasos_2026.pbix`

---

## 7. Recomendações de Negócio

Os resultados apontam quatro frentes que a empresa pode investigar.

### 7.1. Revisão dos Prazos de Entrega para Longas Distâncias

As rotas de 1.500 km ou mais apresentaram taxa de atraso de **63,89%**, superior à observada nas rotas curtas.

**Ação sugerida:** revisar os prazos prometidos para rotas longas, considerando distância, modalidade de transporte e histórico das entregas.

### 7.2. Investigação dos Tempos de Processamento

Os pedidos atrasados apresentaram tempo médio de processamento **4,99 horas superior** ao dos pedidos entregues no prazo.

**Ação sugerida:** examinar as etapas de separação e expedição para entender onde o processamento demora mais.

### 7.3. Avaliação dos Impactos Climáticos

As entregas realizadas sob condições de neve e tempestade apresentaram taxas de atraso superiores a 90%.

**Ação sugerida:** avaliar o uso de informações meteorológicas no planejamento das rotas e dos prazos.

### 7.4. Monitoramento do Desempenho das Transportadoras

A diferença de **18,41 pontos percentuais** entre GlobalExpress e SwiftShip indica variação relevante nas taxas de atraso observadas.

**Ação sugerida:** comparar transportadoras em condições semelhantes antes de considerar mudanças na distribuição de pedidos.

---

## 8. Estrutura do Repositório

```text
analise-entregas-logistica/
├── notebooks/
│   ├── exploracao_dados.ipynb
│   └── analise_sql/
│       ├── atrasos_gerais.ipynb
│       ├── fatores_operacionais.ipynb
│       └── armazens_transportadoras.ipynb
├── powerbi/
│   ├── README.md
│   └── relatorio_analise_atrasos_2026.pbix
└── README.md
```

### Organização dos Arquivos

**`notebooks/exploracao_dados.ipynb`**

Contém as etapas de leitura, inspeção, validação e tratamento dos dados, além da preparação da camada Silver.

**`notebooks/analise_sql/atrasos_gerais.ipynb`**

Reúne consultas relacionadas ao volume de pedidos, indicadores gerais de atraso e evolução temporal.

**`notebooks/analise_sql/fatores_operacionais.ipynb`**

Apresenta análises de tempo de processamento, distância percorrida, condições climáticas e tentativas de entrega.

**`notebooks/analise_sql/armazens_transportadoras.ipynb`**

Contém as consultas utilizadas para investigar o desempenho dos armazéns e das transportadoras.

**`powerbi/`**

Armazena o relatório Power BI e sua documentação específica.

---

## 9. Como Explorar o Projeto

### Análises em Python e SQL

Os notebooks de tratamento e análise estão na pasta `notebooks/`.

A execução integral do processamento depende de um ambiente Databricks configurado e do acesso ao dataset original.

### Dashboard Power BI

O relatório está disponível no arquivo:

`powerbi/relatorio_analise_atrasos_2026.pbix`

Para explorar o dashboard, é necessário utilizar o Power BI Desktop e, quando aplicável, configurar o acesso à fonte de dados.

---

## 10. Escopo e Limitações

### Dataset estático

A análise utiliza uma base histórica estática, sem ingestão contínua ou atualização automática.

Os resultados representam exclusivamente o período e os registros presentes no dataset.

### Arquitetura de dados

O processamento contempla as camadas Raw e Silver. Não foi implementada uma camada Gold.

### Natureza da análise

A análise é exploratória e descritiva. As diferenças observadas não demonstram, por si só, relações de causa e efeito.

### Generalização dos resultados

Os resultados se referem à base utilizada e não devem ser generalizados para outras operações sem novas verificações.

---

## 11. Conclusão

A taxa de atrasos encontrada foi de **56,32%**. Também foram observadas diferenças por transportadora, distância, clima e tempo de processamento.

O projeto reuniu tratamento e validação de dados com Python e Pandas, consultas SQL no Databricks e apresentação dos indicadores no Power BI. As análises ajudam a indicar quais pontos da operação merecem ser investigados primeiro.

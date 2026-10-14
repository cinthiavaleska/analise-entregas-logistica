# Análise de Entregas Logísticas

## Sobre o projeto

Este projeto tem como objetivo analisar dados de entregas de um e-commerce para investigar a ocorrência de atrasos, identificar padrões operacionais e encontrar oportunidades de melhoria no processo logístico.

A análise será desenvolvida no Databricks, utilizando Python e Pandas para explorar, tratar e analisar os dados, com Power BI para a construção de um dashboard interativo.

## Problema de negócio

Atrasos nas entregas podem prejudicar a experiência do cliente e indicar oportunidades de melhoria nas operações logísticas. Por isso, o projeto busca responder às seguintes perguntas:

- Qual é a proporção de pedidos entregues com atraso?
- Como os atrasos se distribuem entre transportadoras e armazéns?
- Existe relação entre as condições climáticas e os atrasos?
- A distância percorrida está associada ao tempo de entrega?
- O número de tentativas de entrega e o tempo de processamento apresentam padrões relacionados aos atrasos?
- Quais fatores operacionais merecem atenção para melhorar o desempenho das entregas?

## Ferramentas utilizadas

- **Databricks:** ambiente de desenvolvimento e análise.
- **Python:** linguagem utilizada no projeto.
- **Pandas:** tratamento, exploração e análise dos dados.
- **SQL:** consultas analíticas no Databricks, quando aplicável.
- **Power BI:** visualização dos indicadores e construção do dashboard.
- **Git e GitHub:** versionamento e documentação do projeto.

## Etapas do projeto

1. **Exploração dos dados:** conhecer as colunas, os tipos de dados e a qualidade da base.
2. **Tratamento dos dados:** verificar inconsistências e preparar os dados para análise.
3. **Análise exploratória:** investigar os atrasos e suas possíveis relações com fatores operacionais.
4. **Indicadores e agregações:** selecionar métricas relevantes para apoiar a análise logística.
5. **Dashboard:** apresentar os principais indicadores e padrões identificados.
6. **Recomendações:** propor ações com base nos resultados encontrados.

## Organização dos dados

O projeto utiliza a abordagem Medallion para organizar os dados em camadas:

- **Raw:** dados originais, preservados sem alterações.
- **Silver:** dados tratados e preparados para análise.
- **Gold:** indicadores e tabelas agregadas que serão definidos conforme as necessidades identificadas durante a análise.

## Fonte dos dados

Dataset: *E-Commerce Delivery and Shipping Data 2026*, disponibilizado no Kaggle.

## Resultados esperados

Identificar padrões associados aos atrasos nas entregas, avaliar diferenças entre grupos operacionais e apresentar oportunidades de melhoria apoiadas pelos dados.

As conclusões e recomendações serão adicionadas após a conclusão das análises.

## Status do projeto

Em desenvolvimento.

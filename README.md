# Análise de Entregas Logísticas

## Sobre o projeto

Projeto de análise de dados de entregas de um e-commerce, desenvolvido para investigar atrasos, identificar padrões operacionais e encontrar oportunidades de melhoria no processo logístico.

A análise utiliza Python, Pandas e SQL no Databricks, com o objetivo de transformar dados operacionais em informações que apoiem a tomada de decisão.

## Problema de negócio

Os atrasos nas entregas podem prejudicar a experiência do cliente e indicar oportunidades de melhoria na operação logística.

O projeto busca responder às seguintes perguntas:

- Qual percentual dos pedidos é entregue com atraso?
- Quantos dias de atraso os pedidos apresentam, em média?
- Como o tempo de processamento, a distância e as condições climáticas se relacionam com os atrasos?
- Existem diferenças no desempenho entre armazéns e transportadoras?
- Quais pontos da operação devem ser priorizados para investigação e melhoria?

## Ferramentas utilizadas

- **Databricks:** ambiente de desenvolvimento e análise.
- **Python e Pandas:** exploração e tratamento dos dados.
- **SQL:** consultas analíticas e cálculo de indicadores.
- **Power BI:** desenvolvimento do dashboard interativo (próxima etapa).
- **Git e GitHub:** versionamento e documentação do projeto.

## Etapas do projeto

1. **Exploração dos dados:** análise das colunas, dos tipos de dados e da qualidade da base.
2. **Tratamento dos dados:** verificação de duplicidades, valores ausentes e consistência dos campos.
3. **Análise exploratória:** investigação dos atrasos e de possíveis relações com fatores operacionais.
4. **Análise SQL:** cálculo de indicadores e comparação entre períodos, distâncias, condições climáticas, armazéns e transportadoras.
5. **Dashboard:** construção de visualizações dos principais indicadores no Power BI.
6. **Recomendações:** identificação de oportunidades de melhoria com base nos resultados.

## Organização dos dados

O projeto utiliza a abordagem Medallion para organizar os dados:

- **Raw:** dados originais.
- **Silver:** dados tratados e preparados para análise.
- **Gold:** camada destinada a indicadores e tabelas agregadas para consumo analítico, a ser definida conforme as necessidades do projeto.

## Principais resultados

A análise de **50.000 pedidos** identificou os seguintes resultados:

- **56,32% dos pedidos** apresentaram atraso, totalizando 28.162 pedidos.
- **2,27 dias** foi o atraso médio entre os pedidos atrasados.
- **13 dias** foi o maior atraso observado.
- Os pedidos atrasados apresentaram tempo médio de processamento de **16,59 horas**, contra 11,60 horas nos pedidos entregues no prazo.
- A taxa de atraso foi de **63,89%** para pedidos com distância de 1.500 km ou mais, contra 36,55% para distâncias de até 499 km.
- A taxa de atraso variou conforme a condição climática, chegando a 93,51% nos pedidos associados a neve e 91,00% nos associados a tempestades.
- Entre as transportadoras analisadas, a GlobalExpress apresentou taxa de atraso de 65,75%, enquanto a SwiftShip apresentou 47,34%.

Os resultados indicam associações entre os atrasos e fatores operacionais. Eles não comprovam, isoladamente, relações de causa e efeito.

## Oportunidades de melhoria

Com base nos resultados, as principais oportunidades de investigação são:

- Avaliar as etapas do processamento dos pedidos para identificar possíveis pontos de espera.
- Investigar diferenças de desempenho entre transportadoras.
- Avaliar o impacto de longas distâncias e condições climáticas adversas no planejamento das entregas.
- Monitorar indicadores por armazém e transportadora para identificar operações que precisam de atenção prioritária.

As recomendações deverão ser acompanhadas por indicadores para avaliar se as ações implementadas contribuem para reduzir os atrasos.

## Fonte dos dados

Dataset: *E-Commerce Delivery and Shipping Data 2026*, disponibilizado no Kaggle.

## Status do projeto

**Em desenvolvimento.** 


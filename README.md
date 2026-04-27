# Give Me Some Credit - Estudo de Risco de Credito

Este repositorio reune um estudo em Python sobre modelagem de risco de credito a partir do dataset **Give Me Some Credit**.  
O foco do projeto e mostrar um fluxo inicial de analise de dados aplicado a credito, com tratamento de faltantes, exploracao dos dados, criacao de variaveis, modelagem logistica e comparacao de estrategias de selecao de variaveis.

## Objetivo

Construir uma primeira abordagem para estimar a probabilidade de inadimplencia (`default_2y`), explorando modelos interpretaveis e comparando diferentes formas de selecionar variaveis.

## Principais etapas do projeto

- leitura e padronizacao dos dados;
- diagnostico de faltantes e inconsistencias;
- tratamento de `age`, `monthly_income` e `dependents`;
- criacao da variavel `late_score` para resumir historico de atrasos;
- analise exploratoria com foco em separacao do target;
- ajuste de modelos de regressao logistica;
- comparacao entre:
  - selecao manual de variaveis;
  - stepwise AIC;
  - regularizacao L1;
- geracao de previsoes para o conjunto de teste.

## Arquivos principais

- `versao1_com_comparacao.ipynb`  
  Analise preditiva com modelo de regressão logistica e comparacao entre estrategias de selecao de variaveis.


## Ferramentas utilizadas

- Python
- pandas
- numpy
- matplotlib
- seaborn
- statsmodels
- scikit-learn

## Resultados

O projeto compara abordagens interpretaveis e automatizadas para modelagem de risco de credito, usando AUC e acuracia como metricas de avaliacao em validacao.  

## Como executar

1. Clone este repositorio.
2. Instale as bibliotecas necessarias em um ambiente Python.
3. Garanta que os arquivos do dataset estejam disponiveis na pasta `GiveMeSomeCredit/`.
4. Abra um dos notebooks no Jupyter Notebook ou JupyterLab.

## Dataset

O estudo foi feito sobre o dataset **Give Me Some Credit**, amplamente usado em problemas de classificacao em credito.

## Motivacao

Este projeto foi desenvolvido como parte do meu estudo para analise de dados com foco em risco de credito e validacao de dados.

## Autor

**Hermes Alves Neto**  
https://www.linkedin.com/in/hermesalvesneto/
https://github.com/hermesalvesneto
hermes.alves.neto@gmail.com


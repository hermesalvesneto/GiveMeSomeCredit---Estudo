# Give Me Some Credit - Estudo de Risco de Credito

Este repositorio apresenta um estudo em Python sobre modelagem de risco de credito a partir do dataset **Give Me Some Credit**.  
O foco do projeto e mostrar um fluxo inicial de analise de dados aplicado a credito, incluindo tratamento de dados, exploracao, engenharia de variaveis, modelagem estatística e comparacao de estrategias de selecao de variaveis.

## Objetivo

Construir um modelo de risco de crédito para estimar a probabilidade de inadimplencia (`default_2y`), explorando modelos interpretaveis e comparando diferentes formas de selecionar variaveis.

O foco é explorar cenários e equilibrar performance preditiva e interpretabilidade.

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

## Modelagem

Foi utilizada regressão logística, amplamente empregada em crédito por sua interpretabilidade e capacidade de estimar probabilidades.

O projeto compara três abordagens de seleção de variáveis:

Manual (EDA): seleção baseada em análise exploratória e entendimento do problema;
Stepwise (AIC): abordagem automatizada baseada em critério de informação;
Regularização L1: seleção automática via penalização.

Essa comparação permite analisar o trade-off entre simplicidade, interpretabilidade e performance.

## Arquivos principais

- `versao1_com_comparacao.ipynb`  
  Analise preditiva com modelo de regressão logistica e comparacao entre estrategias de selecao de variaveis.


## Resultados

O projeto compara abordagens interpretaveis e automatizadas para modelagem de risco de credito, usando AUC e acuracia como metricas de avaliacao em validacao. 

O modelo usando apenas as duas variáveis selecionadas a partir da EDA teve uma boa AUC e acurácia em comparação com os demais métodos de seleção de variáveis. 

Os modelos foram avaliados utilizando AUC (ROC-AUC) e acurácia.

O modelo mais simples, com apenas duas variáveis selecionadas a partir da análise exploratória, apresentou desempenho competitivo em relação aos modelos mais complexos.
Isso indica que variáveis bem escolhidas podem capturar grande parte do risco de crédito, mesmo com menor complexidade.


abordagem	modelo	      n_variaveis	auc_treino	auc_validacao	acuracia_validacao
  L1	  Logistic Regression	 10	          0.790	           0.799	        0.761
 Manual	       GLM Logit	  2	          0.713	           0.717	        0.933
Stepwise AIC   GLM Logit	  8	          0.656	           0.669	        0.933

Observa-se que o modelo com regularização L1 apresentou melhor desempenho em termos de AUC, indicando maior capacidade de discriminar bons e maus pagadores.

Já os modelos mais simples apresentaram alta acurácia, possivelmente influenciada pelo desbalanceamento da base, o que reforça a importância do uso de AUC como métrica principal em problemas de crédito.

Apesar da menor acurácia em relação aos modelos mais simples, o modelo com regularização L1 apresentou maior AUC, indicando melhor capacidade de discriminação entre bons e maus pagadores.

Em problemas de crédito, métricas como AUC são mais adequadas do que acurácia, especialmente em bases desbalanceadas, pois capturam melhor a capacidade do modelo de prever o risco dos clientes.

Dessa forma, o modelo com regularização L1 se mostra mais adequado para construção de um score de crédito.

## Ferramentas utilizadas

- Python
- pandas
- numpy
- matplotlib
- seaborn
- statsmodels
- scikit-learn

## Como executar

1. Clone este repositorio.
2. Instale as bibliotecas necessarias em um ambiente Python.
3. Garanta que os arquivos do dataset estejam disponiveis na pasta `GiveMeSomeCredit/`.
4. Abra um dos notebooks no Jupyter Notebook ou JupyterLab.

## Dataset

O estudo foi feito sobre o dataset **Give Me Some Credit**, amplamente usado em problemas de classificacao em credito.

## Motivacao

Este projeto foi desenvolvido com o objetivo de consolidar conhecimentos em análise de dados aplicada a risco de crédito, com foco na construção de modelos interpretáveis.

## Autor

**Hermes Alves Neto**  
https://www.linkedin.com/in/hermesalvesneto/
https://github.com/hermesalvesneto
hermes.alves.neto@gmail.com


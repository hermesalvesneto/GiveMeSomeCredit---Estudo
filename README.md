# Give Me Some Credit - Estudo de Risco de Credito

Meu objetivo é comparar métodos de regressão logística com diferentes formas de selecionar variáveis. 

Primeiro, faço uma breve análise do conjunto de dados com o tratamento de dados faltantes e um processo de engenharia de features nas variáveis que guardam o números atrasos de pagamento em um determinado prazo fixo. Como essas variáveis de atraso estão altamente correlacionadas, isso pode ser um problema para o modelo. Para evitar isso, agrupamos essas informações em uma única variável chamada `late_score` que faz uma soma ponderada dos atrasos em cada período. Além disso, nessa análise exploratória verificamos que o conjunto de dados disponível para treino é desbalanceado. Apenas cerca de $7\%$ dos dados correspondem a pessoas classificadas como más pagadoras. Se não modelado corretamente, isso pode levar a ajuste que classifica a maioria dos dados como bons pagadores ($y=0$). Para isso vamos procurar nos orientar usando a curva ROC para escolher um limiar que tenha um balanceamento entre **sensibilidade** e **especificidade**.

Feito essa primeira análise exploratória, vamos aos métodos de seleção de variáveis. A primeira forma de selecionar será baseada nos gráficos de boxplot comparando as distribuiçoes de cada variáveis explicativa pelas preditoras. Uma variável que indica uma forte depedência é a variável `late_score`. A variável `credit_utilization` também evidencia uma dependência, mas ao rodar o modelo de regressão logística do pacote `statsmodels` vemos que a partir do teste de hipóteses que a função `sm.GLM` apresenta, temos evidências para não rejeitar a hipótese de que essa variável possui significância estatística para o modelo. Por isso, vamos analisar o desempenho da variável `late_score` sozinha. As outras formas de seleção de variáveis são o AIC, o BIC e a regularização L1 Lasso.

Na avaliação de desempenho dos modelos de regressão logística usando a função logito como função de ligação, podemos observar que quando consideramos um limiar padrão de $0.5$, a sensibilidade dos modelos fica próxima de $0$, o que é muito ruim para avaliar risco de crédito, afinal, não queremos um modelo que tenha uma baixa taxa de acerto nos maus pagadores pois isso implica em conceder crédito a pessoas que não conseguirão pagar. Isso acontece porque os dados estão desbalanceados. Para contornar isso, fiz uma rotina para impõe um limite inferior para a sensibilidade e a partir disso busca por limiares que melhorem a **acurácia** do teste.

Os modelos com limiares otimizados confirmam a suposição de que os melhores limiares estão mais próximos do zero e o resultado foi satisfatório. Surpreendentemente, o modelo que leva em consideração apenas a variável `late_score` apresentou um ótimo resultado.

Para futuras análises, quero fazer análises de resíduos para veficar se o modelo precisa de algum ajuste e gráficos QQ plot para verificar se as suposições sobre o modelo estão corretas. Além disso gostaria de comparar a regressão logística logito com outros modelos.

## Principais etapas do projeto

- leitura e padronizacao dos dados;
- diagnostico de faltantes e inconsistencias;
- tratamento de `age`, `monthly_income` e `dependents`;
- criacao da variavel `late_score` para resumir historico de atrasos;
- analise exploratoria com foco em separacao do target;
- ajuste de modelos de regressao logistica;
- comparacao entre:
  - selecao manual de variaveis;
  - AIC e BIC;
  - regularizacao L1;
- geracao de previsoes para o conjunto de teste.

## Arquivos principais

- `GiveMeSomeCredit-Copy3.ipynb`


## Ferramentas utilizadas

- Python
- pandas
- numpy
- matplotlib
- seaborn
- statsmodels
- scikit-learn

## Dataset

O estudo foi feito sobre o dataset **Give Me Some Credit**, amplamente usado em problemas de classificacao em credito.

## Autor

**Hermes Alves Neto**  
https://www.linkedin.com/in/hermesalvesneto/
https://github.com/hermesalvesneto
hermes.alves.neto@gmail.com


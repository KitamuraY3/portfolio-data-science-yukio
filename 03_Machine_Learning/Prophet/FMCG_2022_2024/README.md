# Previsão de Demanda Diária --- SKU YO-029

Projeto de portfólio em Ciência de Dados para comparar modelos de
previsão de vendas diárias de uma SKU do setor de laticínios, utilizando
dados históricos de 2022 a 2024.

------------------------------------------------------------------------

## Visão geral

O objetivo deste projeto é avaliar e comparar o desempenho dos modelos
**Prophet** e **XGBoost** na previsão das vendas diárias da SKU
**YO-029**, considerando três períodos mensais de teste.

A SKU foi selecionada por apresentar o maior volume total de vendas no
conjunto de dados: **177.798 unidades**. Para a análise, as vendas foram
agregadas por data, somando os valores de `units_sold` entre canais e
regiões.

## Objetivos

-   Analisar o comportamento temporal das vendas diárias.
-   Avaliar a série histórica da SKU selecionada.
-   Treinar um modelo de referência com Prophet.
-   Desenvolver um modelo preditivo com XGBoost.
-   Comparar o desempenho dos modelos em períodos de teste distintos.
-   Interpretar os resultados e suas limitações.

## Dados

-   **Dataset:** FMCG Daily Sales.
-   **Período dos dados originais:** 2022 a 2024.
-   **Registros no arquivo original:** 190.757 linhas e 14 colunas.
-   **SKU analisada:** YO-029.
-   **Volume total vendido pela SKU:** 177.798 unidades.
-   **Período da série diária:** 28/02/2022 a 31/12/2024.
-   **Observações da série diária:** 1.038 datas, sem lacunas.

As vendas foram agregadas diariamente, somando as unidades vendidas em
todos os canais e regiões.

## Metodologia

A avaliação respeitou a ordem temporal dos dados, evitando utilizar
informações futuras durante o treinamento. Foram considerados três
períodos mensais de teste:

  Mês previsto       Período de teste            Dias de treino disponíveis
  ------------------ ------------------------- ----------------------------
  Outubro de 2024    01/10/2024 a 31/10/2024                            946
  Novembro de 2024   01/11/2024 a 30/11/2024                            977
  Dezembro de 2024   01/12/2024 a 31/12/2024                          1.007

Para cada mês, o modelo foi treinado somente com os dados disponíveis
antes do início do período previsto. Após cada mês de teste, as vendas
observadas daquele mês foram incorporadas ao histórico utilizado na
previsão do mês seguinte.

### Modelos avaliados

**Prophet --- baseline**

Utilizado como modelo de referência, sem variável explicativa de
promoção.

**XGBoost**

Modelo baseado em árvores de decisão, utilizando engenharia de atributos
com:

-   Defasagem das vendas de 1 dia (`lag 1`);
-   Defasagem das vendas de 7 dias (`lag 7`);
-   Dia da semana;
-   Mês.

As previsões do XGBoost foram geradas de forma recursiva: durante cada
mês previsto, as previsões dos dias anteriores alimentaram as variáveis
de defasagem dos dias seguintes.

### Tratamento das promoções

A variável de promoção não foi utilizada como preditora. O calendário
futuro de promoções não estava disponível para alimentar as previsões de
maneira consistente.

## Métricas de avaliação

Foram utilizadas duas métricas para comparar as previsões com os valores
observados:

-   **MAE (Mean Absolute Error):** erro absoluto médio, expresso em
    unidades vendidas por dia.
-   **RMSE (Root Mean Squared Error):** raiz do erro quadrático médio,
    também expressa em unidades por dia. Essa métrica penaliza mais
    fortemente erros de maior magnitude.

Em ambas as métricas, valores menores indicam previsões mais próximas
das vendas observadas.

## Resultados

  ---------------------------------------------------------------------------
  Mês                    MAE ---       RMSE ---        MAE ---       RMSE ---
                         Prophet        Prophet        XGBoost        XGBoost
  --------------- -------------- -------------- -------------- --------------
  Outubro/2024             23,60          29,99          27,87          34,45

  Novembro/2024            25,89          32,45          26,78          33,68

  Dezembro/2024            22,07          27,27          31,44          38,97
  ---------------------------------------------------------------------------

### Comparação dos modelos

O Prophet apresentou valores menores de MAE e RMSE nos três meses
avaliados. Portanto, neste experimento, o Prophet teve desempenho
superior ao XGBoost segundo as métricas selecionadas.

## Interpretação e limitações

Os resultados indicam que, para a SKU YO-029, nos períodos avaliados e
com as configurações utilizadas, as previsões do Prophet ficaram mais
próximas das vendas observadas do que as previsões do XGBoost.

É importante considerar as seguintes limitações:

-   A avaliação contempla uma única SKU e três períodos mensais de
    teste.
-   Os resultados não demonstram que o Prophet será superior para outras
    SKUs ou períodos.
-   Promoções não foram incluídas como variáveis explicativas.
-   No XGBoost, a previsão recursiva pode propagar erros ao longo do
    mês.
-   As métricas descrevem erros de previsão diária. Sem informações
    sobre o prazo de reposição e a demanda durante esse prazo, não é
    possível utilizá-las, isoladamente, para recomendar um estoque de
    segurança.

## Tecnologias utilizadas

-   Python
-   Pandas
-   NumPy
-   Prophet
-   XGBoost
-   Scikit-learn

## Autor

**Yukio Kitamura Filho**

Projeto desenvolvido para portfólio em Ciência de Dados.

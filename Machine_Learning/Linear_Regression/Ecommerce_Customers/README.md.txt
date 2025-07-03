# Análise de Regressão Linear em Dados de E-commerce

## Visão Geral do Projeto

Este projeto tem como objetivo construir e avaliar um modelo de Regressão Linear para prever o **Gasto Anual (`Yearly Amount Spent`)** de clientes de uma empresa de e-commerce, com base em características como tempo de uso do aplicativo, tempo de uso do website, duração média da sessão e tempo de associação (tempo como membro). A análise explora as relações entre essas variáveis e o gasto anual, construindo um modelo preditivo robusto.

## Conjunto de Dados

O conjunto de dados `Ecommerce Customers.csv` contém informações fictícias de clientes de uma empresa de e-commerce, incluindo:

* `Email`
* `Address`
* `Avatar`
* `Avg. Session Length`: Duração média das sessões de consultoria de um cliente (em minutos).
* `Time on App`: Tempo médio gasto no aplicativo em minutos.
* `Time on Website`: Tempo médio gasto no website em minutos.
* `Length of Membership`: Quantidade de anos que o cliente é membro.
* `Yearly Amount Spent`: Valor que o cliente gasta anualmente (nosso alvo).

## Ferramentas e Bibliotecas Utilizadas

* **Python**
* **Pandas**: Para manipulação e análise de dados.
* **Numpy**: Para operações numéricas.
* **Matplotlib** e **Seaborn**: Para visualização e exploração de dados.
* **Scikit-learn**: Para construção e avaliação do modelo de Regressão Linear.

## Etapas da Análise

O projeto foi desenvolvido seguindo as seguintes etapas:

### 1. Análise Exploratória de Dados (EDA)

Foi realizada uma análise detalhada para entender a distribuição das variáveis e suas relações.

* **Distribuição do Gasto Anual:** Verificação da distribuição da variável alvo.
* **Correlações Visuais:** Utilização de `jointplot` para visualizar a relação entre `Yearly Amount Spent` e outras variáveis, especialmente `Time on App` e `Length of Membership`.
* **Pairplot:** Para visualizar as relações entre todas as variáveis numéricas.
* **Matriz de Correlação:** Análise quantitativa das correlações entre as variáveis, destacando `Length of Membership`, `Time on App` e `Avg. Session Length` como as mais correlacionadas com `Yearly Amount Spent`.

### 2. Preparação dos Dados para o Modelo

As variáveis foram separadas em:
* **Variáveis Independentes (Features - X):** `['Avg. Session Length', 'Time on App', 'Time on Website', 'Length of Membership']`
* **Variável Dependente (Alvo - y):** `'Yearly Amount Spent'`

Os dados foram então divididos em conjuntos de treino (70%) e teste (30%) usando `train_test_split` para garantir a avaliação imparcial do modelo.

### 3. Construção e Treinamento do Modelo

Um modelo de **Regressão Linear** foi instanciado e treinado utilizando os dados de treino (`X_train`, `y_train`).

### 4. Avaliação do Modelo

O modelo foi avaliado utilizando os dados de teste (`X_test`) e as seguintes métricas:

* **MAE (Erro Médio Absoluto):** Média da magnitude dos erros.
* **MSE (Erro Quadrático Médio):** Média dos erros ao quadrado.
* **RMSE (Raiz do Erro Quadrático Médio):** Raiz quadrada do MSE, na mesma unidade do alvo.
* **R² (Coeficiente de Determinação):** Proporção da variância na variável dependente que é previsível a partir das variáveis independentes.

#### **Resultados das Métricas:**

* **MAE (Erro Médio Absoluto):** `8.558`
* **MSE (Erro Quadrático Médio):** `109.864`
* **RMSE (Raiz do Erro Quadrático Médio):** `10.482`
* **R² (Coeficiente de Determinação):** `0.978`

**Conclusão das Métricas:** O modelo demonstrou uma **performance excepcional**, com um $R^2$ de `0.978`, indicando que aproximadamente 97.8% da variabilidade nos gastos anuais é explicada pelas variáveis do modelo. As métricas de erro (MAE, RMSE) são baixas, confirmando a alta precisão das previsões.

### 5. Análise dos Resíduos

Os resíduos (diferença entre valores reais e previstos) foram analisados visualmente através de um histograma e um gráfico de dispersão:

* **Histograma dos Resíduos:** Mostrou uma distribuição aproximadamente normal centrada em zero, indicando que os erros do modelo são aleatórios e não sistemáticos.
* **Resíduos vs. Valores Previstos:** O gráfico de dispersão não apresentou padrões visíveis (ex: funil, curva), sugerindo que o modelo capturou bem a relação linear nos dados e que não há problemas de heterocedasticidade.

A análise dos resíduos reforça a validade e a robustez do modelo de regressão linear.

### 6. Interpretação dos Coeficientes

A interpretação dos coeficientes do modelo fornece insights sobre a influência de cada feature no `Yearly Amount Spent`:

| Variável                 | Coeficiente |
| :----------------------- | :---------- |
| `Avg. Session Length`    | `25.596`    |
| `Time on App`            | `38.785`    |
| `Time on Website`        | `0.310`     |
| `Length of Membership`   | `61.897`    |

**Interpretações:**

* **`Length of Membership`:** É a variável com maior impacto. Para cada ano adicional como membro, espera-se um aumento de aproximadamente **\$61.90** nos gastos anuais, mantendo as outras variáveis constantes.
* **`Time on App`:** Para cada minuto adicional gasto no aplicativo, espera-se um aumento de aproximadamente **\$38.79** nos gastos anuais.
* **`Avg. Session Length`:** Para cada minuto adicional na duração média da sessão, espera-se um aumento de aproximadamente **\$25.60** nos gastos anuais.
* **`Time on Website`:** Apresenta um impacto muito baixo, com um aumento de apenas **\$0.31** nos gastos anuais para cada minuto adicional no website.

O **Intercepto** (`-1044.26`) representa o gasto anual quando todas as outras variáveis são zero, e pode não ter uma interpretação prática direta neste contexto.

## Conclusões e Próximos Passos

O modelo de Regressão Linear demonstrou ser **extremamente eficaz** na previsão dos gastos anuais dos clientes. As métricas de avaliação e a análise dos resíduos confirmam um modelo robusto e com alto poder explicativo.

**Insights para o Negócio:**
Com base nos coeficientes, a empresa de e-commerce pode focar seus esforços em:
* **Fidelização de Clientes:** Investir em programas de lealdade e retenção, pois o `Length of Membership` é o fator mais impactante.
* **Otimização do Aplicativo:** Continuar investindo na experiência do usuário do aplicativo, já que o tempo gasto no app tem um impacto significante.
* **Avaliação do Website:** Considerar que o tempo gasto no website tem um impacto mínimo no gasto, o que pode indicar a necessidade de otimização da plataforma web ou um direcionamento maior para o aplicativo.

**Possíveis Próximos Passos para o Projeto:**

* **Engenharia de Features:** Explorar a criação de novas features a partir das existentes (ex: interações entre tempo no app e tempo de membro).
* **Testar Outros Modelos:** Avaliar a performance de outros modelos de regressão (ex: Random Forest Regressor, Gradient Boosting Regressor) para comparar e verificar se algum supera a Regressão Linear.
* **Coleta de Mais Dados:** Se possível, obter dados adicionais, como dados demográficos ou informações sobre o histórico de compras, para enriquecer o modelo.
* **Implantação do Modelo:** Se for o caso, pensar em como este modelo poderia ser integrado a um sistema para fazer previsões em tempo real.

---
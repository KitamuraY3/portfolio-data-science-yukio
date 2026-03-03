# 🌸 Análise Visual do Dataset Iris

Este projeto realiza uma análise exploratória detalhada do famoso **dataset Iris**, com foco em visualizações **univariadas, bivariadas e multivariadas**. O objetivo é entender a estrutura dos dados e investigar o potencial de separação entre espécies com base em suas características morfológicas.

---

## 📊 Objetivos

- Explorar a distribuição individual (univariada) de cada variável numérica
- Investigar relações entre pares de variáveis (análise bivariada)
- Aplicar **PCA (Análise de Componentes Principais)** para reduzir a dimensionalidade e visualizar a estrutura dos dados em 2D
- Observar padrões que possam apoiar futuros modelos de classificação

---

## 📁 Estrutura da Análise

1. **Bibliotecas**  
   Importação de pacotes essenciais como `pandas`, `seaborn`, `matplotlib`, `sklearn`.

2. **Dataset**  
   Carregamento do conjunto de dados diretamente da biblioteca `sklearn.datasets`, com tratamento da variável categórica `species`.

3. **Análise Bivariada**  
   Uso de scatterplots, pairplot e heatmap de correlação para investigar relações entre variáveis numéricas e espécies.

4. **Correlação - Heatmap**  
   Cálculo da matriz de correlação entre as variáveis numéricas do dataset para entender as relações lineares entre elas.

5. **Considerações finais - Análise Bivariada**  
   Apresentação de insights extraídos a partir da análise bivariada realizada na etapa anterior.

6. **Análise Multivariada - Redução de Dimensionalidade com PCA**
   Aplicação da técnica de Análise de Componentes Principais (PCA) para reduzir as quatro variáveis numéricas originais em dois componentes principais.

7. **Conclusões**  
   Reflexões sobre a estrutura dos dados e os próximos passos possíveis (como classificação supervisionada).

---

## 🛠️ Tecnologias Utilizadas

- **Python 3.x**
- **Pandas**
- **Seaborn**
- **Matplotlib**
- **Scikit-learn**

---

## 📌 Sobre o Dataset

O dataset Iris é um dos mais clássicos em Machine Learning e estatística. Ele contém **150 amostras** de flores das espécies:
- *Iris setosa*
- *Iris versicolor*
- *Iris virginica*

Com as seguintes variáveis:
- Comprimento e largura da sépala (cm)
- Comprimento e largura da pétala (cm)

---

## 📎 Autor

Projeto desenvolvido por **Yukio Kitamura Filho** como parte do portfólio de Ciência de Dados.

[🔗 GitHub](https://github.com/KitamuraY3)

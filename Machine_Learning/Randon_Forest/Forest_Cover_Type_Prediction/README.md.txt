# 🌲 Forest Cover Type Prediction com Random Forest

Projeto de classificação multiclasse usando Random Forest para prever o tipo de cobertura florestal a partir de variáveis cartográficas da Floresta Nacional Roosevelt (Colorado, EUA). Dataset original disponível no Kaggle: Forest Cover Type Prediction.

---

## 📦 Dataset

- Fonte: competição *Forest Cover Type Prediction* no Kaggle  
- Tamanho: 15.120 observações (treino)  
- Variáveis:
  - 10 features numéricas contínuas (ex.: `Elevation`, `Slope`, distâncias a rios e estradas)
  - 44 variáveis binárias (`Wilderness_Area_*`, `Soil_Type_*`)
  - Target: `Cover_Type` (7 classes de tipos de floresta)

> Observação: O arquivo `train.csv` deve ser baixado diretamente do Kaggle e colocado na pasta do projeto. O dataset é usado apenas para fins acadêmicos e de portfólio.

---

## 🔍 Objetivo do Projeto

Construir um modelo de Machine Learning capaz de classificar o tipo de cobertura florestal com alta acurácia, explorando:

- Análise exploratória detalhada (EDA) das variáveis cartográficas  
- Treinamento de um modelo baseline de Random Forest  
- Otimização de hiperparâmetros com validação cruzada (GridSearchCV)  
- Interpretação dos resultados via métricas, matriz de confusão e importância de features  

---

## 🧪 Metodologia

Principais etapas implementadas no notebook:

1. **Análise Exploratória (EDA)**
   - Inspeção de tipos de dados, estatísticas descritivas e valores ausentes  
   - Distribuição das 7 classes de `Cover_Type` (dataset balanceado)  
   - KDEs e boxplots de features numéricas por classe (ex.: `Elevation`, distâncias e `Hillshade`)  
   - Matriz de correlação para as principais variáveis contínuas  

2. **Pré-processamento**
   - Separação em `X` (features) e `y` (target)  
   - Divisão em treino e teste com `train_test_split` estratificado (80% / 20%)  
   - Padronização das features numéricas com `StandardScaler`

3. **Modelagem**
   - **Modelo baseline**: RandomForestClassifier com configuração padrão e 500 árvores  
   - **Otimização**: GridSearchCV (cv=5) buscando valores para `n_estimators`, `max_depth`, `min_samples_split`, `min_samples_leaf`, `max_features` e `bootstrap`  
   - Avaliação em teste com acurácia, classification report e matriz de confusão

4. **Interpretação**
   - Análise da matriz de confusão (erros entre classes com elevação semelhante)  
   - Gráfico de importância das features (Elevation, distâncias e tipos de solo em destaque)  

---

## 📊 Resultados

| Modelo                    | Acurácia teste | Observações principais                                      |
|---------------------------|---------------:|-------------------------------------------------------------|
| Random Forest baseline    | ~0,87          | Já apresenta boa separação entre as 7 classes              |
| Random Forest otimizado   | ~0,87          | GridSearchCV melhora levemente a estabilidade (cv=5 ≈ 0,867)|

- O modelo consegue distinguir bem os diferentes tipos de cobertura florestal, com f1-score entre ~0,78 e ~0,95 por classe.  
- A feature **`Elevation`** é a mais importante do modelo, seguida por distâncias a hidrografia/estradas e algumas variáveis de solo, confirmando os padrões observados na EDA.  

---

## 🛠️ Stack Tecnológica

- Python 3.x  
- pandas, numpy  
- scikit-learn (modelagem e validação)  
- matplotlib, seaborn (visualização)  
- Jupyter Notebook  

---
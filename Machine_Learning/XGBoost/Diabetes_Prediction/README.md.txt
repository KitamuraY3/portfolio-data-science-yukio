# Diabetes Prediction com XGBoost (Kaggle Playground S5E12)

Este repositório contém a solução para o desafio **Diabetes Prediction** da série *Kaggle Playground Series – Season 5, Episode 12*. O objetivo é prever a **probabilidade de um paciente ser diagnosticado com diabetes** a partir de variáveis tabulares (demográficas, hábitos de vida e histórico clínico), utilizando técnicas de machine learning supervisionado.

Disponível em: https://www.kaggle.com/competitions/playground-series-s5e12

## 📁 Estrutura dos arquivos

- `Diabetes_Prediction.ipynb`  
  Notebook principal com toda a análise exploratória, pré-processamento, modelagem, tuning e geração do arquivo de submissão.

- `train.csv`  
  Conjunto de treino disponibilizado pela competição, contendo a variável alvo `diagnosed_diabetes`.

- `test.csv`  
  Conjunto de teste usado para gerar as previsões enviadas ao Kaggle.

- `submission_xgb_best.csv`  
  Submissão gerada com o modelo XGBoost otimizado.

- `submission_xgb_best_balanced.csv`  
  Submissão gerada com o XGBoost otimizado + balanceamento da classe positiva e threshold ajustado (usado para análise interna).

## 🧠 Abordagem

1. **Análise Exploratória (EDA)**  
   - Análise da distribuição de `diagnosed_diabetes` e das principais variáveis numéricas (idade, IMC, pressão sistólica, minutos de atividade física etc.).  
   - Avaliação de correlações entre features numéricas e o alvo, com foco em variáveis com |correlação| > 0,105.  
   - Estudo das variáveis categóricas (gênero, etnia, escolaridade, renda, histórico familiar, hipertensão, doença cardiovascular, tabagismo, consumo de álcool), tanto na distribuição quanto na proporção de diabéticos por categoria.

2. **Pré-processamento**  
   - Separação de features numéricas e categóricas.  
   - Imputação de valores ausentes (mediana para numéricas, mais frequente para categóricas).  
   - Padronização das variáveis numéricas com `StandardScaler`.  
   - Codificação das variáveis categóricas com `OneHotEncoder`.  
   - Uso de `ColumnTransformer` + `Pipeline` para garantir um fluxo único de pré-processamento e modelagem, evitando data leakage.

3. **Modelos treinados**  
   - **Regressão Logística** como baseline simples.  
   - **XGBoost Classifier** como modelo principal, integrado ao pipeline de pré-processamento.

4. **Tuning e balanceamento**  
   - Otimização de hiperparâmetros do XGBoost com `RandomizedSearchCV`, maximizando a métrica **AUC-ROC** em validação cruzada.  
   - Ajuste do parâmetro `scale_pos_weight` para lidar com o desbalanceamento da classe positiva (diabéticos).  
   - Escolha de um **threshold de decisão = 0,3**, após análise de diferentes cortes e avaliação de precision, recall e f1-score da classe positiva.

## 📈 Resultados

- Melhor modelo: **XGBoost otimizado + balanceamento de classe**.  
- Desempenho em validação (aproximado):  
  - AUC-ROC ≈ 0,72  
  - Accuracy ≈ 0,68  
  - Recall da classe positiva (threshold 0,3) > 0,90, com f1-score em torno de 0,78.  

Na leaderboard pública do Kaggle, o modelo alcançou **score ~0,696**, compatível com os resultados observados em validação.

## 🔭 Próximos passos

- Criar novas features a partir de combinações clínicas relevantes (faixas de idade e IMC, interações entre pressão e histórico de hipertensão, agregações de consumo de álcool e renda).  
- Testar outros algoritmos de gradient boosting (LightGBM, CatBoost) e compará-los com o XGBoost.  
- Explorar técnicas de interpretabilidade de modelos (por exemplo, SHAP) para entender com mais detalhes o impacto de cada variável nas previsões.


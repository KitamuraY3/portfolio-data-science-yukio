# Health Insurance - Previsão de Custos com Machine Learning  

## 📌 Descrição  
Este projeto tem como objetivo prever os custos de seguro de saúde com base em variáveis demográficas e de estilo de vida dos clientes. O trabalho foi desenvolvido como parte do aprendizado em **Ciência de Dados** e utiliza técnicas de **Análise Exploratória de Dados (EDA)** e **Modelagem Preditiva**.  

## 🎯 Objetivos do Projeto  
- **Problema de Negócio:** Entender os principais fatores que influenciam o custo do seguro de saúde.  
- **Objetivo Técnico:** Construir um modelo de Machine Learning capaz de prever os custos individuais.  
- **Objetivos de Aprendizado:** Praticar análise de dados, visualização, preparação de features e modelagem.  
- **Métricas de Sucesso:** Avaliar o desempenho do modelo utilizando **RMSE** e **R²**.  

## 📊 Dataset  
O dataset utilizado contém informações sobre clientes de seguros de saúde, incluindo:  
- Idade  
- Gênero  
- Índice de Massa Corporal (IMC)  
- Número de filhos  
- Tabagismo  
- Região geográfica  
- Custos do seguro  

### Pontos de Atenção  
- Presença de variáveis categóricas (ex.: região, sexo).  
- Possível correlação entre tabagismo e aumento dos custos.  
- Necessidade de normalização e codificação de variáveis.  

## 🛠️ Tecnologias Utilizadas  
- **Linguagem:** Python  
- **Bibliotecas:**  
  - `pandas`, `numpy` → manipulação de dados  
  - `matplotlib`, `seaborn` → visualização de dados  
  - `scikit-learn` → pré-processamento, modelagem e métricas  

## 🔍 Etapas do Projeto  
1. Importação das bibliotecas  
2. Carregamento e análise do dataset  
3. Análise exploratória de dados (EDA)  
4. Pré-processamento (normalização e encoding)  
5. Criação e treinamento do modelo preditivo  
6. Avaliação do modelo com métricas  

## 📈 Resultados Esperados  
- Identificação dos principais fatores que impactam os custos de seguro.  
- Modelo de regressão capaz de prever custos com boa precisão.  
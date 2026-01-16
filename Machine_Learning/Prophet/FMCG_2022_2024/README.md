# 📈 Previsão de Demanda e Planejamento de Estoque — SKU MI-006

## 📌 Visão Geral
Este projeto tem como objetivo desenvolver e comparar modelos de previsão de demanda para uma SKU específica (`MI-006`), com foco em suporte ao planejamento de estoque e mitigação de rupturas.

Foram utilizados dois modelos:
- **Prophet** como baseline para captura de tendência e sazonalidade.
- **XGBoost** para modelagem de padrões não lineares e variações diárias da demanda.

Além da previsão, foi realizada uma **simulação de planejamento de estoque**, incorporando um **buffer de segurança baseado nos erros históricos do modelo**.

---

## 🧠 Objetivos do Projeto
- Analisar o comportamento temporal das vendas (EDA)
- Identificar padrões de sazonalidade e impacto promocional
- Construir um modelo baseline com Prophet
- Desenvolver um modelo preditivo com XGBoost
- Comparar desempenho entre os modelos
- Simular um cenário prático de planejamento de estoque

---

## 🗂️ Estrutura do Projeto
1. Bibliotecas
2. Dataset
3. Análise exploratória
4. Pré-processamento de dados
5. Modelagem
6. Conclusões e etapas futuras

---


## 🔎 Análise Exploratória de Dados (EDA)
A análise exploratória avaliou o comportamento temporal das vendas diárias, padrões de sazonalidade mensal e anual, impacto de promoções e ocorrência de stockouts. Visualizações interativas foram utilizadas para identificar tendências, picos de demanda e períodos críticos, fornecendo contexto para as etapas de modelagem.

## ⚙️ Modelagem Preditiva
### Prophet (Baseline)
O modelo Prophet foi utilizado como baseline, capturando tendência, sazonalidade semanal e anual. Um regressor externo de promoção foi incluído para avaliar o impacto de campanhas promocionais nas vendas. O modelo apresentou previsões estáveis e interpretáveis, servindo como referência inicial.

### XGBoost
O modelo XGBoost utilizou engenharia de atributos com lags temporais, médias móveis e variáveis sazonais. A separação entre treino e teste respeitou a ordem temporal dos dados. O modelo apresentou melhor desempenho na captura de variações diárias e picos de demanda.

## 📊 Avaliação dos Modelos
As métricas utilizadas foram MAE (Mean Absolute Error) e RMSE (Root Mean Squared Error).

- Prophet:  
  MAE = 17.57  
  RMSE = 22.59  

- XGBoost:  
  MAE = 17.02  
  RMSE = 21.04  

O XGBoost apresentou menor erro médio e melhor adaptação às variações da demanda.

## 📦 Simulação de Planejamento de Estoque
Foi realizada uma simulação de planejamento de estoque baseada nas previsões do modelo XGBoost. Um buffer de segurança foi calculado a partir do percentil 95% do erro absoluto histórico do modelo, conforme a fórmula:

```python
buffer_seguranca = np.percentile(abs(residuos), 95)
```python

Essa abordagem permite mitigar riscos de ruptura de estoque ao considerar cenários de erro extremo, mantendo um equilíbrio entre nível de serviço e custo de armazenagem.

---

## 💡 Insights de Negócio

- O Prophet se mostrou eficiente como baseline para entendimento de tendência e sazonalidade

- O XGBoost apresentou melhor desempenho ao capturar picos e variações de curto prazo

- A incorporação de um buffer de segurança baseado nos erros históricos reduz o risco operacional

- A combinação de previsão e intervalo de confiança oferece suporte prático à tomada de decisão em supply chain

---

## 🚀 Próximos Passos

Expansão da modelagem para múltiplas SKUs

Inclusão de variáveis externas como preço, feriados e campanhas

Implementação de monitoramento contínuo do erro do modelo

Deploy do modelo em ambiente produtivo

## 🛠️ Tecnologias Utilizadas

Python, Pandas, NumPy, Plotly, Prophet, XGBoost, Scikit-learn

## 👤 Autor

Yukio Kitamura Filho
Projeto desenvolvido para portfólio em Ciência de Dados

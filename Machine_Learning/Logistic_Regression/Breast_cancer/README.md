# 🩺 Diagnóstico de Câncer de Mama com Regressão Logística

## Descrição do Projeto
Este projeto apresenta um pipeline de análise exploratória, seleção de variáveis e modelagem preditiva utilizando o dataset público Wisconsin Breast Cancer. O objetivo é construir um classificador binário capaz de identificar tumores malignos e benignos com alto desempenho, aplicando técnicas estatísticas sólidas e explicando cada etapa para reforçar a transparência e a interpretação dos resultados.

## Status do Projeto
✅ Concluído (MVP) — estrutura modular e pronta para testes de regularização ou modelos adicionais.

## Índice
- [Descrição do Projeto](#descrição-do-projeto)
- [Status do Projeto](#status-do-projeto)
- [Resumo das Etapas](#resumo-das-etapas)
- [Principais Resultados](#principais-resultados)
- [Como Executar](#como-executar)
- [Tecnologias Utilizadas](#tecnologias-utilizadas)
- [Licença](#licença)

## Resumo das Etapas
- Importação e organização dos dados (sklearn, pandas)
- Análise exploratória: estatísticas, visualizações, matriz de correlação
- Seleção de features via análise de correlação e remoção de redundâncias
- Modelagem com regressão logística usando features independentes
- Avaliação: acurácia, matriz de confusão, relatórios e curva ROC/AUC
- Interpretação dos coeficientes e sugestões de próximos passos

## Principais Resultados
- Seleção criteriosa de features resultou em um modelo simples, estável e fácil de interpretar
- A curva ROC apresentou AUC de 0.98, indicando altíssimo poder discriminante
- O modelo acerta a grande maioria dos diagnósticos, especialmente malignos, com baixo índice de falsos negativos
- Notebook documentado e comentado para facilitar reprodutibilidade e aprendizado

## Como Executar
1. Clone o repositório
2. Instale as dependências listadas em `requirements.txt`
3. Execute o notebook `breast_cancer.ipynb` em um ambiente Jupyter ou VSCode

## Tecnologias Utilizadas
- Python 3.8+
- Jupyter Notebook
- Pandas
- Scikit-learn
- Seaborn & Matplotlib
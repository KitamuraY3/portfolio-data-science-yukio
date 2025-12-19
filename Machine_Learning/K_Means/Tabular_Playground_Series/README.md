# K-Means em Dados de Manufatura Sintéticos  
## Tabular Playground Series – Jul 2022 (Kaggle)

Este projeto aplica o algoritmo **K-Means** ao dataset da competição  
[Tabular Playground Series – Jul 2022](https://www.kaggle.com/competitions/tabular-playground-series-jul-2022)[web:55],
que contém dados tabulares simulados de processos de manufatura.

### Objetivo

Explorar técnicas de **clusterização não supervisionada** para segmentar as 
observações em grupos coerentes e analisar o perfil médio de cada cluster.

### Etapas principais

- Análise exploratória das 29 features numéricas: distribuições por histograma e matriz de correlação das variáveis com maior variância.[web:55][web:82]  
- Pré-processamento com remoção da coluna `id` e padronização das features via `StandardScaler`.[web:82]  
- Escolha do número de clusters usando curva do cotovelo (inertia) e **silhouette score** para k de 2 a 10.[web:80]  
- Treinamento de um modelo **K-Means com k = 5**, com visualização dos clusters em 2D usando PCA e centróides destacados.  
- Análise numérica dos clusters: tamanho de cada grupo, médias das 10 features de maior variância e diferenças em relação à média global.

### Resultados

- Clusters com tamanhos relativamente equilibrados (≈ 15k a 21k amostras por cluster).  
- Score de **Adjusted Rand Index ≈ 0.25** no leaderboard do Kaggle, refletindo a baixa separabilidade global dos dados, mas servindo como baseline honesto para futuros modelos mais sofisticados.[web:55][web:67][web:124]

### Tecnologias

Python, pandas, NumPy, scikit-learn, matplotlib, seaborn.[web:82]

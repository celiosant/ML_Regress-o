📊 Análise de Custos de Seguro de Saúde — Regressão e Clusterização
Projeto de Machine Learning aplicado ao dataset de seguros de saúde, cobrindo desde a análise exploratória até modelos supervisionados de regressão e métodos não supervisionados de agrupamento.

📁 Dataset
[Fonte: Medical Cost Personal Dataset — Kaggle](https://www.kaggle.com/datasets/mirichoi0218/insurance)
O dataset contém informações sobre beneficiários de planos de saúde nos EUA, com as seguintes colunas:
ColunaDescriçãoageIdade do beneficiáriosexSexo (male/female)bmiÍndice de massa corporalchildrenNúmero de filhossmokerFumante (yes/no)regionRegião residencial nos EUAchargesCustos médicos cobrados pelo plano (variável alvo)

🎯 Objetivos

Prever os custos médicos individuais (charges) com diferentes algoritmos de regressão
Comparar desempenho dos modelos por meio de métricas padronizadas
Aplicar técnicas de aprendizado não supervisionado para identificar perfis de beneficiários


🔧 Pré-processamento

One-Hot Encoding nas variáveis categóricas (sex, smoker, region)
Divisão treino/teste: 80% / 20% com random_state=42
Padronização com StandardScaler (essencial para SVR e MLP)


🤖 Modelos de Regressão
Seis algoritmos foram treinados e avaliados:
ModeloObservaçõesLinear RegressionModelo baseDecision TreeSem poda, propenso a overfittingRandom Forest300 estimadores, max_depth=10XGBoost300 estimadores, learning_rate=0.05SVRKernel linearMLP Regressor2 camadas (128, 64), ReLU, Adam, early stopping
Métricas de Avaliação

MAE — Erro Absoluto Médio
MSE — Erro Quadrático Médio
RMSE — Raiz do Erro Quadrático Médio
R² — Coeficiente de Determinação


🔍 Aprendizado Não Supervisionado
PCA (Principal Component Analysis)
Redução de dimensionalidade para 2 componentes, utilizado para visualização e como entrada nos algoritmos de clusterização.
K-Means

Avaliação de K de 2 a 10 clusters via Método do Cotovelo e Silhouette Score
Modelo final com K=3

DBSCAN

Parâmetros: eps=1.5, min_samples=5
Detecta automaticamente o número de clusters e identifica ruídos/outliers

Métricas de Clusterização
MétricaDescriçãoSilhouette ScoreCoesão e separação dos clustersCalinski-HarabaszRazão entre dispersão inter e intra-clusterDavies-BouldinSimilaridade média entre clusters (menor = melhor)

📦 Dependências
bashpip install pandas numpy matplotlib seaborn scikit-learn xgboost kagglehub

▶️ Como Executar

Clone o repositório:

bashgit clone [https://github.com/seu-usuario/seu-repositorio.git](https://github.com/celiosant/ML_Regress-o)
cd seu-repositorio

Instale as dependências:

bashpip install -r requirements.txt

Execute o notebook no Google Colab ou Jupyter:

bashjupyter notebook regressão.ipynb

O dataset é baixado automaticamente via kagglehub. É necessário ter uma conta no Kaggle configurada.


📈 Resultados
Os gráficos de dispersão Valores Reais vs. Valores Preditos são gerados para cada modelo, permitindo comparação visual da qualidade das previsões. A tabela de resultados é ordenada pelo R² em ordem decrescente.

📝 Estrutura do Projeto
├── regressão.py        # Script principal com todo o pipeline
├── README.md           # Documentação do projeto
└── requirements.txt    # Dependências (opcional)

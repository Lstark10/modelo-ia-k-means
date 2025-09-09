# Projeto de Clusterização de Clientes com K-Means

Este projeto implementa um sistema de clusterização de clientes utilizando o algoritmo K-Means, com otimização de hiperparâmetros via Optuna e interface interativa usando Gradio.

## 📊 Visão Geral

O projeto realiza a segmentação de empresas/clientes com base em características como faturamento mensal, número de funcionários, localização, idade da empresa e nível de inovação. O objetivo é identificar grupos similares de clientes para apoiar estratégias de negócio e marketing.

## 🎯 Objetivos

- Segmentar clientes em grupos homogêneos utilizando algoritmo K-Means
- Otimizar hiperparâmetros do modelo para melhor performance
- Validar estatisticamente as diferenças entre grupos
- Fornecer interface web para aplicação do modelo em novos dados
- Salvar modelo e pipeline para reutilização

## 📁 Estrutura do Projeto

```
k-means/
├── dataset.csv                           # Dataset principal com dados dos clientes
├── modelo_ia.ipynb                       # Notebook principal com toda a análise
├── modelo_clusterizacao_clientes.pkl     # Modelo K-Means treinado e otimizado
├── pipeline_clusterizacao_clientes.pkl   # Pipeline de pré-processamento
├── requirements.txt                      # Dependências do projeto
└── README.md                            # Documentação do projeto
```

## 📈 Dataset

O dataset contém informações de **502 empresas/clientes** com as seguintes variáveis:

### Variáveis Numéricas:
- **faturamento_mensal**: Faturamento mensal da empresa (R$)
- **numero_de_funcionarios**: Quantidade de funcionários
- **idade**: Idade da empresa (anos)

### Variáveis Categóricas:
- **localizacao**: Cidade onde a empresa está localizada
  - São Paulo, Rio de Janeiro, Belo Horizonte, Vitória
- **atividade_economica**: Setor de atuação
  - Comércio, Indústria, Agronegócio, Serviços

### Variáveis Ordinais:
- **inovacao**: Nível de inovação da empresa (escala 0-10)

## 🔬 Metodologia

### 1. Análise Exploratória de Dados (EDA)
- Análise da distribuição das variáveis
- Visualizações interativas com Plotly Express
- Análise estatística das diferenças entre grupos

### 2. Validação Estatística
- **Teste de Bartlett**: Verificação da homogeneidade das variâncias
- **Teste de Shapiro-Wilk**: Teste de normalidade dos dados
- **ANOVA de Welch**: Análise de variância para grupos com tamanhos diferentes

### 3. Pré-processamento dos Dados
Utilização de `ColumnTransformer` com diferentes estratégias:
- **Variáveis Numéricas**: Padronização com `StandardScaler`
- **Variáveis Categóricas**: Codificação One-Hot com `OneHotEncoder`
- **Variáveis Ordinais**: Codificação ordinal com `OrdinalEncoder`

### 4. Otimização de Hiperparâmetros
- **Framework**: Optuna com `GridSampler`
- **Parâmetros otimizados**:
  - `n_clusters`: Número de clusters (3-10)
  - `distance_metric`: Métrica de distância (euclidean, minkowski)
- **Métrica de avaliação**: Silhouette Score

### 5. Treinamento do Modelo
- Algoritmo: K-Means com parâmetros otimizados
- Validação através do Silhouette Score
- Atribuição de clusters aos dados originais

## 📊 Resultados e Visualizações

O projeto gera diversas visualizações para interpretação dos clusters:

1. **Idade vs Faturamento Mensal**: Scatter plot colorido por cluster
2. **Inovação vs Faturamento Mensal**: Análise da relação inovação-receita
3. **Número de Funcionários vs Faturamento**: Visualização do porte das empresas

## 🚀 Interface Web com Gradio

O projeto inclui uma aplicação web que permite:
- Upload de novos datasets em formato CSV
- Aplicação automática do modelo treinado
- Download dos resultados com clusters atribuídos
- Interface intuitiva para usuários não técnicos

## 💾 Persistência do Modelo

Os seguintes arquivos são salvos para reutilização:
- `modelo_clusterizacao_clientes.pkl`: Modelo K-Means otimizado
- `pipeline_clusterizacao_clientes.pkl`: Pipeline completo de pré-processamento

## 🛠️ Instalação e Uso
OBS: Caso queira optar por executar em ambientes como Google collab ou Anaconda jupyter, basta descomentar a primeira célula do arquivo ipynb e executar o arquivo caso esteja faltando alguma dependencia. É uma alternativa ao arquivo requirements.txt.

### Pré-requisitos
- Python 3.12+
- Jupyter Notebook ou JupyterLab

### Instalação
```bash
# Clone ou baixe o projeto
cd k-means

# Instale as dependências
pip install -r requirements.txt

# Inicie o Jupyter Notebook
jupyter notebook modelo_ia.ipynb
```

### Execução
1. Execute todas as células do notebook sequencialmente
2. O modelo será treinado e otimizado automaticamente
3. A interface Gradio será iniciada ao final
4. Acesse a interface web no link fornecido

## 📋 Dependências Principais

- **pandas**: Manipulação e análise de dados
- **plotly**: Visualizações interativas
- **scikit-learn**: Algoritmos de machine learning
- **optuna**: Otimização de hiperparâmetros
- **gradio**: Interface web interativa
- **joblib**: Serialização de modelos
- **scipy**: Testes estatísticos
- **pingouin**: Análises estatísticas avançadas

## 🔍 Interpretação dos Resultados

Os clusters gerados podem ser interpretados considerando:
- **Perfil de faturamento**: Empresas de alto, médio e baixo faturamento
- **Porte**: Micro, pequenas, médias e grandes empresas
- **Maturidade**: Empresas jovens vs estabelecidas
- **Inovação**: Nível de adoção tecnológica e inovação
- **Localização**: Distribuição geográfica dos clusters

## 🎯 Aplicações Práticas

Este modelo pode ser utilizado para:
- **Segmentação de mercado**: Identificar diferentes perfis de clientes
- **Estratégias de marketing**: Campanhas direcionadas por cluster
- **Desenvolvimento de produtos**: Soluções específicas para cada grupo
- **Análise de concorrência**: Posicionamento no mercado
- **Precificação**: Estratégias diferenciadas por segmento

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo LICENSE para mais detalhes.


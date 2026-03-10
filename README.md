
# 📡 Telecom X - Previsão de Churn (Parte 2)
---
Este projeto tem como objetivo identificar os principais fatores que levam os clientes da Telecom X a cancelarem seus serviços (Churn) e construir modelos preditivos para antecipar essa evasão.

Status do Projeto: Camada Gold Concluída ✨ (Dados Limpos, Modelos Treinados e Insights Extraídos).

## 🎯 Propósito da Análise

O Churn é a métrica silenciosa que pode quebrar uma empresa de telecomunicações. Nosso objetivo principal foi:

- Identificar Padrões: Entender por que clientes nos deixam após meses de contrato.

- Prever o Futuro: Criar um modelo capaz de sinalizar clientes em risco antes do cancelamento.

- Otimizar o Negócio: Sugerir ações baseadas em dados para aumentar a retenção.

## 📂 Estrutura do Projeto
```bash

├── data/
│   └── telco_churn_treated.csv  # Dataset limpo e codificado (Camada Gold)

├── notebooks/
│   └── analise_preditiva_v2.ipynb # Notebook principal com o pipeline completo

├── visuals/
│   ├── matriz_correlacao.png    # Heatmap de variáveis
│   ├── importancia_features.png # Gráfico de pesos do modelo
│   └── boxplots_evasao.png      # Comparativo de Tenure e 
Faturamento
└── README.md

```


## 🛠️ Preparação dos Dados (Data Pipeline)

A preparação seguiu um rigoroso protocolo de engenharia de dados para evitar o Data Leakage (Vazamento de Dados):

1. Classificação e Seleção: * Identificamos variáveis categóricas (Contrato, Provedor) e numéricas (Tenure, Faturamento Mensal).

- Decisão Técnica: Removemos Faturamento_Total para eliminar a Multicolinearidade com o tempo de contrato, e Genero por não apresentar relevância estatística.

2. Codificação (Encoding):

- Variáveis binárias mapeadas para 0 e 1.

- One-Hot Encoding aplicado em colunas multiclasse com drop_first=True para evitar a armadilha das variáveis dummy.

3. Separação de Dados: * Divisão em 70% Treino e 30% Teste.

- Uso de stratify para manter a proporção real de 26,5% de churn em ambos os conjuntos.

4. Escalonamento (Scaling):

- Aplicação de StandardScaler apenas em variáveis contínuas, garantindo que o modelo de Regressão Logística não fosse enviesado por magnitudes diferentes.
---

### 📈 Insights da Análise Exploratória (EDA)

O Vale da Morte: Clientes com menos de 12 meses de contrato representam a maior parte da evasão.

A Bomba da Fibra Óptica: Curiosamente, clientes de Fibra Óptica (nosso produto premium) têm a maior taxa de churn, sugerindo problemas de preço ou estabilidade.

O Poder da Fidelidade: Contratos de 2 anos reduzem a chance de churn a níveis mínimos, agindo como a principal âncora de retenção.

---

### 🤖 Modelagem e Resultados

Treinamos dois modelos para comparar abordagens lineares e não-lineares:

Regressão Logística (Baseline): Escolhida pela alta interpretabilidade. Alcançou Recall de 55% para a classe de evasão, sendo a nossa escolha para produção por priorizar a captura de desertores.

Random Forest: Utilizada para capturar interações complexas. Confirmou a importância extrema do Tempo de Contrato e do Tipo de Provedor.

Justificativa: Preferimos a Regressão Logística com dados escalonados devido ao equilíbrio entre performance e a facilidade de explicar os coeficientes para os tomadores de decisão.
## 🚀 Como Executar

Clone o repositório:

```bash
  git clone https://github.com/seu-usuario/telecom-x-churn.git
```

```
pip install pandas seaborn matplotlib scikit-learn
```

Abra o Jupyter Notebook:

Navegue até notebooks/analise_preditiva_v2.ipynb e execute as células em ordem. Certifique-se de que o arquivo .csv está na pasta data/.
### Desenvolvido como parte do desafio prático de Ciência de Dados


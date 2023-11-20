# Estimando o risco de crédito com uma Regressão Logística


### 1. O Objetivo do Projeto

O objetivo de um modelo de credit scoring é prever, na data da decisão do crédito, a probabilidade de que o crédito, se concedido, incorra em perda para o credor. A probabilidade de perda em uma operação de crédito denominamos risco de crédito.

O objetivo do projeto era construir um modelo que estimasse o risco de crédito para dados de proponentes de emprestimos hipotecários e agrupar os clientes em classes de risco.



### 2. O Projeto

O projeto foi construído com Python em jupyter notebooks. 

O código foi dividido em 5 etapas:
1. Sample;
2. Explore;
3. Modify;
4. Modelling;
5. Assess;

Os dados usados neste projeto estão disponíveis em
Os dados foram divididos em três amostras: Treino (60% dos dados), Teste (20% dos dados) e Validação (20% dos dados)

### 2. Feature Engineering

**2.1 Missing Values**

Para todas as variáveis com valores vazios criei uma variável binária que indicasse a existência de valor vazio.

A partir dessa binária analisei se os valores faltantes possuíam alguma relação com ocorrência do evento resposta.

Descobri que, os valores faltantes de VALUE e DEBTINC possuíam IV (Information Value) de 0.36 e 1.57 respectivamente;

Por essa razão as variáveis VALUE e DEBTINC foram imputadas com um valor extremo (média + 3*desvio).

Entendi que a ocorrência de valores faltantes das demais variáveis não possuíam poder de discriminação. Por essa razão essas variáveis foram imputadas com uma estratégia de flag de missing + um modelo de árvore.

**2.2 Transformação de Variáveis Categóricas**

O IV de REASON e JOB é muito baixo, -0.008 e -0.078 respectivamente. Por essa razão ambas as variáveis foram deixadas de fora da modelagem. 

**2.3 Transformação de Variáveis Numéricas**

Com a análise exploratória conclui que:
- Nenhuma variável numérica possui linearidade com a variável resposta;
- Todas as variáveis são bastante assimétricas e nenhuma é normal;

Por isso avalie uma eventual discretização. E todas as variáveis numéricas,
quando discretizadas, possuíam IV alto.

Por essa razão todas as variáveis numéricas foram discretizadas usando um modelo de árvore.

**4. Modelagem**

Para a modelagem foi utilizado uma regressão logística com um método de regularização (l1)

**5. Avaliação do modelo**

Para a avaliar o modelo a acurácia do modelo usei as métricas:

- Cumulative Gain
- Confusion Matrix
- Curva de Lift
- Estatística KS
- Curva ROC

Além das métricas de qualidade de ajuste, também analisei a estabilidade do modelo, contabilizando a distribuição de clientes em cada classe de risco.

Além disso calculei o impacto financeiro para diferentes classes de risco.

### Autor do projeto
Tomas Silva

### Referências:
- Manual de Análise de Dados  por Luiz Paulo LUIZ PAULO FAVERO
- Credit Scoring: Desenvolvimento, Implantação, Acompanhamento por Abraham Laredo Sicsú
# Análise de Dados - Rossmann Sales Prediction

## 1. Contexto do Negócio

A **Rossmann** opera mais de **3.000 farmácias em 7 países europeus**.  
Atualmente, os gerentes de loja têm a tarefa de **prever suas vendas diárias com até seis semanas de antecedência**.  

Essas vendas são influenciadas por diversos fatores, como **promoções**, **concorrência**, **feriados escolares e estaduais**, **sazonalidade** e **localização**.

---

## 2. Solução do Problema

O objetivo foi **criar um modelo de Machine Learning** capaz de **prever as vendas das lojas Rossmann nas próximas 6 semanas**, utilizando os dados disponibilizados pela plataforma **Kaggle**.

---

## 3. Planejamento da Solução

O projeto foi estruturado com base no método **CRISP-DM**, seguindo as etapas abaixo:

### 1️⃣ Questão de Negócio  
Prever as vendas das lojas para as próximas 6 semanas.

### 2️⃣ Entendimento do Negócio  
O **CEO** precisa determinar o **valor do orçamento** de cada loja para planejar futuros investimentos e reformas.

### 3️⃣ Coleta de Dados  
Os dados foram obtidos em formato **CSV** na plataforma **Kaggle**.

### 4️⃣ Limpeza e Preparação dos Dados  
Foram realizadas:
- Descrição e análise exploratória das variáveis.  
- *Feature engineering* conforme o viés do negócio.  
- Tratamento de valores ausentes e inconsistentes.

### 5️⃣ Exploração dos Dados  
Exploração para entender o negócio sob a ótica dos dados e identificar variáveis relevantes para o aprendizado do modelo.  
Foram aplicadas análises **univariadas, bivariadas e multivariadas**, além da **validação de hipóteses** com os dados.

### 6️⃣ Modelagem dos Dados  
- Tratamento de variáveis categóricas (*encoding*).  
- Transformações de data e variáveis cíclicas.  
- Aplicação de logaritmo na variável resposta.  
- *Feature selection* com o algoritmo **Boruta**.

### 7️⃣ Algoritmos de Machine Learning  
Foram testados **5 modelos**:  
1 modelo *baseline*, 2 modelos lineares e 2 modelos não lineares.

| Modelo | MAE | MAPE | RMSE |
|--------|------|------|------|
| Random Forest Regressor | 679.62 | 0.0999 | 1011.19 |
| XGBoost Regressor | 843.11 | 0.1226 | 1250.95 |
| Average Model | 1354.80 | 0.4550 | 1835.13 |
| Linear Regression | 1867.08 | 0.2927 | 2671.05 |
| Linear Regression - Lasso | 1891.70 | 0.2891 | 2744.45 |

Em seguida, foi realizado o **Cross Validation** para medir a performance real e selecionar o melhor modelo:

| Modelo | MAE (CV) | MAPE (CV) | RMSE (CV) |
|--------|-----------|-----------|-----------|
| Linear Regression | 2081.73 ± 295.63 | 0.30 ± 0.02 | 2952.52 ± 468.37 |
| Random Forest Regressor | 837.68 ± 219.10 | 0.12 ± 0.02 | 1256.08 ± 229.79 |
| XGBoost Regressor | 1030.28 ± 167.19 | 0.14 ± 0.02 | 1478.26 ± 320.36 |
| Lasso | 2116.38 ± 341.50 | 0.29 ± 0.01 | 3057.75 ± 504.26 |

---

## 4. Avaliação dos Algoritmos

A avaliação foi realizada com base nas métricas **MAE**, **MAPE** e **RMSE**, considerando tanto a **precisão estatística** quanto o **impacto no negócio**.

---

## 5. Principais Insights

###  Insight 1  
Lojas com **vendedores mais próximos** tendem a **vender mais**.

### Insight 2  
Lojas com **promoções ativas por longos períodos** tendem a **vender menos após certo tempo**, indicando saturação do cliente.

### Insight 3  
Lojas com **maior sortimento de produtos** apresentam **menor volume de vendas**, possivelmente por diluição da atenção do consumidor.

---

## 6. Resultados

Os modelos **não lineares** obtiveram melhor desempenho, sendo o **Random Forest** o que apresentou o **melhor resultado geral**.  
No entanto, foi utilizado o **XGBoost** para o *fine tuning* e obtenção da **versão final do modelo**, por sua eficiência e facilidade de ajuste.

| Modelo Final | MAE | MAPE | RMSE | MPE |
|---------------|------|------|------|------|
| XGBoost Regressor | 664.97 | 0.0975 | 957.77 | -0.0035 |

---

## 7. Conclusões

O projeto demonstrou a **eficácia do uso de modelos de Machine Learning** para prever vendas de forma precisa, auxiliando gestores na **tomada de decisão estratégica**.  

O modelo desenvolvido é capaz de fornecer **projeções confiáveis de vendas para 6 semanas**, possibilitando uma **melhor alocação de recursos** e **planejamento de investimentos**.  

Além disso, o processo reforçou a importância do **CRISP-DM** como metodologia estruturada, garantindo clareza nas etapas e reprodutibilidade dos resultados.

---

## 8. Próximos Passos

-  Simular novos cenários de negócio para testar a robustez do modelo.  
-  Explorar **modelos de aprendizado profundo (Deep Learning)** para comparar desempenho.  
-  Aprimorar as análises com novas fontes de dados externas (clima, feriados regionais, eventos locais).

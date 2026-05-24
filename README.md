# 🛠️ Case 2: Ciência de Dados - Manutenção Preditiva

Este projeto foi desenvolvido como parte do processo seletivo para a vaga de Estágio na **M. Dias Branco**. O objetivo principal é construir um modelo de Machine Learning capaz de prever falhas em máquinas industriais com base em dados de sensores, minimizando paradas não planejadas na linha de produção.

---

## 📌 Contexto de Negócio

Na indústria alimentícia, a parada inesperada de uma linha de produção gera altos custos com manutenção corretiva, além do desperdício de matéria-prima que fica retida nas esteiras. 

Este modelo foi desenhado para atuar de forma **preventiva**, acionando a equipe de manutenção mecânica e elétrica com alta assertividade antes que a quebra ocorra.

---

## 🛠️ Tecnologias e Bibliotecas Utilizadas

* **Python 3.12+**
* **Pandas & NumPy:** Manipulação e limpeza dos dados brutos.
* **Matplotlib & Seaborn:** Análise exploratória visual (EDA).
* **Scikit-Learn:** Criação, treinamento e avaliação do modelo preditivo.

---

## 🚀 Estrutura do Pipeline de Dados

O projeto foi dividido de forma modular dentro do notebook `02_manutencao_preditiva.ipynb`:

1.  **Tratamento de Valores Ausentes (NaN):** Imputação dos dados faltantes de `temperatura_celsius` e `pressao_psi` utilizando a mediana das colunas, preservando a distribuição original.
2.  **Engenharia de Recursos (Encoding):** Conversão da variável categórica `tipo_maquina` em variáveis numéricas binárias através do método One-Hot Encoding (`pd.get_dummies`).
3.  **Divisão dos Dados:** Separação em matriz de características ($X$) e vetor alvo ($y$), divididos estritamente em **80% para treino** e **20% para teste**, utilizando amostragem estratificada (`stratify=y`) devido ao desbalanceamento das falhas (apenas 4,2% dos dados).
4.  **Modelagem:** Escolha do algoritmo **Random Forest Classifier** utilizando o parâmetro `class_weight='balanced'` para compensar a raridade da classe de falhas.

---

## 📊 Resultados e Métricas do Modelo

O modelo apresentou uma performance excepcional no conjunto de testes (dados inéditos):

* **Recall (Classe 1 - Falha): 100% (1.00)**
    * *Impacto:* O modelo foi capaz de antecipar **todas** as quebras mecânicas da base de teste. Zero paradas inesperadas passaram batidas.
* **Precisão (Classe 1 - Falha): 95% (0.95)**
    * *Impacto:* Altíssima confiabilidade nos alertas gerados. O time de manutenção só é acionado em cenários reais, evitando alarmes falsos e otimizando a mão de obra.

### Relatório de Classificação Completo:

```text
              precision    recall  f1-score   support

           0       1.00      1.00      1.00       479
           1       0.95      1.00      0.98        21

    accuracy                           1.00       500

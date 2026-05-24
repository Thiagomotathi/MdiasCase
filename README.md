# 🏭 Case M. Dias Branco — Ciência de Dados

Cases técnicos do processo seletivo de Estágio na **M. Dias Branco**: Análise Exploratória de Dados e Manutenção Preditiva com Machine Learning.

**Stack:** Python 3.12+ · Pandas · NumPy · Matplotlib · Seaborn · Scikit-Learn

---

## 📊 Case 1: Análise Exploratória (EDA)

Investigação da base de dados de sensores industriais para extrair insights antes da modelagem:

- Estatísticas descritivas dos sensores de temperatura, pressão e vibração
- Estudo de correlação entre horas de funcionamento, temperatura e pressão
- Descoberta do desbalanceamento: falhas representam apenas **4,2%** dos registros — insight que guiou a estratégia do Case 2
- Visualizações com histogramas e diagramas de dispersão por tipo de máquina

---

## 🛠️ Case 2: Manutenção Preditiva

Modelo de ML para prever falhas em máquinas industriais e evitar paradas não planejadas na linha de produção.

**Pipeline** (`02_manutencao_preditiva.ipynb`):

1. Imputação de NaN em `temperatura_celsius` e `pressao_psi` pela mediana
2. One-Hot Encoding da variável `tipo_maquina`
3. Split 80/20 com amostragem estratificada (`stratify=y`)
4. **Random Forest** com `class_weight='balanced'`

---

## 🛠️ Tecnologias e Bibliotecas Utilizadas

* **Python 3.12+**
* **Pandas & NumPy:** Manipulação e limpeza dos dados brutos.
* **Matplotlib & Seaborn:** Análise exploratória visual (EDA).
* **Scikit-Learn:** Criação, treinamento e avaliação do modelo preditivo.

---

## 🚀 Estrutura do Pipeline de Dados

O projeto foi dividido de forma modular dentro do notebook `02_manutencao_preditiva.ipynb`:

1. **Tratamento de Valores Ausentes (NaN):** Imputação dos dados faltantes de `temperatura_celsius` e `pressao_psi` utilizando a mediana das colunas, preservando a distribuição original.
2. **Engenharia de Recursos (Encoding):** Conversão da variável categórica `tipo_maquina` em variáveis numéricas binárias através do método One-Hot Encoding (`pd.get_dummies`).
3. **Divisão dos Dados:** Separação em matriz de características (X) e vetor alvo (y), divididos estritamente em **80% para treino** e **20% para teste**, utilizando amostragem estratificada (`stratify=y`) devido ao desbalanceamento das falhas (apenas 4,2% dos dados).
4. **Modelagem:** Escolha do algoritmo **Random Forest Classifier** utilizando o parâmetro `class_weight='balanced'` para compensar a raridade da classe de falhas.

---

## 📂 Fontes de Dados & Boas Práticas

Seguindo as boas práticas de mercado e engenharia de dados, a pasta `data/` foi incluída no `.gitignore`. Isso garante que volumes grandes de dados brutos e informações sensíveis não sejam versionados no histórico do Git, mantendo o repositório leve e focado estritamente no código-fonte.

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
```

## 📦 Como Executar o Projeto

Para reproduzir os resultados deste modelo na sua máquina, siga os passos abaixo:

1. Clone o repositório:

```bash
git clone https://github.com/Thiagomotathi/MdiasCase.git
```


2. Prepare a base de dados:
   - Crie uma pasta chamada data na raiz do projeto (caso ela não exista).
   - Cole o arquivo contendo a base de dados do case (fornecido pela banca) dentro dessa pasta com o nome original.
   - O notebook está configurado para ler o caminho: data/nome_do_seu_arquivo.csv

3. Instale as dependências:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

4. Execute o Pipeline:
   - Abra o VS Code, selecione o Kernel do seu ambiente Python e execute as células do arquivo:
   - notebooks/02_manutencao_preditiva.ipynb

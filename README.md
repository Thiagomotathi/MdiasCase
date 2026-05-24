Hahaha, verdade! O interpretador do chat acaba renderizando os títulos e as linhas em vez de mostrar o texto puro para você copiar. Vamos resolver isso agora mesmo.
Aqui está o conteúdo completo e formatado dentro de um bloco de código protegido. É só clicar no botão de copiar no canto superior direito do bloco abaixo e colar direto no seu arquivo README.md:
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

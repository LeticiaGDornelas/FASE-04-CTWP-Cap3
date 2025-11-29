# ATIVIDADE (IR ALÉM) – Da Terra ao Código: Automatizando a Classificação de Grãos com Machine Learning
---

Integrantes (Nome + RM)
Leticia Grossi Dornelas – RM568172
Leonardo Borges Alves da Mota – RM566939
Bernardo Naves Doti Avelar – RM566867
David Eduardo da Silva Correia - RM567525

---


# Classificação de Grãos de Trigo – Machine Learning

Este projeto tem como objetivo analisar um conjunto de dados contendo medições físicas de grãos de trigo e desenvolver modelos de **classificação supervisionada** capazes de distinguir três diferentes variedades:

- **Kama**
- **Rosa**
- **Canadian**

O trabalho segue as etapas clássicas de um fluxo de Machine Learning:  
**Análise Exploratória (EDA) → Pré-processamento → Modelagem → Avaliação → Otimização → Interpretação final.**

---

## 📁 Estrutura do Repositório

/
├── seeds_dataset.txt # Conjunto de dados utilizado
├── fase_04_ctwp_cap3.ipynb # Notebook com análise e modelos
├── fase_04_ctwp_cap3.py # Versão exportada do notebook
└── README.md # Documentação do projeto


---

## 1. Descrição do Conjunto de Dados

O dataset contém **210 amostras**, cada uma representando um grão de trigo descrito por **7 características físicas**:

1. **area** – área do grão  
2. **perimeter** – perímetro do grão  
3. **compactness** – medida de compacidade  
4. **length_kernel** – comprimento do núcleo  
5. **width_kernel** – largura do núcleo  
6. **asymmetry_coefficient** – coeficiente de assimetria  
7. **length_groove** – comprimento do sulco do núcleo  

A variável alvo (**class**) possui 3 rótulos:

- 1 = Kama  
- 2 = Rosa  
- 3 = Canadian  

---

## 2. Análise Exploratória e Pré-processamento

As seguintes etapas foram executadas:

### ✔ Inspeção inicial
- Verificação de dimensões, tipos de dados e contagem de classes.
- Dataset completamente **balanceado**: 70 amostras por classe.

### ✔ Estatísticas descritivas
- Cálculo de média, mediana e desvio padrão.
- Atributos mostram variação coerente entre as variedades.

### ✔ Visualizações
- **Histogramas** e **boxplots** para identificar distribuições e outliers.
- **Pairplot** para observar separabilidade entre classes.
- **Matriz de correlação** mostrando forte relação entre atributos de tamanho.

### ✔ Tratamento de dados
- Não foram encontrados valores ausentes.
- Padronização aplicada com **StandardScaler**.

---

## 🧠 3. Modelos de Classificação Treinados

Foram utilizados cinco algoritmos:

- **K-Nearest Neighbors (KNN)**
- **Support Vector Machine (SVM – RBF)**
- **Random Forest**
- **Logistic Regression**
- **Naive Bayes**

### ✔ Divisão dos dados
- 70% para treino  
- 30% para teste  
- Estratificação mantida  

### ✔ Métricas avaliadas
- **Acurácia**
- **Precisão (macro)**
- **Recall (macro)**
- **F1-score (macro)**
- **Matriz de confusão**

---

## 4. Resultados dos Modelos (Sem Otimização)

Com base nos resultados obtidos:

- **Random Forest** apresentou o melhor desempenho geral (~0.92).
- **KNN** e **SVM (RBF)** obtiveram métricas semelhantes (~0.87).
- **Logistic Regression** veio logo abaixo (~0.85).
- **Naive Bayes** teve o menor desempenho (~0.80), mas ainda razoável.

As matrizes de confusão indicaram que erros tendem a ocorrer entre classes morfologicamente semelhantes.

---

## ⚙ 5. Otimização via Grid Search

Foram ajustados hiperparâmetros de:

- **KNN** → n_neighbors, weights, metric  
- **SVM (RBF)** → C, gamma  
- **Random Forest** → n_estimators, max_depth, min_samples_split  

### ✔ Resultados da otimização
- Melhoras leves a moderadas nas métricas.
- **Random Forest otimizado** manteve o melhor desempenho final.
- **SVM** também apresentou ganhos com ajuste fino de C e gamma.

---

## 6. Conclusões

- O dataset de grãos possui **alta separabilidade**, facilitando a classificação.
- **Random Forest** destacou-se como o melhor modelo:
  - Alta acurácia
  - Robustez a outliers
  - Boa capacidade de generalização  
- A padronização foi essencial para modelos baseados em distância (KNN e SVM).
- Os resultados confirmam que métodos supervisionados são eficazes para classificar variedades de trigo com base em morfologia.

---

## 7. Como Executar o Projeto

### **No Google Colab**
1. Abra o notebook `.ipynb`
2. Faça upload do arquivo `seeds_dataset.txt`
3. Execute todas as células na ordem correta

### **No computador**
Instale as dependências:

```bash
pip install numpy pandas matplotlib seaborn scikit-learn

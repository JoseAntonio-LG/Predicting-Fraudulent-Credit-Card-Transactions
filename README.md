# Credit Card Fraud Detection

Projeto de Data Science para detecção de fraudes em transações de cartão de crédito utilizando algoritmos de Machine Learning.  
O objetivo é identificar padrões em transações fraudulentas e legítimas, minimizando falsos positivos e maximizando a detecção de fraudes.

---

## Índice
1. Sobre o Projeto
2. Tecnologias Utilizadas
3. Conjunto de Dados
4. Estrutura do Projeto
5. Como Executar
6. Resultados
7. Próximos Passos
8. Autor

---

## 1. Sobre o Projeto

Este projeto foi desenvolvido como parte do meu aprendizado em Data Science, com o intuito de aplicar conceitos de análise de dados, pré-processamento, visualização e modelagem.  
O foco está em prever se uma transação é fraudulenta com base em dados anonimizados, preservando alta precisão e um bom recall, para reduzir perdas financeiras e manter a experiência positiva para clientes legítimos.  
Modelos utilizados: **RandomForestClassifier** e **XGBoost**.

---

## 2. Tecnologias Utilizadas

- **Linguagem:** Python 3.10
- **Bibliotecas Principais:**
  - Pandas, NumPy
  - Matplotlib, Seaborn
  - Scikit-learn
  - XGBoost
- **Ambiente:** Jupyter Notebook

---

## 3. Conjunto de Dados

O dataset utilizado é público e está disponível no Kaggle:  
[Credit Card Fraud Detection Dataset](https://www.kaggle.com/mlg-ulb/creditcardfraud)  

**Descrição:**
- 284.807 transações registradas
- 492 fraudes (0,172% do total)
- Variáveis obtidas via PCA para preservar a privacidade
- Colunas principais: `Time`, `Amount`, `V1` a `V28` (componentes principais) e `Class` (variável alvo)

---

## 4. Estrutura do Projeto

📂 credit-card-fraud-detection
├── notebooks/ # Notebooks com análise e modelagem
├── data/ # Dados (ou link para download)
├── images/ # Imagens de gráficos e matrizes de confusão
├── README.md # Documentação do projeto
└── requirements.txt # Lista de dependências


---

## 5. Como Executar

1. Clone este repositório:
```bash
git clone https://github.com/seuusuario/Predicting-Fraudulent-Credit-Card-Transactions.git



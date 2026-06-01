# Predicting Fraudulent Credit Card Transactions

This project explores how machine learning can be used to detect fraudulent credit card transactions in a highly imbalanced financial dataset. The workflow combines exploratory data analysis, feature inspection, model training, threshold tuning, and evaluation with metrics that are appropriate for fraud detection.

The analysis is implemented in [`CreditCard.ipynb`](CreditCard.ipynb).

## Dataset

The project uses the public Credit Card Fraud Detection dataset from Kaggle:

https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud

The dataset contains **284,807 transactions** and **31 columns**:

- `Time`: seconds elapsed between each transaction and the first transaction in the dataset.
- `Amount`: transaction amount.
- `Class`: target variable, where `0` means legitimate transaction and `1` means fraud.
- `V1` to `V28`: anonymized numerical features obtained through PCA.

The dataset is extremely imbalanced:

- **99.83%** legitimate transactions.
- **0.17%** fraudulent transactions.

Because of this imbalance, accuracy alone is not a reliable metric. The project focuses mainly on precision, recall, F1-score, ROC AUC, confusion matrices, and precision-recall behavior.

## Project Workflow

1. Import libraries and load the dataset.
2. Inspect the dataset structure, missing values, and summary statistics.
3. Perform exploratory data analysis:
   - transaction amount distribution;
   - fraud vs. non-fraud class distribution;
   - transaction amount by class;
   - transaction time patterns;
   - density plots for anonymized variables.
4. Create time-based features from the `Time` column.
5. Split the dataset into training, validation, and test sets using stratification.
6. Train and evaluate two machine learning models:
   - `RandomForestClassifier`;
   - `XGBoost`.
7. Select the classification threshold using the validation set.
8. Report final performance on the test set.

## Methodology Notes

The data is split into three mutually exclusive sets:

- **60% training**
- **20% validation**
- **20% test**

The split is stratified by the target class to preserve the fraud/non-fraud ratio in each subset.

The validation set is used for model-selection decisions, including the classification threshold. The test set is kept only for final evaluation, which helps avoid optimistic performance estimates.

## Models

### Random Forest

The Random Forest model is used as a strong baseline. It provides feature importance scores and performs well on the minority class, although recall remains the main area for improvement.

Validation performance for the fraud class:

| Metric | Value |
| --- | ---: |
| Precision | 0.9398 |
| Recall | 0.7959 |
| F1-score | 0.8619 |
| ROC AUC | 0.8979 |

### XGBoost

XGBoost is trained with early stopping using the validation set. A probability threshold is selected based on the validation precision-recall curve and then applied to the test set.

The selected threshold was:

| Threshold Source | Value |
| --- | ---: |
| Validation set | 0.5586 |

Final test performance for the fraud class:

| Metric | Value |
| --- | ---: |
| Precision | 0.9091 |
| Recall | 0.8081 |
| F1-score | 0.8556 |
| ROC AUC | 0.9759 |
| Accuracy | 0.9995 |

In the test set, this corresponds to approximately **80 detected frauds**, **19 missed frauds**, and **8 legitimate transactions incorrectly flagged as fraud**.

## Key Takeaways

The models achieve strong fraud-detection performance despite the severe class imbalance. XGBoost shows strong ranking performance, with a test ROC AUC of **0.9759**, and the validation-selected threshold provides a balanced fraud-class F1-score of **0.8556**.

The main business trade-off is between:

- reducing false positives, so legitimate transactions are not unnecessarily flagged;
- increasing recall, so fewer fraudulent transactions are missed.

In this type of problem, recall for the fraud class is especially important because false negatives represent fraudulent transactions that pass undetected.

## How to Run

1. Download `creditcard.csv` from Kaggle.
2. Place the file in the root folder of this project.
3. Open and run [`CreditCard.ipynb`](CreditCard.ipynb).

Required Python libraries include:

```text
pandas
numpy
matplotlib
seaborn
plotly
scikit-learn
xgboost
```

## Related Article

An explanatory article about the project is available here:

https://medium.com/@jose.lopesgomes012/predicting-fraudulent-credit-card-transactions-c1ae2d86d733

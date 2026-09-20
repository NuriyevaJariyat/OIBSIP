# Credit Card Fraud Detection

## Project Overview

This project focuses on detecting fraudulent credit card transactions using machine learning.

The main goal is to identify fraudulent transactions despite a highly imbalanced dataset, where legitimate transactions significantly outnumber fraudulent ones.

## Dataset

The project uses the Credit Card Fraud Detection dataset.

The dataset contains:

* 284,807 transactions
* 492 fraudulent transactions
* 30 features
* 1 target variable: `Class`

The target variable:

* `0` — legitimate transaction
* `1` — fraudulent transaction

## Class Imbalance

The dataset is highly imbalanced:

* Legitimate transactions: **99.827%**
* Fraudulent transactions: **0.173%**

Because fraudulent transactions represent only a very small part of the dataset, accuracy alone is not sufficient for evaluating the model.

## Exploratory Data Analysis

The data was analyzed to understand:

* Transaction amount distribution
* Transaction timing
* Fraudulent vs legitimate transactions
* Class imbalance
* Missing values

The dataset contained no missing values.

A derived `Hour` feature was created from the `Time` column to explore transaction activity by hour.

## Why Accuracy Can Be Misleading

Accuracy can be misleading for highly imbalanced fraud detection datasets.

A model could classify most transactions as legitimate and still achieve very high accuracy while missing many fraudulent transactions.

Therefore, this project uses additional evaluation metrics:

* Precision
* Recall
* F1-score
* ROC-AUC

## Data Preparation

The dataset was divided into training and testing sets using an 80/20 split.

Stratification was used to preserve the proportion of fraudulent transactions in both datasets.

The training data initially contained:

* 227,451 legitimate transactions
* 394 fraudulent transactions

## Handling Class Imbalance

SMOTE (Synthetic Minority Over-sampling Technique) was applied to the training data.

SMOTE creates synthetic examples of the minority class instead of simply duplicating existing fraudulent transactions.

After SMOTE:

* Legitimate transactions: **227,451**
* Fraudulent transactions: **227,451**

SMOTE was applied only to the training data. The test data was kept unchanged to provide a realistic evaluation.

## Machine Learning Models

Two machine learning models were trained:

### 1. Logistic Regression

Logistic Regression was used as a baseline classification model.

Results for fraudulent transactions:

* Precision: **0.13**
* Recall: **0.90**
* F1-score: **0.23**
* ROC-AUC: **0.9765**

The model detected approximately 90% of fraudulent transactions, but its precision was low, meaning that it generated many false fraud alerts.

### 2. Random Forest

Random Forest was trained using the balanced training data created with SMOTE.

Results for fraudulent transactions:

* Precision: **0.84**
* Recall: **0.83**
* F1-score: **0.83**
* Accuracy: **1.00**

Random Forest provided a more balanced result between precision and recall.

## Model Evaluation

The models were evaluated using:

### Precision

Precision measures how many transactions predicted as fraudulent were actually fraudulent.

### Recall

Recall measures how many actual fraudulent transactions were detected by the model.

### F1-score

F1-score combines Precision and Recall into a single metric.

### ROC-AUC

ROC-AUC measures how well the model distinguishes between legitimate and fraudulent transactions across different classification thresholds.

A ROC curve was also created to compare the two models.

## Feature Importance

Feature importance was analyzed using the Random Forest model.

Among the features shown in the feature importance analysis, `V14` had the highest importance.

The feature importance indicates how strongly a feature was used by the model to separate the classes. It does not mean that the feature itself causes fraud.

## Scalability

The model could be used for a high-volume transaction system processing 1 million transactions per hour, which is approximately 278 transactions per second.

To handle this volume, the system could use real-time or batch processing, efficient feature preprocessing, and multiple model instances running in parallel. The model should also be monitored for changes in fraud patterns and retrained periodically.

For a production system, prediction speed, infrastructure capacity, data drift, and model performance would need to be monitored continuously.

## Key Findings

The analysis demonstrates that fraud detection is challenging because fraudulent transactions are extremely rare compared with legitimate transactions.

SMOTE helped balance the training data and allowed the models to learn from the minority class.

Logistic Regression achieved high fraud recall but low precision.

Random Forest achieved a more balanced combination of precision and recall, with a fraud precision of 0.84 and recall of 0.83.

The results also demonstrate why accuracy should not be considered the only metric for an imbalanced fraud detection problem.

## Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
* imbalanced-learn
* JupyterLab

## Project Workflow

1. Load the dataset
2. Inspect the data
3. Analyze class imbalance
4. Perform exploratory data analysis
5. Split the data into training and testing sets
6. Apply SMOTE to the training data
7. Train Logistic Regression
8. Train Random Forest
9. Evaluate Precision, Recall, F1-score and ROC-AUC
10. Plot the ROC curve
11. Analyze feature importance
12. Discuss scalability

## Conclusion

This project demonstrates a complete machine learning workflow for credit card fraud detection.

The main challenge was the severe class imbalance between legitimate and fraudulent transactions. SMOTE was used to balance the training data, while the original test data was preserved for realistic evaluation.

The comparison of Logistic Regression and Random Forest showed the importance of using multiple evaluation metrics instead of relying only on accuracy.

In a real-world fraud detection system, the balance between detecting fraudulent transactions and minimizing false alerts would depend on the business requirements and the cost of different types of errors.


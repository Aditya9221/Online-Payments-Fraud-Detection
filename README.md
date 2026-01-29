# Online Payment Fraud Detection
Project Overview

This project focuses on detecting fraudulent online payment transactions using machine learning. Fraud detection is a real-world classification problem characterized by extreme class imbalance, where fraudulent transactions form a very small percentage of total data.

The primary objective of this project is to minimize missed fraud cases, rather than maximize overall accuracy.

# Dataset Characteristics

Fraud transactions ≈ 0.19%

Non-fraud transactions ≈ 99.81%

Highly imbalanced target variable

Due to this imbalance, traditional metrics like accuracy are misleading and insufficient for model evaluation.

# Methodology
1️. Data Preprocessing

Numerical features scaled using StandardScaler

Categorical features encoded using OneHotEncoder

Feature processing handled via ColumnTransformer

Pipeline-based workflow used to avoid data leakage

2️. Handling Class Imbalance

To address extreme class imbalance:

SMOTE (Synthetic Minority Over-sampling Technique) was applied only on training data

Implemented using an imblearn pipeline to prevent data leakage

SMOTE was used to improve minority class representation during training, not as a standalone solution

3️. Models Used

Three classification models were trained and compared:

Logistic Regression – baseline linear model

Decision Tree Classifier – non-linear model for interpretability

Random Forest Classifier – ensemble model for robust performance

Class-weight balancing was applied where applicable to further penalize misclassification of fraud cases.

4️. Model Evaluation Strategy

Given the imbalance, evaluation focused on:

Recall (fraud class)

F1-score

ROC-AUC

Confusion Matrix

Accuracy was used only as a reference metric and not for final decision-making.

5️. Threshold Tuning

Used predict_proba() to obtain fraud probabilities

Applied custom decision thresholds instead of default 0.5

Threshold tuning allowed control over the recall–precision trade-off

The final threshold was selected to prioritize recall

# Final Results

Recall (Fraud): 100%

Precision: Low due to a high number of false positives

F1-score: Low (expected under extreme class imbalance)

The final Random Forest model successfully detected all fraudulent transactions, accepting higher false positives as a business-aligned trade-off.

# Key Insight

In fraud detection systems:

Missing a fraudulent transaction is far more costly than flagging a legitimate one.

Therefore, prioritizing recall over precision is a deliberate and justified decision.

# Conclusion

Due to extreme class imbalance, accuracy was not a reliable metric for this problem. By combining SMOTE-based oversampling, class-weight balancing, and probability-based threshold tuning, the final model achieved 100% recall, ensuring that no fraudulent transactions were missed. Although this resulted in low precision due to many false positives, the trade-off is acceptable in fraud detection scenarios where minimizing missed fraud is the primary objective.

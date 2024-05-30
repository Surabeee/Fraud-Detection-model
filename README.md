# Fraud Detection Model using XGBoost

This repository contains a fraud detection model designed to identify fraudulent transactions in a financial dataset using the XGBoost algorithm. The model is built, trained, and evaluated using a dataset containing over 6 million transactions.

## Table of Contents

- [Overview](#overview)
- [Data Preprocessing](#data-preprocessing)
- [Model Training](#model-training)
- [Model Evaluation](#model-evaluation)
- [Key Factors Predicting Fraud](#key-factors-predicting-fraud)
- [Results and Interpretation](#results-and-interpretation)
- [Conclusion](#conclusion)
- [How to Use](#how-to-use)

## Overview

The fraud detection model leverages XGBoost, an efficient and scalable implementation of gradient boosting, to classify transactions as fraudulent or non-fraudulent.

## Data Preprocessing

1. **Loading the Data**: The dataset contains 6,362,620 rows and 10 columns.
2. **Handling Missing Values**: Ensured data completeness.
3. **Handling Outliers**: Identified outliers using box plots.
4. **Handling Multicollinearity**: Used Variance Inflation Factor (VIF) to identify high multicollinearity among features.
5. **Feature Engineering**:
   - Created `balanceOrigDiff` and `balanceDestDiff` to capture balance changes.
   - Applied log transformations to reduce skewness.
6. **Encoding Categorical Variables**: One-hot encoded the transaction type (`type`).

## Model Training

1. **Feature Selection**: Selected features included:
   - `amount_log`, `balanceOrigDiff_log`, `balanceDestDiff_log`, and one-hot encoded transaction types.
2. **Splitting the Data**: Split the data into training (80%) and testing (20%) sets.
3. **Training the Model**: Trained the XGBoost model with the following parameters:
   - `use_label_encoder=False`
   - `eval_metric='logloss'`
   - `random_state=42`
   - `n_jobs=-1`

## Model Evaluation

1. **Predictions**: Made predictions on the test set.
2. **Performance Metrics**:
   - Confusion Matrix: Visualized true/false positives and negatives.
   - Classification Report: Provided precision, recall, f1-score, and support.
   - ROC AUC Score: Measured overall performance.

## Key Factors Predicting Fraud

1. **Feature Importance**: Extracted from the XGBoost model. Important features included:
   - `amount_log`, `balanceOrigDiff_log`, `balanceDestDiff_log`, and transaction types.

## Results and Interpretation

The XGBoost model achieved a high ROC AUC score, indicating good discrimination between fraudulent and non-fraudulent transactions. Important features made intuitive sense:
- **Transaction Amount**: Large or unusual amounts.
- **Balance Differences**: Significant changes in balances.
- **Transaction Types**: Certain types (e.g., TRANSFER) more prone to fraud.

## Conclusion

The XGBoost-based model effectively detects fraudulent transactions by leveraging engineered features and addressing multicollinearity. Regular updates and fine-tuning are recommended to adapt to new fraud patterns.

## How to Use

1. **Clone the Repository**:
    ```sh
    git clone https://github.com/yourusername/Fraud-Detection-model.git
    cd Fraud-Detection-model
    ```

2. **Install Dependencies**:
    ```sh
    pip install -r requirements.txt
    ```

3. **Run the Model**:
    ```sh
    python fraud_detection.py
    ```

4. **Evaluate the Model**: Review the output metrics and feature importance to understand the model's performance.

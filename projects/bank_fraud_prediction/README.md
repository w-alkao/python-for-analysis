# 🏦 Bank Fraud Detection using Machine Learning

## 📌 Project Overview

This project develops a **machine learning system for detecting fraudulent bank transactions**. The objective is to identify potentially fraudulent transactions in a highly imbalanced dataset, where legitimate transactions significantly outnumber fraudulent ones.

The project explores transaction patterns, performs data cleaning and feature engineering, compares multiple machine learning algorithms, and optimizes the fraud detection threshold to achieve high fraud recall while reducing false positives.

## 🎯 Problem Statement

Fraudulent transactions represent a small proportion of total banking transactions, making fraud detection a challenging **imbalanced classification problem**.

A traditional rule-based flagging system may fail to detect a significant portion of fraudulent activity. This project aims to build a machine learning model capable of:

* Detecting fraudulent transactions
* Identifying important fraud-related patterns
* Handling highly imbalanced classes
* Minimizing false positives
* Maintaining high fraud detection recall
* Providing a reusable trained model for future predictions

## 🔍 Exploratory Data Analysis

The project investigates several aspects of transaction behavior, including:

* Fraud rate and class distribution
* Fraud rate by transaction type
* Fraud rate by transaction amount
* Fraud patterns across different hours
* Day vs. night transaction behavior
* Transaction amount distribution
* Correlation between balance-related variables
* Existing rule-based fraud flags

The analysis shows that fraudulent transactions represent only a small fraction of the dataset, making **precision-recall analysis particularly important**.

## 🧹 Data Cleaning & Feature Engineering

Several preprocessing and feature engineering steps were applied:

* Checked for missing values
* Distinguished valid zero balances from actual missing data
* Applied `log1p` transformation to transaction amounts to reduce skewness
* Created an `is_high_amount` feature to identify transactions above the 99th percentile
* Created balance-difference features:

  * `balance_diff_orig`
  * `balance_diff_dest`
* Removed highly correlated and redundant balance variables
* Encoded transaction types using `LabelEncoder`
* Removed identifier fields such as origin and destination account names
* Applied `RobustScaler` to numerical features
* Used a stratified train/test split to preserve the fraud ratio

## 🤖 Machine Learning Models

Three classification algorithms were evaluated:

1. **Logistic Regression**
2. **Random Forest**
3. **XGBoost**

Class imbalance was addressed using class weighting and `scale_pos_weight` for XGBoost.

Model performance was evaluated using:

* ROC-AUC
* PR-AUC
* Precision
* Recall
* Classification Report
* Confusion Matrix

Because fraud is a rare event, **PR-AUC and fraud recall** were given particular importance rather than relying only on accuracy or ROC-AUC.

## ⚙️ Threshold Optimization

Instead of using the default probability threshold of `0.5`, the project optimized the decision threshold based on the precision-recall trade-off.

The objective was to achieve approximately **90% fraud recall** while improving precision and reducing unnecessary fraud alerts.

This demonstrates an important practical aspect of fraud detection: the probability threshold can be adjusted according to the operational cost of false positives versus missed fraud.

## 📊 Model Performance

The tuned XGBoost model achieved approximately:

| Metric       | Result |
| ------------ | -----: |
| Fraud Recall |   ~90% |
| Precision    |   ~29% |
| PR-AUC       |  ~0.88 |

The results indicate that the model can detect a large proportion of fraudulent transactions while limiting the number of transactions sent for further investigation.

> Performance values may vary slightly depending on the dataset version, preprocessing, and execution environment.

## 🔑 Key Fraud Indicators

The analysis identified several transaction characteristics associated with fraudulent activity:

* Large transaction amounts
* Significant changes in account balances
* Certain transaction types
* Night-time transactions
* Transfers involving non-merchant destinations
* Unusual transaction behavior

These features provide useful signals for identifying potentially suspicious transactions.

## 💾 Model Deployment Preparation

The final model is saved as a reusable artifact using `joblib`.

The saved artifact contains:

* Trained model
* Selected decision threshold
* Feature list
* Model name

This allows the trained model to be loaded later and used to score new transactions without retraining the entire pipeline.

## 🛡️ Potential Fraud Prevention Strategies

A production fraud detection system could combine the machine learning model with additional security mechanisms such as:

* Real-time transaction scoring
* Step-up authentication
* Transaction velocity rules
* Rule-based + ML two-stage detection
* Continuous model monitoring
* Periodic model retraining
* Human review of high-risk transactions

## 🛠️ Technologies Used

* **Python**
* **Pandas**
* **NumPy**
* **Scikit-learn**
* **XGBoost**
* **Matplotlib**
* **Seaborn**
* **Joblib**
* **Jupyter Notebook**

## 📂 Project Structure

```text
bank-fraud-detection/
│
├── bank_fraud_prediction.ipynb
├── data.csv
├── best_fraud_model_tuned.pkl
└── README.md
```

## 🚀 How to Run

### 1. Clone the repository

```bash
git clone https://github.com/your-username/bank-fraud-detection.git
cd bank-fraud-detection
```

### 2. Install dependencies

```bash
pip install pandas numpy scikit-learn xgboost matplotlib seaborn joblib jupyter
```

### 3. Launch the notebook

```bash
jupyter notebook bank_fraud_prediction.ipynb
```

### 4. Run the notebook

Make sure `data.csv` is located in the same directory as the notebook before running the cells.

## 📈 Key Takeaways

This project demonstrates an end-to-end machine learning workflow for an imbalanced financial classification problem:

**Data Exploration → Data Cleaning → Feature Engineering → Model Training → Model Comparison → Threshold Optimization → Model Tuning → Evaluation → Model Saving**

The project emphasizes that in fraud detection, **accuracy alone is not sufficient**. A useful fraud detection model must balance fraud recall with precision and the operational cost of false alerts.

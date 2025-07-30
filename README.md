# 🛡️ Fraud Detection using Machine Learning

A comprehensive project to detect fraudulent financial transactions using EDA, feature engineering, and multiple classification models with hyperparameter tuning.

---

## 📌 Problem Statement

Detect fraudulent transactions from a large dataset (~6.3M records), improving accuracy and minimizing false positives.

---

## 📂 Dataset

Dataset is not uploaded due to size constraints.  
📥 **Download from:** [Insert your dataset link]  
Place the file in the `data/` directory.

---

## 🛠️ Project Steps

1. **Data Cleaning**
   - Handled missing values and invalid entries
2. **EDA**
   - Plotted distributions, boxplots, and correlation heatmaps
3. **Feature Engineering**
   - Created `balance_change`, `orig_balance_diff`, etc.
4. **Outlier Treatment & Multicollinearity**
5. **Modeling**
   - Logistic Regression
   - Random Forest
   - XGBoost
   - CatBoost (with tuning)
   - LightGBM (with tuning)
6. **Evaluation**
   - Metrics: Accuracy, Precision, Recall, F1, AUC

---

## 📊 Model Summary

| Model      | Precision | Recall | F1 Score | AUC |
|------------|-----------|--------|----------|-----|
| Logistic   | 0.91      | 0.76   | 0.83     | 0.92|
| RandomForest | 0.96    | 0.89   | 0.92     | 0.97|
| XGBoost    | 0.97      | 0.91   | 0.94     | 0.98|
| CatBoost   | 0.98      | 0.92   | 0.95     | 0.99|
| LightGBM   | 0.98      | 0.93   | 0.96     | 0.99|

---

## ✅ Key Insights

- Fraudulent transactions show distinct balance patterns.
- CatBoost and LightGBM outperform others in precision and recall.
- Derived features significantly boost model performance.

---

## 📦 Setup

```bash
pip install -r requirements.txt

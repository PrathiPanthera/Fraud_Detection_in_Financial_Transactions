# Fraud Detection Project - Final Conclusions

## Problem Statement
Detect fraudulent financial transactions using classification models on a large transaction dataset.  
**Target variable**: `isFraud` (binary classification).

---

## Business Objective
- Build an accurate model to flag suspicious transactions.
- Prioritize minimizing **false negatives** (missed frauds) while controlling false positives.

---

## Key EDA Insights
- **Class imbalance**: Fraudulent cases are less than 0.1% of total.
- **High-value transactions** are more prone to fraud.
- `TRANSFER` and `CASH_OUT` are the most fraud-prone transaction types.
- Features like `amount`, `balance_diff`, and `orig_balance_diff` are strong fraud indicators.

---

## Feature Engineering
- Derived Features:
  - `balance_change` = |oldbalanceOrg - newbalanceOrig| + |oldbalanceDest - newbalanceDest|
  - `orig_balance_diff` = oldbalanceOrg - newbalanceOrig
- Log transformation applied to skewed features.
- Multicollinearity treated using **VIF**.
  
---

## Modeling Summary

| Model               | Highlights                                              |
|--------------------|----------------------------------------------------------|
| Logistic Regression | Interpretable baseline. Improved with `class_weight='balanced'`. |
| Random Forest       | Strong performance, manageable with tuned `n_estimators`. |
| XGBoost (Tuned)     | Best performance overall. High AUC, F1-score. Handles imbalance well. |
| CatBoost (Tuned)    | Competitive with XGBoost. Less preprocessing. Fast training. |
| LightGBM (Tuned)    | Extremely fast, very good performance. Slightly behind XGBoost. |

All models evaluated using: **Accuracy**, **Precision**, **Recall**, **F1-score**, and **ROC-AUC**.  
**Recall** and **AUC** were prioritized to detect the majority of fraudulent cases.

---

## Final Recommendation

- Use **XGBoost with Hyperparameter Tuning** as the final model.
- For speed-critical or explainable use cases, also consider:
  - **CatBoost** (great speed and performance)
  - **Logistic Regression** (for stakeholder transparency)
  - **LightGBM** (fast with near-best results)

---

## Feature Recommendations

- Retain:
  - `amount`, `balance_change`, `orig_balance_diff`, log-transformed balances
- Explore:
  - Time-based features (hour, day of week)
  - Behavioral/user profiling
  - Historical transaction context

---

All code, EDA notebooks, and models are versioned and available in this GitHub repository.

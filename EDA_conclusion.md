
### `eda_conclusions`

**1. Class Imbalance Observed**

* The dataset is highly imbalanced with a very small percentage of fraud cases (`isFraud = 1`).
* This necessitates techniques like `class_weight`, resampling, or anomaly detection.

**2. Transaction Type Insight**

* Most fraudulent transactions are of type `TRANSFER` and `CASH_OUT`.
* Other types like `PAYMENT` and `DEBIT` rarely show fraud.

**3. Balance Behavior Indicates Fraud**

* Fraudulent transactions often show unusual balance patterns such as:

  * `oldbalanceDest = 0` while `newbalanceDest` has a significant increase.
  * No change in `oldbalanceOrg` despite high `amount` values.

**4. Amount Distribution**

* Fraud transactions tend to have high transaction amounts compared to non-fraud cases.

**5. Highly Correlated Features**

* Features like `oldbalanceOrg`, `newbalanceOrg`, `oldbalanceDest`, and `newbalanceDest` are highly correlated.
* Created meaningful derived features like:

  * `balance_change`
  * `orig_balance_diff`
  * `dest_balance_diff`

**6. Outliers Detected**

* Outliers in `amount` and balance features were identified via boxplots and treated via IQR/quantile clipping.

**7. Multicollinearity Addressed**

* Variance Inflation Factor (VIF) analysis was conducted.
* Highly collinear variables were dropped or transformed to avoid redundant predictors.

**8. Final Feature Set**

* Numerical + derived features retained after outlier handling and correlation analysis.
* Categorical variables like `type` were encoded.


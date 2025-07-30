### `modelling_conclusions`

**1. Train-Test Split and Feature Scaling**

* Dataset was split into training and testing sets (typically 75/25).
* StandardScaler was applied to numerical features to ensure consistent model input.

**2. Logistic Regression (Baseline Model)**

* Performed decently but struggled with recall due to class imbalance.
* Suitable as a quick baseline, but not optimal for fraud detection.

**3. Random Forest Classifier**

* Handled non-linear patterns and interactions effectively.
* Performed well with balanced accuracy and recall.
* Provided good feature importance insights.

**4. XGBoost Classifier**

* Delivered high test AUC and F1 scores.
* Robust to overfitting and handled class imbalance well using `scale_pos_weight`.
* Best performance observed when hyperparameters like `n_estimators`, `max_depth`, and `learning_rate` were tuned.

**5. CatBoost Classifier**

* Efficient with categorical features and performed well with minimal preprocessing.
* Hyperparameter tuning using `RandomizedSearchCV` improved results.
* Outperformed Logistic Regression and was comparable to XGBoost and LightGBM.

**6. LightGBM Classifier**

* Very fast and efficient with large data (60k+ rows).
* Hyperparameter tuning helped enhance AUC and F1-score.
* Strong candidate for production due to speed and performance.

**7. Best Model Selection**

* XGBoost and LightGBM showed the best balance of recall, precision, and AUC.
* CatBoost was close behind and easier to deploy with fewer preprocessing steps.

**8. Model Evaluation Metrics Used**

* Accuracy, Precision, Recall, F1-score, and ROC-AUC were calculated for both train and test sets.
* ROC-AUC was the main metric due to class imbalance.

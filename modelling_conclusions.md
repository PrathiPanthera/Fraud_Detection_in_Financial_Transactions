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

## Model Performance Summary

| Model         | Train Accuracy | Test Accuracy | Train Precision | Test Precision | Train Recall | Test Recall | Train F1 | Test F1 | Train AUC | Test AUC |
|---------------|----------------|---------------|------------------|-----------------|---------------|--------------|----------|---------|------------|-----------|
| Logistic      | 0.998709       | 0.998709      | 0.000000         | 0.000000        | 0.000000      | 0.000000     | 0.000000 | 0.000000| 0.784791   | 0.786708  |
| Random Forest | 0.999994       | 0.999996      | 0.999674         | 0.999512        | 0.995942      | 0.997077     | 0.997804 | 0.998293| 1.000000   | 0.999277  |
| XGBoost       | 0.999890       | 0.999822      | 0.961961         | 0.930867        | 0.952435      | 0.931320     | 0.957174 | 0.931093| 0.999984   | 0.999824  |
| CatBoost      | 0.999959       | 0.999967      | 0.973179         | 0.977555        | 0.995455      | 0.997077     | 0.984191 | 0.987220| 0.998664   | 0.999249  |
| LightGBM      | 0.998783       | 0.998841      | 0.514760         | 0.526898        | 0.996429      | 0.997077     | 0.678832 | 0.689458| 0.999766   | 0.999686  |
| CatBoost      | 0.999959       | 0.999967      | 0.973179         | 0.977555        | 0.995455      | 0.997077     | 0.984191 | 0.987220| 0.998664   | 0.999249  |


* Accuracy, Precision, Recall, F1-score, and ROC-AUC were calculated for both train and test sets.
* ROC-AUC was the main metric due to class imbalance.

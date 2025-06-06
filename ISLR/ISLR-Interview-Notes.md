# 📘 ISLR Interview Notes – High-Yield Concepts

A distilled summary of key ISLR concepts that are frequently asked in data science and quant/stat interviews.

---

## 📌 1. Linear Regression

### 🔹 What are the assumptions of linear regression?
- Linearity
- Independence
- Homoscedasticity
- Normality of residuals
- No multicollinearity (in multiple regression)

### 🔹 How is the coefficient β₁ interpreted?
- β₁ represents the expected change in the response variable for a one-unit increase in the predictor, holding other variables constant.

### 🔹 What is the difference between R² and adjusted R²?
- R² measures explained variance.
- Adjusted R² penalizes for adding non-informative predictors.

**💡 Tip:**  
In interviews, always mention that assumptions should be *checked*, not just assumed.

---

## 📌 2. Classification – Logistic Regression

### 🔹 Why can’t we use linear regression for classification?
- Predicted values are not bounded between 0 and 1.
- Linear regression doesn’t model probability well for binary outcomes.

### 🔹 What is the log-odds (logit)?
- `log(p / (1 - p))` where `p` is the predicted probability.
- Logistic regression models the log-odds as a linear function of predictors.

**💡 Tip:**  
Mention maximum likelihood estimation (MLE) when asked about model fitting.

---

## 📌 3. Resampling Methods

### 🔹 What is the purpose of cross-validation?
- To estimate model performance and prevent overfitting.
- Helps select tuning parameters (e.g., regularization strength in Ridge/Lasso).

### 🔹 Difference between LOOCV and k-fold CV?
- LOOCV: low bias, high variance.
- k-fold (e.g., k=5, 10): trade-off between bias and variance.

---

## 📌 4. Regularization – Ridge vs Lasso

| Method  | Penalty         | Shrinks Coefficients | Can Zero Out Features? |
|---------|------------------|----------------------|------------------------|
| Ridge   | L2 (sum of squares) | Yes                  | No                     |
| Lasso   | L1 (sum of abs)     | Yes                  | Yes (feature selection) |

**💡 Tip:**  
Lasso is often favored in high-dimensional settings (e.g., p >> n).

---

## 📌 5. Bias-Variance Tradeoff

### 🔹 Explain bias-variance tradeoff.
- High bias: underfitting
- High variance: overfitting
- Ideal model minimizes total test error (bias² + variance + irreducible error)

**Interview phrasing tip:**  
Say “the tradeoff governs the expected test error” and mention model complexity control.

---

## 📌 6. Decision Trees & Bagging

### 🔹 Why are trees prone to overfitting?
- Trees are very flexible and fit noise unless pruned.

### 🔹 What does bagging do?
- Reduces variance by averaging over bootstrapped models.

---

## 📌 7. Random Forests

### 🔹 How is Random Forest different from bagging?
- Adds randomness: at each split, only a subset of predictors is considered.

### 🔹 Variable importance?
- Mean decrease in impurity
- Mean decrease in accuracy (OOB score drop)

---

## 📌 8. Support Vector Machines (Optional)

### 🔹 What is the margin in SVM?
- Distance between the separating hyperplane and the closest points (support vectors).

### 🔹 What is the kernel trick?
- Projects data into higher dimensions without explicitly computing it.

---

## 📌 9. Model Evaluation Metrics

| Metric      | Type        | Use Case                                 |
|-------------|-------------|------------------------------------------|
| Accuracy    | Classification | When classes are balanced              |
| Precision   | Classification | When false positives are costly       |
| Recall      | Classification | When false negatives are costly       |
| F1 Score    | Classification | When precision/recall are both needed |
| RMSE / MAE  | Regression   | RMSE penalizes outliers more            |
| R²          | Regression   | Explains variance                       |

---

## 🧠 Final Tips for Interview

- Be able to explain *why* you use a method, not just how.
- Use visuals or metaphors if you're comfortable (e.g., “lasso squeezes small features to zero”).
- Always discuss assumptions, limitations, and when you would **not** use a method.

# Improving Predictive Models Using Feature Selection & Regularization (Smarket Case Study)

> Applied best subset selection, forward stepwise selection, cross-validation, and regularization techniques (LASSO, Ridge, Elastic Net, RFE) to improve and validate a regression model predicting S&P 500 daily returns.

**Author:** Amisha Farhana Shaik  
**Project Type:** Feature Selection | Model Validation | Regularization | Financial Modeling  

---

## Business Problem

In Case Study 3, we built a regression model to predict daily S&P 500 returns.

However:

- The model had low explanatory power.
- It was trained once without validation.
- Feature selection was not systematically evaluated.

Objective of this case:

- Improve the predictive model using feature selection techniques.
- Validate model performance via cross-validation.
- Compare regularization methods.
- Identify whether model refinement meaningfully improves performance.

Dataset: Smarket (2001–2005 daily returns) :contentReference[oaicite:1]{index=1}  

Train/Test Split:
- Training: 2004 and earlier
- Testing: 2005

---

# 1️⃣ Baseline Linear Regression

Model:
Today ~ Lag1 + Lag2 + Lag3 + Lag4 + Lag5 + Volume

Result (from Case 3):
- Test MSE ≈ 0.4175 :contentReference[oaicite:2]{index=2}

This serves as the benchmark.

---

# 2️⃣ Best Subset Selection

Method:
- Evaluate all possible combinations of predictors (2^p subsets).
- Select subset minimizing performance criterion (e.g., Cp, MSE).

Challenge:
Computationally intensive for many predictors.

Outcome:
Best model identified included:
['Lag5', 'Year_Day', 'Lag1', 'Lag2', 'Lag4', 'Volume', 'Lag3'] :contentReference[oaicite:3]{index=3}

However:

Best Model Test MSE ≈ 0.4196  
Slightly higher than baseline.

Conclusion:
Feature selection did not materially improve predictive performance.

---

# 3️⃣ Cp Statistic

Cp balances:
- Model fit
- Model complexity

Lower Cp = better balance between bias and variance :contentReference[oaicite:4]{index=4}

Used to guide subset selection.

---

# 4️⃣ Forward Stepwise Selection

Process:
- Start with no predictors.
- Add predictor that most reduces Cp.
- Stop when improvement becomes negligible.

This reduces computational cost compared to full subset search.

Result:
Model performance similar to full subset selection.

---

# 5️⃣ Cross-Validation

Applied k-fold cross-validation to evaluate generalization.

Cross-validated MSE values:
≈ 1.286 (varies slightly across subsets) :contentReference[oaicite:5]{index=5}

Key Insight:
Validation reveals that small differences in training error do not translate into real improvement.

Important takeaway:
Case 3 model was not validated.
Case 4 introduces proper validation, even if MSE increases slightly.

---

# 6️⃣ Regularization Methods

## LASSO Regression

- Performs variable selection by shrinking coefficients to zero.
- Encourages sparsity.

Result:
- MSE ≈ 0.42
- R² ≈ 0.00 :contentReference[oaicite:6]{index=6}

No meaningful improvement.

---

## Ridge Regression

- Shrinks coefficients but does not eliminate variables.
- Reduces variance.

Result:
- MSE ≈ 0.42
- R² ≈ 0.00 :contentReference[oaicite:7]{index=7}

Similar performance to baseline.

---

## Elastic Net

- Combines LASSO + Ridge penalties.
- Hyperparameters tuned via grid search.

Result:
- MSE ≈ 0.42
- R² ≈ 0.00 :contentReference[oaicite:8]{index=8}

Conclusion:
Regularization does not extract predictive signal from lagged returns.

---

# 7️⃣ Recursive Feature Elimination (RFE)

Method:
- Iteratively remove least important predictors.
- Refit model at each step.

Result:
Selected subset did not meaningfully improve MSE.

---

# Final Model Comparison

Case Study 3:
Test MSE = 0.4175  

Case Study 4 (validated best subset):
Test MSE = 0.4196 :contentReference[oaicite:9]{index=9}  

Interpretation:
Model complexity reduction does not improve predictive accuracy.
Daily stock returns remain largely unpredictable.

---

# Technical Workflow

Baseline Regression  
        ↓  
Best Subset Selection  
        ↓  
Cp Statistic Evaluation  
        ↓  
Forward Stepwise Selection  
        ↓  
Cross-Validation  
        ↓  
LASSO / Ridge / Elastic Net  
        ↓  
Recursive Feature Elimination  
        ↓  
Model Comparison  

---

## Technical Skills Demonstrated

- Best Subset Selection
- Cp Statistic
- Forward Stepwise Selection
- Cross-Validation
- Bias-Variance Tradeoff
- LASSO Regularization
- Ridge Regression
- Elastic Net
- Hyperparameter Tuning
- Recursive Feature Elimination
- Financial Return Modeling
- Validation-Based Model Comparison

---

## Business Insight

- Historical lagged returns provide minimal predictive power.
- Increasing model complexity does not overcome market randomness.
- Validation is critical — small training improvements often fail out-of-sample.
- Regularization confirms lack of strong predictive structure.
- Efficient markets hypothesis is supported in this dataset.

---

## Why This Case Study Matters

This project demonstrates:

- Systematic model refinement
- Proper validation methodology
- Understanding of regularization tradeoffs
- Avoiding overfitting
- Realistic interpretation of financial predictability limits

This reflects mature modeling discipline — knowing when improvement is not possible.

---

## Applications

Financial Modeling | Feature Selection | Model Validation | Regularization | Quantitative Finance | Predictive Analytics

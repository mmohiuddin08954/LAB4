# MSCS-634 Lab 4: Regression Analysis with Regularization Techniques

## Purpose
This lab explores multiple regression approaches on the **Diabetes dataset** from `sklearn.datasets` to predict disease progression from baseline health measurements. The goal is to compare Simple Linear Regression, Multiple Regression, and Polynomial Regression, and to evaluate how **Ridge** and **Lasso** regularization help control overfitting as model complexity increases. All models are evaluated using MAE, MSE, RMSE, and R².

## Key Insights
- **Multiple features outperform a single feature.** Multiple Regression (using all 10 health measurements) achieved a substantially higher R² than Simple Linear Regression using only BMI, confirming that disease progression depends on a combination of factors.
- **Polynomial regression shows clear overfitting at higher degrees.** As the polynomial degree increased, training R² kept rising while test R² plateaued and then declined — the classic overfitting signature.
- **Regularization controls overfitting.** Both Ridge and Lasso recovered generalization performance on the expanded polynomial feature set. Ridge shrinks coefficients smoothly, while Lasso can zero out coefficients entirely, performing automatic feature selection.
- **BMI and the `s5` serum measurement** were consistently the strongest predictors of disease progression across every model tested.
- **Alpha (regularization strength) matters.** Very small alpha values behave close to ordinary regression (risk of overfitting), while very large alpha values over-penalize the model and cause underfitting. A moderate alpha balanced bias and variance best in this dataset.

## Challenges and Decisions
- **Choosing a baseline feature:** BMI was selected for the Simple Linear Regression step based on its strong correlation with the target variable, identified via a correlation heatmap in the data exploration phase.
- **Polynomial degree selection:** Degrees 1–4 were tested to clearly illustrate the overfitting trend; degree 2 was carried forward into the regularization comparison as a reasonable middle ground between underfitting and severe overfitting.
- **Alpha range for Ridge/Lasso:** A log-scaled range of alpha values (0.01 to 100) was used to show the full spectrum of regularization effects, from near-unregularized to heavily penalized models.
- **Lasso convergence:** Lasso required an increased `max_iter` (10,000) to reliably converge on the expanded polynomial feature set without convergence warnings.

## Repository Contents
- `Lab4_Regression_Regularization.ipynb` — Jupyter Notebook containing all analysis, models, and visualizations.
- `README.md` — This file.

## How to Run
1. Clone the repository.
2. Install dependencies: `pip install numpy pandas matplotlib seaborn scikit-learn`
3. Open and run `Lab4_Regression_Regularization.ipynb` in Jupyter Notebook or JupyterLab.

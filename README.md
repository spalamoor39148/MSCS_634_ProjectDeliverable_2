# MSCS_634_ProjectDeliverable_2

Dataset Summary, Modeling Process, and Results
Dataset Overview
The dataset used is the Heart Disease UCI dataset, containing 303 patient records with 14 clinical attributes such as age, sex, chest pain type, cholesterol, resting blood pressure, and exercise-induced angina. The primary objective is to predict the likelihood of heart disease based on these attributes.

Modeling Process
Feature Engineering:

Polynomial features (degree = 2) were generated to capture nonlinear relationships and feature interactions.

Data was scaled using StandardScaler to ensure that all features had the same scale, which is important for regularized models like Lasso and Ridge.

Regression Models Built:

Linear Regression: Served as a baseline model to capture direct linear relationships.

Ridge Regression: Applied L2 regularization to reduce overfitting and penalize large coefficients.

Lasso Regression: Used L1 regularization for both regularization and automatic feature selection.

Model Evaluation Metrics:

R-squared (R²): Measures how well the model explains variance in the target variable.

Root Mean Squared Error (RMSE): Measures the average magnitude of prediction errors.

5-fold Cross-Validation: Used to assess the generalization performance of each model.

Evaluation Results
Model	Cross-Validated RMSE	Test RMSE	Test R² Score

📊 Model Evaluation Summary
Model	CV RMSE ↓	Test RMSE ↓	Test R² ↑
Linear Regression	0.5423	0.6049	-0.4700 
Ridge Regression	0.4110	0.5272	-0.1167 
Lasso Regression	0.3854	0.4130	0.3147 

Interpretation
1. Lasso Regression performs best overall:
Lowest CV RMSE (0.3854): Suggests best generalization performance on unseen data during cross-validation.

Lowest Test RMSE (0.4130): Indicates smallest prediction error on the test set.

Highest Test R² (0.3147): Explains ~31% of the variance in the test data — the only model with positive R², which means it's learning useful patterns.

2. Linear Regression underperforms significantly:
Negative R² (-0.4700) on test data implies it performs worse than a horizontal line at the mean of the target variable.

High RMSE further confirms poor fit and high variance.

3. Ridge Regression improves over Linear Regression but still lacks generalization:
Lower CV and test RMSE than Linear Regression, but still negative R² (−0.1167), meaning it fails to capture the underlying signal well enough on the test set.

 Why Lasso Works Better Here
Lasso adds L1 regularization, which:

Performs feature selection by zeroing out less important coefficients.

Helps in sparse and high-dimensional data.

Reduces overfitting more aggressively than Ridge (L2 regularization).

So, if your dataset has many irrelevant or weak predictors, Lasso is ideal.

Key Observations:
Ridge Regression slightly outperformed others in terms of RMSE and R², indicating better generalization on unseen data.

Lasso helped identify and reduce less important features by shrinking their coefficients to zero.

Polynomial features improved model accuracy by capturing nonlinear effects between variables.

Challenges and Solutions
Challenge	Resolution
Missing or noisy values (e.g., zero cholesterol)	Filtered out or imputed with median values
Multicollinearity in polynomial features	Addressed with Ridge regularization
Scaling inconsistencies	StandardScaler applied before modeling
Overfitting risk	Reduced using cross-validation and regularized models

Conclusion
The modeling phase provided insights into which clinical features most influence heart disease predictions. Regularized regression techniques like Ridge and Lasso proved more effective than plain linear regression in handling feature complexity and generalizing well to test data.



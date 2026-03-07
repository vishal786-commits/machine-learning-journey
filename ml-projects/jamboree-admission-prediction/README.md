# Jamboree Admission Prediction

## Overview

This project analyzes factors influencing graduate school admissions and builds a Linear Regression model to predict a student's probability of admission.

The goal is to provide data-driven insights that can help students understand which factors most strongly impact their admission chances.

---

## Objective

- Analyze relationships between academic and profile features.
- Build an interpretable Linear Regression model.
- Validate regression assumptions.
- Evaluate model performance using MAE, RMSE, and R².
- Provide actionable insights.

---

## Dataset

The dataset contains information about:

- GRE Score
- TOEFL Score
- University Rating
- SOP
- LOR
- CGPA
- Research
- Chance of Admit (Target Variable)

Dataset source (publicly shared for educational use):
https://drive.google.com/uc?id=1zO1ttneqKZbIBf9N5dcJ5XWYWWFcA5HV

Note: The dataset is used for educational purposes. Licensing belongs to the original source.

---

## Why Statsmodels Instead of Scikit-learn?

Statsmodels was used because this project focuses on statistical interpretation, not just prediction.

Statsmodels provides:
- p-values
- Confidence intervals
- Detailed regression summary
- Statistical significance of variables

This allows us to understand which factors truly influence admission probability, rather than only measuring predictive accuracy.

---

## Techniques Used

- Exploratory Data Analysis (EDA)
- Correlation analysis
- Multicollinearity check (VIF)
- Assumption testing (Linearity, Homoscedasticity, Normality)
- Linear Regression (Statsmodels)
- Model evaluation (MAE, RMSE, R²)

---

## Results

- R²: 0.855
- Adjusted R²: 0.847
- MAE: 0.043
- RMSE: 0.060

The model explains approximately 85% of the variation in admission probability and shows low prediction error.

---

## Key Insights

- CGPA is the strongest predictor of admission probability.
- GRE and TOEFL scores significantly impact admission chances.
- Research experience and strong LOR improve competitiveness.
- Academic performance plays a larger role than subjective components.

---

## Author

Vishal Gopalkrishna  
Machine Learning Journey Project

# Machine Learning Foundations: Regression, Feature Selection & Classification

---

## 1. Fundamentals of Supervised Learning

Supervised learning focuses on building models that map input features ($X$) to a target output ($Y$).

### Train / Test Split
To evaluate model performance on unseen data and prevent overfitting:
* **Training Data (80%):** Used by the model to learn parameters (e.g., weights or coefficients).
* **Testing Data (20%):** Kept separate to evaluate the model's accuracy on unseen samples using metrics like $R^2$ (Coefficient of Determination) or MSE (Mean Squared Error).

### Key Terminology
* **Feature Space ($X$):** The set of all input variables used for prediction ($X = \{x_1, x_2, x_3, \dots, x_n\}$).
* **Target Variable ($Y$):** The variable/outcome we aim to predict.

---

## 2. Regression Analysis

### Overview
* **Goal:** Predict a continuous target variable $Y$ based on features $X$.
* **Core Question:** *"How does each feature contribute to the predicted target value?"*

### Linear Regression Equation
$$\hat{Y} = b_0 + b_1 x_1 + b_2 x_2 + b_3 x_3 + \dots + b_n x_n$$

Where:
* $\hat{Y}$ = Predicted continuous value (e.g., Predicted Price).
* $b_0$ = **Intercept** (the baseline value when all features are 0).
* $b_1, b_2, b_3, \dots, b_n$ = **Coefficients / Weights** indicating the effect of each corresponding feature ($x_1, x_2, x_3$) on $Y$.

---

## 3. Real-World Housing Dataset Example

| # Sinks ($x_1$) | Sq Ft ($x_2$) | # Bathrooms ($x_3$) | # Bedrooms ($x_4$) | Price ($Y$) |
| :---: | :---: | :---: | :---: | :---: |
| 2 | 200 | 1 | 1 | $300,000 |
| 5 | 450 | 2 | 1 | $500,000 |
| 4 | 1,000 | 3 | 3 | $1,500,000 |

### Prediction Model Example
$$\text{Predicted Price} = b_0 + b_1(\text{Sinks}) + b_2(\text{SqFt}) + b_3(\text{Bathrooms})$$

---

## 4. Feature Selection & Multicollinearity

### Selection Goals
1. **Maximize target correlation:** Select features ($x_i$) that strongly correlate with $Y$.
2. **Minimize feature redundancy:** Avoid features that are highly correlated with each other (**multicollinearity**).

### Correlation Matrix Analysis

| Feature / Target | $x_1$ | $x_2$ | $x_3$ | $Y$ |
| :--- | :---: | :---: | :---: | :---: |
| **$x_1$** | 1.00 | 0.20 | 0.70 | **0.70** |
| **$x_2$** | 0.20 | 1.00 | 0.30 | **0.10** |
| **$x_3$** | 0.70 | 0.30 | 1.00 | **0.65** |
| **$Y$** | **0.70** | **0.10** | **0.65** | 1.00 |

#### Insights & Feature Recommendations:
* **$x_1$ and $Y$ ($r = 0.70$):** Strong positive correlation with $Y$. Highly useful for prediction.
* **$x_3$ and $Y$ ($r = 0.65$):** Strong positive correlation with $Y$.
* **Multicollinearity Issue ($x_1$ vs $x_3$, $r = 0.70$):** $x_1$ and $x_3$ are strongly correlated with each other, meaning they convey redundant information.
* **$x_2$ and $Y$ ($r = 0.10$):** Very weak correlation with $Y$. Provides little predictive power on its own.

---

## 5. Classification vs. Regression

| Metric / Aspect | Regression | Classification |
| :--- | :--- | :--- |
| **Output Type** | Continuous numerical value | Discrete class / categorical label |
| **Target Examples** | House prices, temperature, stock price | Spam/Not Spam, House Tier (Low/Med/High) |
| **Primary Goal** | Estimate a numerical quantity | Group data into distinct categories |
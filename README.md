# Cross-Sectional Returns in the Chinese Stock Market: Rank-Based Regression Analysis

## Project Overview
This project analyzes the cross-sectional variation of stock returns in the Chinese A-share market using a rank-based regression framework.

The goal is to evaluate whether firm characteristics such as size, book-to-market ratio, leverage, momentum, and growth variables can explain differences in monthly excess returns.

This project focuses on **relative ranking across firms**, rather than absolute values, to improve robustness and comparability.

---

## Dataset
- **Source:** CSMAR (China Stock Market & Accounting Research)
- **Time Range:** January 2010 – December 2022
- **Target Variable:** Monthly excess return (stock return minus market return)

### Data Processing
- Merged stock return data with financial statement variables  
- Removed missing or invalid observations  
- Lagged financial variables to avoid look-ahead bias  

**Note:**  
The original dataset is large and cannot be fully uploaded to GitHub.  
The provided CSV file is a **processed dataset used for modeling**.

---

## Feature Engineering

### Rank Transformation
All explanatory variables were transformed into **percentile ranks within each month**.

### Why ranking?
- Standardizes variables onto a common scale (0–1)  
- Reduces sensitivity to outliers  
- Improves cross-sectional comparability  
- Focuses on relative firm positioning  

### Ranked Features
- Rank_Size  
- Rank_BM  
- Rank_OpLev  
- Rank_FinLev  
- Rank_Mom  
- Rank_Rev  
- Rank_AG  

---

## Methodology

### Model
- **Multiple Linear Regression (OLS)**  
- **HC1 robust standard errors**

### Train-Test Split
- 80% training set  
- 20% testing set  

### Variable Selection
A two-step process was used:

1. **VIF (Variance Inflation Factor)**  
   - Identified multicollinearity issues  

2. **Backward Elimination using BIC**  
   - Removed redundant variables  
   - Improved model interpretability  

---

## Final Model

The final model includes the following predictors:

- Rank_Size  
- Rank_BM  
- Rank_OpLev  
- Rank_FinLev  
- Rank_Mom  
- Rank_Rev  
- Rank_AG  

---

## Key Results

- **Momentum** is the strongest positive predictor of returns  
- **Revenue growth** also shows strong predictive power  
- **Book-to-market and reversal-related effects** show negative relationships  
- **Size** has a moderate positive contribution  

### Model Performance
- **Adjusted R² ≈ 0.05**  
- **Train RMSE:** 0.1418  
- **Test RMSE:** 0.1421  

The close train/test RMSE suggests the model generalizes well and does not exhibit overfitting.

---

## Sensitivity Analysis
- Linear model allows direct interpretation of coefficients  
- Momentum produces the largest change in predicted returns  
- Indicates strong economic importance among factors  

---

## Limitations
- Linear model may miss nonlinear relationships  
- Ranking compresses magnitude differences  
- Low R² reflects inherent noise in stock return data  

---

## Future Improvements
- Add industry fixed effects  
- Incorporate nonlinear models  
- Explore interaction terms  
- Test performance across different market regimes  

---

## Project Structure

The repository is organized as follows:

```text
chinese-stock-return-regression/
│
├── chinese_stock_rank_regression.ipynb   # Main regression analysis
├── chinese_stock_model_data.csv          # Processed dataset used for modeling
├── chinese_stock_return_regression_slides.pptx  # Project presentation
└── README.md
```

---

## Tools & Libraries
- Python  
- pandas  
- statsmodels  
- scikit-learn  
- matplotlib  
- seaborn  

---

## Author
Yunelle Teng  
Applied Data Science @ University of Chicago

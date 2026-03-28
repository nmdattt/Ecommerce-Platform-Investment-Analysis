# Ecommerce Platform Investment Analysis Project

## Overview
This project analyzes customer behavior from the `Ecommerce_Customers.csv` dataset to determine whether the company should prioritize investment in mobile app or website development.

Using Python, the analysis covers data cleaning, exploratory data analysis (EDA), statistical testing, linear modeling, GAM modeling, feature selection, and cross-validation to uncover which platform (App vs. Website) contributes more to customer spending.

The final conclusion is based on validated statistical evidence and multiple regression models.

## Dataset
The dataset includes 1,000 observations with variables such as:

* `Time_on_App`
* `Time_on_Website`
* `Time_on_Membership`
* `Length_of_Membership`
* `Avg_Session_Length`
* `Yearly_Amount_Spent`

The dataset represents customer engagement and spending patterns for an online retail business.

## Data Cleaning & Preprocessing
Data cleaning was performed using `tidyverse`, `janitor`, `VIM`, and custom preprocessing steps in Python.

### 1. Standardized & validated data
* Renamed all variables using `clean_names()`
* Checked structure (`str()`), summaries, and missing patterns
* Used `VIM::aggr()` to verify missingness and ensure data completeness

### 2. Outlier & distribution analysis
* Visualized outliers using boxplots & histograms
* Checked skewness/kurtosis
* Verified linearity assumptions for regression

### 3. Multicollinearity & correlation
* Built correlation matrices and pairwise scatterplots
* Identified relationships between Website/App usage and spending
* Confirmed moderate correlation between `time_on_app` and `yearly_amount_spent`

## Exploratory Data Analysis (EDA)
EDA was performed using `ggplot2`, smoothing functions, and grouped visualizations.

### Key questions explored
* Do customers spend more time on the website or on the mobile app?
* Is engagement different across membership duration?
* Which time variable correlates more strongly with spending?
* Does the platform usage show linear or nonlinear patterns?

### Visualizations produced
* Boxplots comparing Website vs App time
* GAM smoothing curves of `Spending ~ Time_on_App` and `Spending ~ Time_on_Website`
* Scatterplots with trendlines
* Distribution analysis of key numerical variables

## EDA Findings
* Customers spend slightly more time on the mobile app than on the website.
* Membership duration strongly influences spending behavior.
* Time on App shows a clearer, more consistent upward trend with spending.
* Website engagement is flatter and less predictive.

## Modeling & Statistical Analysis
The predictive modeling phase was implemented using Python's scikit-learn to build, train, and evaluate a Multiple Linear Regression model.

### 1. Data Splitting & Model Training
* Split the dataset into training and testing sets (`train_test_split`) to ensure objective evaluation on unseen data.
* Built a Linear Regression model using features including `Time_on_App`, `Time_on_Website`, `Length_of_Membership`, and `Avg_Session_Length`.
* Checked model assumptions by visualizing the normal distribution of residuals using `seaborn`.

**Result**:
* `Time_on_App` is a statistically significant feature and strongly predictive of customer spending.
* `Time_on_Website` has minimal impact on the model's predictive power.

### 2. Coefficients Analysis (Feature Impact)
* Extracted the model's coefficients to quantify the exact business impact of each platform.

**Result**:
* The model mathematically proves the superiority of the mobile app: a one-unit increase in `Time_on_App` is associated with an increase of $38.59 in `Yearly_Amount_Spent`, whereas a one-unit increase in `Time_on_Website` only yields an increase of $0.19.

### 3. Model Evaluation
* Evaluated the model's performance on the test data to verify its reliability.
* Calculated standard regression metrics: Mean Absolute Error (MAE), Mean Squared Error (MSE), Root Mean Squared Error (RMSE), and Explained Variance Score (R²).

**Result**:
* The model achieved a very high R² score (approx. 98%), confirming that the selected features (especially `Time_on_App` and `Length_of_Membership`) reliably and accurately explain the variance in customer spending.

## Final Conclusion
Across all analyses — EDA, hypothesis testing, linear regression, GAM, and cross-validation:

**Time spent on the Mobile App is a significantly stronger driver of Yearly Amount Spent than time on the Website.**

## Business Recommendation
* Prioritize mobile app development, including UI/UX enhancements and engagement features.
* Website should be maintained but not considered the primary revenue driver.
* Encourage customers to migrate to or increase activity on the mobile app for higher spending potential.

## Tools & Libraries Used
* `pandas` (Data manipulation, cleaning, and handling missing data)
* `numpy` (Numerical computations and array operations)
* `matplotlib` & `seaborn` (Exploratory data analysis and statistical visualization)
* `scikit-learn` (Machine learning: Linear Regression modeling, cross-validation, and model evaluation)

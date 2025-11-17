# Ecommerce Platform Investment Analysis – R Project

## Overview
This project analyzes customer behavior from the `Ecommerce_Customers.csv` dataset to determine whether the company should prioritize investment in mobile app or website development.

Using R, the analysis covers data cleaning, exploratory data analysis (EDA), statistical testing, linear modeling, GAM modeling, feature selection, and cross-validation to uncover which platform (App vs. Website) contributes more to customer spending.

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
Data cleaning was performed using `tidyverse`, `janitor`, `VIM`, and custom preprocessing steps in R.

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
Multiple modeling approaches were implemented using `leaps`, `mgcv`, `caret`, and base R methods.

### 1. Linear Model (LM)
* Built several linear regression models:
    * Full model with all predictors
    * Reduced models using variable selection
* Checked model assumptions (linearity, normality, VIF, residual patterns)

**Result:**
* `Time_on_App` is statistically significant and strongly predictive of spending.
* `Time_on_Website` is weaker and often not significant.

### 2. Best Subset Selection (`leaps`)
* Explored multiple predictor combinations.
* Compared models via Adjusted R², Cp, BIC
* Selected the most efficient model

**Result:**
Topology of best models consistently includes:
* `Time_on_App`
* `Length_of_Membership`
* `Time_on_Website` (frequently excluded)

### 3. Generalized Additive Model (GAM)
* Used `mgcv` and `mgcViz` to capture nonlinear trends.
* Fitted GAM with smooth terms `s(Time_on_App)`
* Checked visualization & significance of smoothing terms

**Result:**
* `Time_on_App` shows a strong nonlinear positive effect on spending.
* `Time_on_Website` remained nearly flat.

### 4. Cross-validation (`caret`)
* Performed K-fold CV to evaluate model performance.
* Metrics: RMSE, MAE, R²
* Compared LM vs GAM vs Best Subset models

**Result:**
Models containing `Time_on_App` consistently outperform others.

## Final Conclusion
Across all analyses — EDA, hypothesis testing, linear regression, GAM, and cross-validation:

**Time spent on the Mobile App is a significantly stronger driver of Yearly Amount Spent than time on the Website.**

## Business Recommendation
* Prioritize mobile app development, including UI/UX enhancements and engagement features.
* Website should be maintained but not considered the primary revenue driver.
* Encourage customers to migrate to or increase activity on the mobile app for higher spending potential.

## Tools & Libraries Used
* `tidyverse` (data cleaning, transformation)
* `janitor` (variable standardization)
* `VIM` (missing data analysis)
* `ggplot2` (visualization)
* `leaps` (best subset modeling)
* `mgcv`, `mgcViz` (GAM modeling)
* `caret` (cross-validation & model evaluation)

# Ecommerce Platform Investment Analysis Project

## Overview
This project analyzes customer behavior from the `Ecommerce_Customers.csv` dataset to determine whether the company should prioritize investment in mobile app or website development.

Using Python, the analysis covers data cleaning, exploratory data analysis (EDA), and Multiple Linear Regression modeling to uncover which platform (App vs. Website) contributes more to customer spending.

The final conclusion is based on validated statistical evidence and coefficient analysis.

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
Data cleaning and preprocessing were performed using Python's pandas and numpy libraries.

### 1. Standardized & validated data
* Checked dataframe structure using `.info()` and `.describe()` to understand data types and summary statistics.
* Verified missingness and ensured data completeness using `.isnull()`.

2. Outlier & distribution analysis
* Visualized data distributions using histograms and distplots.
* Verified linearity assumptions for regression modeling.

3. Multicollinearity & correlation
* Built correlation matrices and pairwise scatterplots (`sns.pairplot`).
* Confirmed a strong relationship between `Length_of_Membership` and `Yearly_Amount_Spent`.
* Identified a moderate correlation between `Time_on_App` and `Yearly_Amount_Spent`.

## Exploratory Data Analysis (EDA)
EDA was performed using `seaborn` and `matplotlib` to visualize relationships and distributions.

### Key questions explored:
* Do customers spend more time on the website or on the mobile app?
* Which time variable correlates more strongly with spending?
* What is the relationship between membership duration and yearly amount spent?

### Visualizations produced:
* Jointplots (scatter and hex bin) comparing Website/App time vs. Yearly Amount Spent.
* Pairwise relationship visualizations across the entire dataset to spot overarching trends.
* Linear trend plots (`sns.lmplot`) mapping `Yearly_Amount_Spent` against `Length_of_Membership` and `Time_on_App`.

## EDA Findings
* `Length_of_Membership` is the strongest predictor of spending behavior.
* `Time_on_App` shows a clearer, more consistent upward linear trend with spending.
* `Time_on_Website` engagement is much flatter and shows almost no correlation with yearly spending.

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
Across all analyses — Exploratory Data Analysis and Multiple Linear Regression:

**Time spent on the Mobile App is a significantly stronger driver of Yearly Amount Spent than time on the Website**. (Holding all other features fixed, a 1-unit increase in Time on App is associated with an increase of **$38.59**, compared to only **$0.19** for Time on Website).

## Business Recommendation
* Prioritize mobile app development, including UI/UX enhancements and engagement features.
* Website should be maintained but not considered the primary revenue driver.
* Encourage customers to migrate to or increase activity on the mobile app for higher spending potential.

## Tools & Libraries Used
* `pandas` (Data manipulation, cleaning, and handling missing data)
* `numpy` (Numerical computations and array operations)
* `matplotlib` & `seaborn` (Exploratory data analysis and statistical visualization)
* `scikit-learn` (Machine learning: Linear Regression modeling, cross-validation, and model evaluation)

# Housing Price Prediction - Senior Statistics Capstone

## Project Overview
This project represents the culmination of my undergraduate statistics degree as the final project for my senior capstone (STT 481). The objective was to utilize various regression and machine learning techniques to accurately predict house prices using a dataset containing 23 numeric explanatory variables.

The project explores the trade-off between model interpretability (e.g., Linear Regression) and flexibility (e.g., Gradient Boosting), ultimately determining which methods yield the lowest test error on unseen data.

## Dataset
The dataset consists of housing data split into training and testing sets. It includes:
* **Response Variable:** Sale Price.
* **Features:** 23 numeric variables describing property characteristics, such as `LotArea`, `OverallQual`, `YearBuilt`, and various surface area metrics (e.g., `BsmtFinSF2`, `GarageArea`).
* **Data Processing:** Transformations were applied to the response variable (log-transformation) to correct non-normality observed in Q-Q plots.

## Methodologies Implemented
I implemented and compared nine different statistical learning methods to minimize the Cross-Validation (CV) error:

### 1. Parametric & Non-Parametric Regression
* **K-Nearest Neighbors (KNN):** Utilized $K=4$ based on LOOCV MSE.
* **Linear Regression (OLS):** Optimized by removing insignificant variables (e.g., `BsmtFinSF2`, `LowQualFinSF`).
* **Best Subset Selection:** Used BIC to select the simplest model with the best fit, identifying 19 key variables.
* **Generalized Additive Models (GAM):** Fitted to capture non-linear relationships.

### 2. Shrinkage Methods
* **Ridge Regression:** Tuning parameter $\lambda$ chosen via 10-fold cross-validation.
* **Lasso Regression:** Performed variable selection, shrinking several coefficients to zero.

### 3. Tree-Based Methods
* **Decision Trees:** Pruned using cross-validation to prevent overfitting.
* **Bagging:** Utilized `mtry=23` (all predictors).
* **Random Forest:** Utilized `mtry=5` (approx. $\sqrt{p}$) to decorrelate trees.
* **Gradient Boosting:** Optimized with 5000 trees, interaction depth of 4, and shrinkage of 0.01.

## Key Findings & Results
* **Model Performance:** Gradient Boosting achieved the lowest Kaggle score (0.13909), outperforming all other models.
* **Feature Importance:** Across tree-based methods, `OverallQual` (Overall Quality) was consistently identified as the most influential predictor of sale price.
* **Interpretability vs. Accuracy:** The project demonstrated that while linear models offered clear coefficient interpretability, ensemble methods like Boosting and Random Forest provided superior predictive power by capturing complex non-linearities.

## Technologies & Libraries
* **Language:** R
* **Key Libraries:** `glmnet` (Ridge/Lasso), `randomForest`, `gbm` (Boosting), `tree`, `leaps` (Subset Selection), `FNN` (KNN), `boot`, `DAAG`.

## Author
**Nikhil Bhandarkar**
*Statistics Capstone Project (STT 481)*
*Date: March 2022*

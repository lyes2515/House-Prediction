# House Prices Prediction - End-to-End Machine Learning Project

## Project Overview
This project aims to predict house prices using the famous **Ames Housing dataset** from Kaggle.  
It follows a complete machine learning pipeline: data loading, exploratory data analysis, cleaning, feature engineering, model training, evaluation, and Kaggle submission.

**Final Kaggle Public Score:** `0.13102` (RMSLE)

---

## Dataset
- **Source:** [House Prices - Advanced Regression Techniques](https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques)
- **Files used:**
  - `train.csv` (1460 houses)
  - `test.csv` (1459 houses)

---

## Project Pipeline

1. **Data Loading & Initial Exploration**
   - Loaded the data and inspected shape, data types, and basic statistics.

2. **Exploratory Data Analysis (EDA)**
   - Analyzed missing values
   - Created correlation heatmap with `SalePrice`
   - Visualized key features (`GrLivArea`, `OverallQual`, `YearBuilt`, etc.)

3. **Data Cleaning**
   - Dropped columns with very high missing percentage (`PoolQC`, `MiscFeature`, `Alley`, `Fence`)
   - Imputed missing values:
     - Categorical features → `"None"`
     - Numerical features → median or logical values

4. **Feature Encoding**
   - Applied One-Hot Encoding on all categorical features using `pd.get_dummies(drop_first=True)`

5. **Modeling**
   Models trained and evaluated:
   | Model                        | Test RMSE   | Test R²   |
   |-----------------------------|-------------|-----------|
   | Linear Regression           | 52,522      | 0.640     |
   | Random Forest (Tuned)       | 28,701      | 0.893     |
   | Gradient Boosting           | 26,345      | 0.9095    |
   | XGBoost                     | 26,280      | 0.9100    |
   | **Tuned XGBoost (Best)**    | **25,475**  | **0.9154**|

6. **Feature Engineering**
   - Created new features: `TotalSF`, `TotalBath`, `HouseAge`, `RemodAge`
   - Performed feature selection based on XGBoost feature importance

7. **Final Model**
   - Best model: **Tuned XGBoost**
   - Hyperparameters:

8. **Kaggle Submission**
- Applied the same preprocessing pipeline to the test set
- Generated `submission.csv`
- **Public Score: 0.13102**

---

## Key Takeaways

- Tree-based models (especially XGBoost and Gradient Boosting) significantly outperformed Linear Regression.
- Proper missing value handling and consistent preprocessing between train and test sets are critical.
- Feature engineering helped slightly, but careful feature selection was more important.
- Hyperparameter tuning provided a noticeable performance boost.

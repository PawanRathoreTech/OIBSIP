# House Price Prediction Using Machine Learning

## 1. Project Overview

The objective of this project is to predict house sale prices using Machine Learning regression techniques.

The project uses the Ames Housing Dataset, which contains information about residential properties, including house quality, living area, garage capacity, basement area, construction year, neighborhood, and other property characteristics.

Two regression models were developed and evaluated:
- Linear Regression
- Ridge Regression

The main objective was to understand how different house features influence property prices and compare the predictive performance of both models.

## 2. Dataset Information

**Dataset:** House Prices - Advanced Regression Techniques  
**Source:** Kaggle  
**Total Records:** 1,460  
**Total Columns:** 81  
**Target Variable:** SalePrice

The dataset contains both numerical and categorical features.

Examples of numerical features:
- OverallQual
- GrLivArea
- GarageCars
- GarageArea
- TotalBsmtSF
- YearBuilt

Examples of categorical features:
- Neighborhood
- HouseStyle
- GarageType
- Exterior1st
- MSZoning

## 3. Tools and Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook

## 4. Project Workflow

### Step 1: Data Loading and Inspection

The dataset was loaded using Pandas.

Initial inspection was performed using:
- `head()`
- `shape`
- `info()`
- `isnull().sum()`

The dataset contained 1,460 rows and 81 columns.

### Step 2: Exploratory Data Analysis (EDA)

Descriptive statistics were calculated for the target variable, SalePrice.

Key statistics:

| Statistic | Value |
|---|---:|
| Mean | 180,921.20 |
| Median | 163,000 |
| Standard Deviation | 79,442.50 |
| Minimum | 34,900 |
| Maximum | 755,000 |

A histogram with a KDE curve was created to understand the distribution of house prices.

**Observation:** Most houses have sale prices concentrated between approximately 100,000 and 200,000. The distribution is positively skewed, with a smaller number of expensive houses forming a long right tail.

### Step 3: Missing Value Handling

Missing values were identified and handled in a separate cleaned dataset copy named `df_model`.

Different approaches were used depending on the feature:
- Missing categorical values representing the absence of a property feature were replaced with `None`.
- Missing LotFrontage values were filled using the median.
- Other missing numerical and categorical values were handled according to their meaning.

The cleaned dataset was checked again to confirm that no missing values remained.

### Step 4: Correlation Analysis

A correlation matrix was calculated for numerical features and visualized using a heatmap.

The features showing the strongest positive correlations with SalePrice included:

| Feature | Correlation |
|---|---:|
| OverallQual | 0.7910 |
| GrLivArea | 0.7086 |
| GarageCars | 0.6404 |
| GarageArea | 0.6234 |
| TotalBsmtSF | 0.6136 |
| 1stFlrSF | 0.6059 |
| FullBath | 0.5607 |
| YearBuilt | 0.5229 |

**Observation:** OverallQual and GrLivArea showed the strongest positive relationships with house sale prices among the numerical features.

### Step 5: Feature Selection

Eight numerical features were initially selected based on their correlation with SalePrice:

1. OverallQual
2. GrLivArea
3. GarageCars
4. GarageArea
5. TotalBsmtSF
6. 1stFlrSF
7. FullBath
8. YearBuilt

For the final prediction model, all 79 predictor features were included, consisting of numerical and categorical features. The Id column was excluded because it is an identification field.

### Step 6: Data Preprocessing and One-Hot Encoding

Categorical and numerical features were identified separately.

One-Hot Encoding was applied to categorical features using Scikit-learn's `OneHotEncoder`.

A `ColumnTransformer` was used to:
- Encode categorical features.
- Pass numerical features through without modification.

The encoder was fitted on training data and applied to testing data to avoid data leakage.

After encoding:
- Training data: 1,168 rows × 300 features
- Testing data: 292 rows × 300 features

### Step 7: Train-Test Split

The dataset was divided into:
- 80% training data
- 20% testing data

| Dataset | Records |
|---|---:|
| Training | 1,168 |
| Testing | 292 |

The split was performed using Scikit-learn's `train_test_split` with `random_state=42`.

### Step 8: Linear Regression Model

A Linear Regression model was created using Scikit-learn.

The model was trained on the encoded training dataset and used to predict house prices for the testing dataset.

### Step 9: Model Evaluation

The model was evaluated using three regression metrics:

- Mean Squared Error (MSE)
- Root Mean Squared Error (RMSE)
- R² Score

**Linear Regression Results:**

| Metric | Result |
|---|---:|
| MSE | 965,597,173.76 |
| RMSE | 31,074.06 |
| R² Score | 0.8741 |

The R² score indicates that the model explains approximately 87.41% of the variation in house sale prices on the test dataset.

### Step 10: Actual vs Predicted Prices

A scatter plot was created to compare actual house prices with predicted prices.

**Observation:** The points show a strong relationship between actual and predicted prices. However, some predictions, particularly for expensive houses, differ noticeably from actual prices.

### Step 11: Residual Analysis

Residuals were calculated as:

`Residual = Actual Price - Predicted Price`

A residual plot was created to examine prediction errors.

**Observation:** Most residuals are distributed around the zero line. However, the spread of residuals increases for higher predicted prices, indicating larger errors for some expensive properties.

### Step 12: Coefficient Analysis

Model coefficients were analyzed to identify features with positive and negative contributions to predicted house prices.

Some of the highest positive coefficients included:
- Neighborhood_NoRidge
- Neighborhood_StoneBr
- Neighborhood_NridgHt
- Exterior1st_BrkFace
- BsmtQual_Ex

Some of the negative coefficients included:
- Condition2_PosN
- Neighborhood_Mitchel
- PoolQC_Gd
- LandContour_Bnk
- RoofMatl_ClyTile

Categorical coefficients represent differences relative to their reference categories.

### Step 13: Ridge Regression (Bonus)

Ridge Regression was implemented as an additional model for comparison.

A Pipeline was created using:
- StandardScaler with `with_mean=False`
- Ridge Regression with `alpha=1.0`

The Ridge model was trained and evaluated using the same training and testing datasets.

**Ridge Regression Results:**

| Metric | Result |
|---|---:|
| MSE | 883,964,425.43 |
| RMSE | 29,731.54 |
| R² Score | 0.8848 |

## 5. Final Model Comparison

| Metric | Linear Regression | Ridge Regression |
|---|---:|---:|
| MSE | 965,597,173.76 | 883,964,425.43 |
| RMSE | 31,074.06 | 29,731.54 |
| R² Score | 0.8741 | 0.8848 |

**Result:** Ridge Regression performed better on the test dataset, achieving a lower MSE and RMSE and a higher R² score.

## 6. Key Findings

- OverallQual and GrLivArea showed strong positive correlations with SalePrice.
- Categorical features provided additional predictive information after One-Hot Encoding.
- The final model used 300 encoded features.
- Ridge Regression achieved better evaluation results than Linear Regression.
- Prediction errors were larger for some expensive houses.

## 7. Conclusion

This project demonstrates an end-to-end Machine Learning workflow for house price prediction, including data inspection, missing value handling, exploratory data analysis, feature selection, categorical encoding, model training, evaluation, and interpretation.

Both Linear Regression and Ridge Regression were evaluated. Ridge Regression achieved the better result, with an R² score of 0.8848 and an RMSE of approximately 29,731.54.

The project highlights the importance of data preprocessing and feature engineering in building effective regression models.

## 8. Project Files

- `House_Price_Prediction.ipynb` – Complete Jupyter Notebook containing data analysis, preprocessing, model training, evaluation, and visualizations.
- `train.csv` – Original Kaggle dataset.
- `SalePrice_Distribution.png` – Distribution of house prices.
- `Actual_vs_Predicted.png` – Comparison of actual and predicted house prices.
- `Model_Comparison.png` – Linear Regression and Ridge Regression comparison.

## 9. Author

**Pawan Rathore**

Data Analytics | Python | SQL | Excel | Power BI

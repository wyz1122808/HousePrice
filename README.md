# House Price Prediction

This is a basic guide and documentation of the house price prediction model.

## Introduction

The goal of this project is to predict house prices using various regression techniques.

## Data

The dataset includes two files:

- `train.csv` which is used to train the model.
- `test.csv` which is used to evaluate the model's performance.

## Data Preprocessing

Some columns in the dataset have missing values. The missing values analysis shows the following:


```r
null_columns = train_data.columns[train_data.isnull().any()]
total = train_data[null_columns].isnull().sum().sort_values(ascending=False)
percent = total / 1460
missing_data = pd.concat([total, percent], axis=1, keys=['Total','Percent'])

```
## Feature Transformation
Several columns undergo transformations to better fit into our regression model:

- Sale Price - Log transformation
- GrLivArea - Log transformation
- TotalBsmtSF - Log transformation, with consideration for houses without basements

## Modeling

The XGBoost algorithm is employed as our primary model and categorical features are encoded using label encoding.
As an alternative model, the Random Forest regression is also applied.

## Evaluation

The models' performances are evaluated using the Mean Absolute Error (MAE):

- XGBoost: MAE on validation set and train set
- Random Forest: MAE on a test set of 10% data


## Conclusions

The dataset undergoes preprocessing, feature transformation, and modeling using XGBoost and Random Forest algorithms. The performance is evaluated using MAE. The results suggest further tuning and more sophisticated feature engineering could improve prediction accuracy.


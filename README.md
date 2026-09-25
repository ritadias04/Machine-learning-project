# Used Car Price Prediction

Machine Learning project developed at NOVA IMS (Master's in Data Science and Advanced Analytics, 2025/26).

## Business Problem
Pricing a used car accurately is hard before a mechanical inspection. The goal was to build a regression model that estimates a car's price from its characteristics, helping sellers and dealers set competitive prices with less uncertainty.

## Data
Used car listings with features such as brand, model, year, transmission, fuel type, mileage, fuel efficiency (mpg), engine size and paint quality.

## Approach

### 1. Preprocessing
- Missing numerical values imputed with the mean or median.
- Inconsistent categorical values (e.g. misspelled brands and models) standardised with manually defined dictionaries.
- Extreme outliers limited through winsorising.
- One-hot encoding for categorical features and MinMaxScaler for numerical features.

### 2. Feature Engineering & Selection
- `carAge`: age of the car at the time of the listing.
- `AvgMileagePerYear`: average mileage per year of use.
- Feature selection combining statistical tests (Spearman correlation, chi-squared), LassoCV and Recursive Feature Elimination (RFE).

### 3. Modelling
Models were compared with cross-validation, using MAE as the main metric:
- **K-Nearest Neighbours** (optimal k = 5)
- **Neural Networks (MLPRegressor):** tuned architecture, with the best configuration using two hidden layers (100 and 50 neurons)
- **Decision Trees:** MSE and MAE splitting criteria, splitter strategies and cost-complexity pruning to reduce overfitting
- **Ensembles:** Bagging, Gradient Boosting and **Random Forest**

## Results
- **Random Forest** was selected as the final model, with a test MAE of about 1,470. That is well below Gradient Boosting (about 1,890) and the single decision trees.
- Error analysis by price segment showed an average percentage error (MAPE) of around 9%, with relative errors of about 8% for mid-range and expensive cars.
- The most important features were transmission type, car age and engine size.
- A simple interactive interface (ipywidgets) returns a price prediction for any new car's characteristics.


## Team (Group 28)
Ana Rita Dias · Catarina Santos · Marisa Ramos · Nadia Scaletchi

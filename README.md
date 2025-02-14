# Used Car Price Prediction

## Overview
The goal is to **accurately predict vehicle prices** while ensuring the predictions are **interpretable**.  
We address **missing values**, **outliers**, and **inconsistent labeling**, then compare three **regression algorithms**.  
The **KNN** model ultimately performs best.

---

## Data and Features
- **Total Records**: 402,005  
- **Categorical Features**: `standard_make`, `vehicle_condition`, `fuel_type`, etc.  
- **Numerical Features**: `mileage`, `price`, `year_of_registration`  
- **Key Steps**:  
  - Replaced or dropped **missing values** (e.g., imputed `mileage` and `year_of_registration`).  
  - Removed **outliers** (IQR-based filtering for extreme mileage and price).  
  - Created a new feature, **Car Age** = `(2020 - year_of_registration)`.

> **Note**: The dataset is **not publicly included** due to size.

---

## Project Steps

1. **Data Exploration**  
   - Basic statistics, histograms, and correlations to understand distributions.

2. **Preprocessing & Cleaning**  
   - **Missing Data**: Median imputation and logical corrections (e.g., `mileage = 0` for certain "USED" cars).  
   - **Outliers**: IQR-based filtering for extreme price/mileage values.  
   - **Feature Engineering**: Added Car Age, consolidated rare fuel types.  
   - **Encoding & Scaling**: Converted categorical variables, standardized numerical features.

3. **Model Building**  
   - **KNN**  
   - **Decision Tree**  
   - **Linear Regression**

4. **Hyperparameter Tuning**  
   - **KNN**: `n_neighbors` ∈ {3, 5, 7, 9, 11, 15}.  
   - **Decision Tree**: `max_depth`, `min_samples_leaf`.  
   - **Linear Regression**: Baseline approach (no hyperparameters).

5. **Evaluation**  
   - **RMSE**, **R²**, **residual plots**, and **feature importance**.

---

## Models and Evaluation

- **KNN**  
  - After Grid Search, best model uses `n_neighbors = 15`.

- **Decision Tree**  
  - Tuned `max_depth` and `min_samples_leaf`.

- **Linear Regression**  
  - Baseline approach, no hyperparameters.

**Metrics**  
- **R²** (Coefficient of Determination)  
- **RMSE** (Root Mean Squared Error)  
- Additional interpretability checks (residual distributions, monotonic checks)

---

## Results
- **KNN** emerged as the top performer, achieving **R² ≈ 0.79** and **RMSE ≈ 3801**.  
- **Decision Tree** followed with **R² ≈ 0.75**.  
- **Linear Regression** scored lowest, **R² ≈ 0.71**.

---

## Interpretability
- **Feature Importance**: Car Age, body type, and brand significantly affect price.  
- **Residual Analysis**: Visual checks for distribution and outliers confirmed monotonic trends (older cars → lower price).

---

## Usage

```bash
# 1. Clone this repository
git clone https://github.com/Salman-Javaid-Hub/MMU.git

# 2. Install dependencies
pip install -r requirements.txt

# 3. Run notebooks or scripts to replicate preprocessing, modeling, and evaluation steps
# 4. Adjust hyperparameters in the code (e.g., for KNN or Decision Tree) as needed

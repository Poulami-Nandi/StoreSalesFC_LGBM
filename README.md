# StoreSalesFC_LGBM: Store Sales - Time Series Forecasting

This repository contains a complete solution for the **Store Sales - Time Series Forecasting** Kaggle competition. The task is to predict the daily sales of various items across different stores for a specified period using historical data and external factors.

---

## Problem Statement

Accurately forecasting sales is critical for effective inventory management and resource allocation. This project involves predicting future sales for store-item combinations using time-series data enriched with external datasets.

### Objective
The primary goal is to predict the `sales` column in the test dataset for each `id`. The predictions should minimize the **Root Mean Squared Logarithmic Error (RMSLE)**.

---

## Dataset Overview

The competition provides several datasets:

1. **`train.csv`**  
   Historical daily sales data:
   - `date`: Date of sales.
   - `store_nbr`: Store identifier.
   - `family`: Product category.
   - `sales`: Target variable (daily sales).
   - `onpromotion`: Whether the item was on promotion.

2. **`test.csv`**  
   Test data for prediction:
   - `id`: Unique identifier.
   - `date`, `store_nbr`, `family`, `onpromotion`: Features for which predictions are required.

3. **`stores.csv`**  
   Metadata about each store (e.g., location and type).

4. **`oil.csv`**  
   Daily oil prices, which may influence the economy and sales.

5. **`holidays_events.csv`**  
   Information about holidays and special events, potentially impacting sales.

6. **`transactions.csv`**  
   Historical daily transactions for each store.

---

## Project Workflow

### 1. Data Preprocessing
- Merge external datasets with `train` and `test`.
- Handle missing values (e.g., forward-fill oil prices).
- Encode categorical features (e.g., `family`, `type`) using `LabelEncoder`.
- Extract time-based features (e.g., day of the week, month, year).

### 2. Model Training
- Use **LightGBM**, a gradient boosting framework, for training.
- Split the training data into training and validation sets.
- Optimize the model to minimize RMSLE using:
  - Early stopping.
  - Hyperparameter tuning.

### 3. Prediction and Submission
- Generate predictions for the test dataset.
- Prepare a valid submission file with `id` and `sales` columns.

---

## Repository Structure

```plaintext
.
├── data/
│   ├── train.csv                # Training dataset
│   ├── test.csv                 # Test dataset
│   ├── stores.csv               # Store metadata
│   ├── oil.csv                  # Daily oil prices
│   ├── holidays_events.csv      # Holidays and special events
│   ├── transactions.csv         # Daily transactions
├── notebooks/
│   ├── store_sales_forecasting.ipynb  # Complete solution notebook
├── submission/
│   ├── submission.csv           # Submission file
├── requirements.txt             # Required Python libraries
└── README.md                    # Project documentation


---
## Requirements
To run the project, install the required Python libraries:

```plaintext

bash
Copy code
pip install -r requirements.txt

---
## Key Libraries:
- pandas: For data manipulation.
- numpy: For numerical operations.
- lightgbm: For training the gradient boosting model.
- scikit-learn: For data splitting and evaluation metrics.

---
## Running the Notebook
- Setup Kaggle API:
Download the datasets using the Kaggle API or manually upload them to the data/ folder.
- Run the Jupyter Notebook:
Execute the steps in store_sales_forecasting.ipynb sequentially to:
Preprocess the data.
Train the LightGBM model.
Generate predictions.
- Create the Submission File:
Save the final predictions as submission.csv in the submission/ folder.

---

## Expected Results
A successful solution should:

Accurately predict daily sales for each store-item combination.
Minimize the RMSLE metric.
Generate a valid submission file with the required format.

---
## License
This project is licensed under the MIT License.

---
## Acknowledgments
Kaggle for hosting the Store Sales - Time Series Forecasting competition.
The data contributors for providing detailed and rich datasets.

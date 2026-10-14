# Beta Bank Churn Prediction

Machine learning project focused on predicting customer churn for Beta Bank.

The objective is to identify customers who are likely to leave the bank so that retention strategies can be applied before churn occurs.

## Project Objective

The target variable is `Exited`:

- `0`: the customer stays with the bank.
- `1`: the customer leaves the bank.

The main evaluation metric is **F1-score**, with a required minimum value of **0.59** on the test set.

**AUC-ROC** is also used as a complementary metric to evaluate the model's ability to distinguish between customers who churn and those who remain.

## Dataset

The dataset contains 10,000 customer records with information such as:

- Credit score
- Geography
- Gender
- Age
- Tenure
- Account balance
- Number of products
- Credit card ownership
- Activity status
- Estimated salary

The dataset is not included in this repository.

## Data Preparation

The following preprocessing steps were performed:

- Removed non-predictive columns:
  - `RowNumber`
  - `CustomerId`
  - `Surname`
- Filled missing values in `Tenure` using the median calculated from the training set.
- Applied One-Hot Encoding to categorical variables.
- Standardized numerical features.
- Split the data into:
  - 60% training
  - 20% validation
  - 20% test
- Used stratification to preserve the class distribution.

## Class Imbalance

The target variable was imbalanced:

- Approximately 79.6% of customers remained.
- Approximately 20.4% of customers churned.

Two techniques were evaluated to address class imbalance:

- `class_weight='balanced'`
- Upsampling of the minority class

## Models Evaluated

The following models were tested:

- Logistic Regression
- Logistic Regression with class weights
- Logistic Regression with upsampling
- Decision Tree
- Random Forest
- Random Forest with class weights
- Random Forest with upsampling

## Best Model

The best validation performance was obtained with a Random Forest trained using upsampling.

Parameters:

- `n_estimators = 100`
- `max_depth = 11`
- `random_state = 12345`

Validation results:

- F1-score: **0.644**
- AUC-ROC: **0.867**

## Final Test Results

The final model achieved:

- F1-score: **0.590**
- AUC-ROC: **0.851**

The model met the required minimum F1-score of 0.59.

## Technologies Used

- Python
- Pandas
- Scikit-learn
- Jupyter Notebook
- Git
- GitHub

## Repository Structure

```text
beta-bank-churn-prediction/
│
├── beta_bank_churn_prediction.ipynb
├── README.md
└── .gitignore
# Breast Cancer Classification and Diabetes Regression using Scikit-Learn

## Overview

This project explores two fundamental Machine Learning problem types using datasets available in Scikit-Learn:

1. **Binary Classification** using Logistic Regression on the Breast Cancer dataset.
2. **Regression** using Linear Regression, Lasso (L1), and Ridge (L2) Regularisation on the Diabetes dataset.

The objective of this assignment was not only to train machine learning models but also to understand concepts such as:

- Train-Test Splitting
- Feature Scaling
- Logistic Regression
- Classification Metrics
- Linear Regression
- Mean Squared Error (MSE)
- L1 (Lasso) Regularisation
- L2 (Ridge) Regularisation
- Feature Selection
- Coefficient Shrinkage

---

# Part 1 – Breast Cancer Classification

## Problem Statement

Predict whether a breast tumor is:

- Malignant (Cancerous)
- Benign (Non-Cancerous)

This is a **Binary Classification** problem because the target variable contains two classes.

Dataset used:

```python
from sklearn.datasets import load_breast_cancer
```

Target values:

```text
0 = Malignant
1 = Benign
```

---

## Workflow

### Step 1 – Load Dataset

The Breast Cancer dataset was loaded from Scikit-Learn and separated into:

- Features (X)
- Target (y)

### Step 2 – Train-Test Split

The dataset was divided into:

```text
80% Training Data
20% Testing Data
```

using:

```python
train_test_split(
    test_size=0.20,
    random_state=9001
)
```

The fixed random state ensures reproducible results.

### Step 3 – Feature Scaling

MinMaxScaler was applied to normalize all features into the range:

```text
0 → 1
```

Feature scaling is important because Logistic Regression performs better when features are on comparable scales.

To avoid data leakage:

```python
scaler.fit(X_train)
scaler.transform(X_train)
scaler.transform(X_test)
```

was used instead of fitting the scaler on the test data.

### Step 4 – Model Training

A Logistic Regression classifier was trained using the default solver.

```python
log_reg = LogisticRegression()
```

### Step 5 – Evaluation

Predictions were generated on both training and testing datasets and evaluated using:

```python
classification_report()
```

which provides:

- Accuracy
- Precision
- Recall
- F1 Score

---

## Results

### Training Performance

| Metric | Value |
|----------|----------|
| Accuracy | 96.26% |

### Testing Performance

| Metric | Value |
|----------|----------|
| Accuracy | 100.00% |

The model achieved perfect classification on the testing split used in this assignment.

---

## Key Learnings

### Precision

Measures:

> When the model predicts a class, how often is it correct?

### Recall

Measures:

> Out of all actual examples of a class, how many did the model identify?

### F1 Score

Balances Precision and Recall into a single metric.

### Data Leakage

Feature scaling should always be fitted using training data only and then applied to testing data.

---

# Part 2 – Diabetes Disease Progression Prediction

## Problem Statement

Predict a patient's disease progression score using clinical measurements.

Dataset used:

```python
from sklearn.datasets import load_diabetes
```

Unlike the Breast Cancer dataset, the target variable is numerical.

Therefore, this becomes a **Regression** problem.

---

## Workflow

### Step 1 – Load Dataset

The Diabetes dataset was loaded and separated into:

- Features (X)
- Target (y)

Target:

```text
Disease Progression Score
```

### Step 2 – Train-Test Split

```text
80% Training Data
20% Testing Data
```

using:

```python
random_state=9001
```

### Step 3 – Feature Scaling

MinMaxScaler was applied to normalize feature ranges.

### Step 4 – Train Three Regression Models

#### Model A – Linear Regression

No regularisation applied.

```python
LinearRegression()
```

#### Model B – Lasso Regression (L1)

Uses L1 Regularisation.

```python
Lasso(alpha=1)
```

Lasso can shrink coefficients to exactly zero and perform automatic feature selection.

#### Model C – Ridge Regression (L2)

Uses L2 Regularisation.

```python
Ridge(alpha=1)
```

Ridge shrinks coefficients while retaining all features.

### Step 5 – Evaluation

Performance was measured using:

```python
mean_squared_error()
```

---

## Why MSE?

Mean Squared Error (MSE) measures the average squared difference between:

```text
Actual Value
Predicted Value
```

Lower MSE indicates better predictive performance.

The squaring operation penalizes large prediction errors more heavily.

---

## Results

| Model | MSE |
|----------|----------|
| Linear Regression | 2839.66 |
| Ridge Regression (L2) | 2914.91 |
| Lasso Regression (L1) | 3066.58 |

### Best Performing Model

For this dataset and train-test split:

```text
Linear Regression
```

achieved the lowest Mean Squared Error.

This suggests that strong regularisation was not necessary for this particular dataset.

---

# Understanding Regularisation

## L1 Regularisation (Lasso)

Lasso penalizes coefficient magnitude and may completely remove features.

Example from the results:

| Feature | Linear | Lasso |
|----------|----------|----------|
| age | -9.01 | 0 |
| s1 | -207.80 | 0 |
| s2 | 115.73 | 0 |
| s4 | 60.42 | 0 |

These coefficients were reduced to zero, effectively removing the features from the model.

This demonstrates automatic feature selection.

---

## L2 Regularisation (Ridge)

Ridge reduces coefficient magnitude but keeps all features.

Example:

| Feature | Linear | Ridge |
|----------|----------|----------|
| s1 | -207.80 | -24.04 |

The feature remains in the model but with reduced influence.

This helps reduce model complexity while preserving information from all features.

---

# Comparison of Regression Models

| Property | Linear Regression | Lasso (L1) | Ridge (L2) |
|----------|----------|----------|----------|
| Regularisation | No | Yes | Yes |
| Feature Removal | No | Yes | No |
| Coefficient Shrinkage | No | Yes | Yes |
| Feature Selection | No | Yes | No |
| Complexity Control | No | Yes | Yes |

---

# Key Learnings

This assignment provided practical exposure to:

### Classification

- Logistic Regression
- Accuracy
- Precision
- Recall
- F1 Score

### Regression

- Linear Regression
- Mean Squared Error

### Regularisation

- L1 (Lasso)
- L2 (Ridge)
- Feature Selection
- Coefficient Shrinkage

### Machine Learning Workflow

```text
Dataset
    ↓
Train-Test Split
    ↓
Feature Scaling
    ↓
Model Training
    ↓
Prediction
    ↓
Evaluation
```

---

## Technologies Used

- Python
- Pandas
- NumPy
- Scikit-Learn
- Jupyter Notebook

---

## Conclusion

This assignment demonstrates two core machine learning workflows:

1. Classification using Logistic Regression for predicting breast cancer diagnosis.
2. Regression using Linear, Lasso, and Ridge Regression for predicting diabetes disease progression.

It also highlights the practical impact of Regularisation techniques on model complexity, coefficient behavior, feature selection, and predictive performance.
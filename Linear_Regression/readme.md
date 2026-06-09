# University Graduation Rate Prediction using Linear Regression

## Overview

This assignment demonstrates the complete machine learning workflow for a regression problem using Linear Regression. The objective is to predict a university's graduation rate (`Grad.Rate`) based on institutional characteristics such as admissions, enrollment, expenditure, faculty qualifications, alumni engagement, and whether the university is private or public.

The project covers data preparation, feature engineering, model training, prediction, and evaluation using standard regression metrics.

---

## Problem Statement

Build a Linear Regression model to predict the graduation rate of universities using the provided dataset.

Target Variable:

- `Grad.Rate`

Objective:

- Train a Linear Regression model
- Generate predictions on training and testing datasets
- Evaluate model performance using regression metrics
- Interpret the learned coefficients

---

## Dataset Preparation

The following preprocessing steps were performed:

### 1. Remove University Name

The university name column was removed because it acts as an identifier rather than a predictive feature.

### 2. Exploratory Data Analysis

Descriptive statistics were generated using:

```python
df.describe().round(2)
```

This provided:

- Mean
- Standard Deviation
- Minimum
- Maximum
- Quartiles

for all numerical features.

### 3. One-Hot Encoding

The categorical feature:

```text
Private
```

was converted into numerical format using:

```python
pd.get_dummies(drop_first=True)
```

Result:

```text
Private_Yes
```

where:

- 1 = Private University
- 0 = Public University

Using `drop_first=True` avoids multicollinearity caused by redundant encoded columns.

### 4. Feature and Target Separation

Features:

```python
X
```

Target:

```python
y = Grad.Rate
```

---

## Train-Test Split

Dataset split:

```text
70% Training
30% Testing
```

Configuration:

```python
random_state = 42
```

This ensures reproducible results.

---

## Model Training

Model used:

```python
LinearRegression()
```

The model was trained on the training dataset using:

```python
model.fit(X_train, y_train)
```

---

## Model Coefficients

After training, coefficients were extracted using:

```python
model.coef_
```

Key observations:

| Feature | Coefficient |
|----------|----------|
| Private_Yes | 5.05 |
| perc.alumni | 0.34 |
| Top25perc | 0.14 |
| PhD | 0.14 |
| Terminal | -0.11 |

### Interpretation

#### Private_Yes (+5.05)

Private universities are predicted to have graduation rates approximately 5 percentage points higher than public universities, holding all other features constant.

#### perc.alumni (+0.34)

Higher alumni participation is associated with higher graduation rates.

#### PhD (+0.14)

Universities with a greater percentage of faculty holding PhDs tend to achieve slightly higher graduation rates.

#### Terminal (-0.11)

A negative relationship was observed with graduation rate. This represents correlation within the dataset and should not be interpreted as causation.

---

## Model Evaluation

### Training Performance

| Metric | Value |
|----------|----------|
| R² | 0.46 |
| MSE | 160.59 |
| MAE | 9.37 |

### Testing Performance

| Metric | Value |
|----------|----------|
| R² | 0.44 |
| MSE | 160.48 |
| MAE | 9.60 |

---

## Understanding the Metrics

### R² Score

Measures how much variation in graduation rate is explained by the model.

```text
R² = 0.44
```

The model explains approximately 44% of the variation in graduation rates.

---

### Mean Squared Error (MSE)

Measures prediction error while heavily penalizing large mistakes.

```text
Lower MSE = Better
```

---

### Mean Absolute Error (MAE)

Measures the average prediction error.

```text
MAE = 9.60
```

Interpretation:

On average, the model's graduation rate predictions are off by approximately 9.6 percentage points.

---

## Overfitting Analysis

Train and test metrics are very similar:

| Metric | Train | Test |
|----------|----------|----------|
| R² | 0.46 | 0.44 |
| MAE | 9.37 | 9.60 |

This indicates:

- Good generalization
- No significant overfitting
- Stable model performance on unseen data

---

## Key Learnings

This assignment demonstrates:

- Data preprocessing for machine learning
- One-hot encoding of categorical variables
- Feature and target separation
- Train-test splitting
- Linear Regression model training
- Coefficient interpretation
- Regression evaluation metrics
- Model generalization assessment

The project serves as a complete end-to-end example of applying Linear Regression to a real-world prediction problem.

---

## Technologies Used

- Python
- Pandas
- NumPy
- Scikit-Learn
- Jupyter Notebook

---

## Concepts Covered

- Linear Regression
- Feature Engineering
- One-Hot Encoding
- Train-Test Split
- Coefficient Interpretation
- R² Score
- Mean Squared Error (MSE)
- Mean Absolute Error (MAE)
- Model Evaluation
- Generalization vs Overfitting
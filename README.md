# Diabetes Prediction Using Machine Learning

This project demonstrates data cleaning, exploratory data analysis (EDA), handling missing values, outlier detection, and model building.

---

## Table of Contents
- [Overview](#overview)
- [Dataset](#dataset)
- [Project Pipeline](#project-pipeline)
- [Model Performance](#model-performance)
- [Model Testing](#model-testing)
- [Tools](#-tools)

---

## Overview

This project uses the **Pima Indians Diabetes Database** to build a predictive model that determines whether a patient has diabetes based on diagnostic measurements. The dataset has been modified to include realistic data quality issues (like invalid zero values) to simulate real-world healthcare data challenges.

---

## Dataset

- **Source**: `diabetes1.csv`
- **Features**:
  - `Pregnancies`
  - `Glucose`
  - `BloodPressure`
  - `SkinThickness`
  - `Insulin`
  - `BMI`
  - `DiabetesPedigreeFunction`
  - `Age`
  - `Outcome` (target: 0 = No Diabetes, 1 = Diabetes)

---

## Project Pipeline

### 1. Data Loading & Cleaning
- Loaded dataset using `pandas`
- Removed duplicate records
- Identified and handled invalid zero values

### 2. Missing Value Treatment
- Replaced invalid `0` values with `NaN` in columns: `Glucose`, `BloodPressure`, `SkinThickness`, `Insulin`, `BMI`
- Used **KNN Imputation** (k=5) to fill missing values
- Visualized missing patterns with `missingno`

### 3. Data Splitting
- **Train**: 60%
- **Validation**: 20%
- **Test**: 20%
- Used `stratify=y` to maintain class balance

### 4. Outlier Detection
- Applied **Z-score method** (threshold = 3)
- Removed outliers from training set only

### 5. Feature Scaling
- Used **RobustScaler** (less sensitive to outliers)

### 6. Exploratory Data Analysis
- Histograms with KDE plots
- Boxplots for outlier visualization
- Correlation heatmaps

### 7. Feature Engineering
New features were created to improve predictive performance:
- Glucose_BMI_Interaction
- Glucose_Genetic_Interaction
- Metabolic_Score
- Obese
- Hypertensive
- Glucose_Squared

### 8. Feature Selection
Feature reduction techniques are applied to identify the most important predictors.
Methods:
- Feature Importance Analysis
- Top-N Feature Selection

### 9. Sampling
Sampling techniques are applied to address class imbalance (SMOTETomek) and improve model generalization.

### 10. Models Evaluated
The following machine learning models were trained and tuned:

1. Logistic Regression
2. Decision Tree
3. Random Forest
4. Neural Network
5. K-Nearest Neighbors (KNN)
6. Naive Bayes
7. Stacking Classifier

---

## Model Performance

| Model | Accuracy | AUC |
|---------|----------|---------|
| Logistic Regression | 0.73 | 0.7967 |
| Decision Tree | 0.74 | 0.7579 |
| Random Forest | 0.77 | 0.8224 |
| Neural Network | 0.71 | 0.7885 |
| K-Nearest Neighbors | 0.70 | 0.7572 |
| Naive Bayes | 0.69 | 0.7876 |
| Stacking Classifier | **0.78** | 0.8117 |

### Best Model

**Stacking Classifier (highest accuracy)**
- Accuracy: 78%
- AUC: 0.8117

**Random Forest (higest AUC)**
- Accuracy: 77%
- AUC: 0.8224

---

## Model Testing

Source: `diabetes2.csv` 
<br>

By using Random Forest: <br>

<img width="546" height="357" alt="image" src="https://github.com/user-attachments/assets/2bfa89f9-162b-4c25-983a-402938223625" />

---

## Tools

| Library | Purpose |
|---------|---------|
| `pandas`, `numpy` | Data manipulation |
| `matplotlib`, `seaborn`, `missingno` | Visualization |
| `scikit-learn` | Machine learning & preprocessing |

**Key scikit-learn components**:
- `train_test_split`
- `KNNImputer`
- `RobustScaler`
- `zscore`

# Diabetes-Prediction-Using-Machine-Learning

This project focuses on building a **predictive model** for diabetes diagnosis using clinical data. The pipeline includes **data cleaning**, **exploratory data analysis**, **handling missing values**, **outlier detection**, and **model training**. The dataset used is the well-known **Pima Indians Diabetes Database**, but this version contains additional noise (`0` values as missing data) to simulate real‑world healthcare data challenges.

---

## 📁 Dataset

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

## 🔍 Project Workflow

### 1. Data Loading & Initial Exploration
- Loaded the dataset using `pandas`.
- Inspected structure, data types, and missing values.
- Identified **duplicate records** and removed them.

### 2. Missing Value Handling
- Detected that `0` values in certain columns (`Glucose`, `BloodPressure`, `SkinThickness`, `Insulin`, `BMI`) are invalid.
- Replaced these `0`s with `NaN`.
- Used **KNN Imputation** to fill missing values.
- Visualized missing patterns using `missingno`.

### 3. Train‑Validation‑Test Split
- Split data into:
  - **Train**: 60%
  - **Validation**: 20%
  - **Test**: 20%
- Used `stratify=y` to maintain class balance across splits.

### 4. Outlier Detection & Removal
- Applied **Z‑score method** to the training set.
- Removed samples with any feature having a Z‑score > 3.

### 5. Feature Scaling
- Applied **RobustScaler** to scale features (less sensitive to outliers).

### 6. Exploratory Data Analysis (EDA)
- Visualized distributions using **histograms + KDE**.
- Plotted **boxplots** to inspect outliers.
- Analyzed **correlation matrices** using `seaborn`.

---

## 🛠️ Technologies Used

- `pandas`, `numpy`
- `matplotlib`, `seaborn`, `missingno`
- `scikit‑learn`:
  - `train_test_split`
  - `KNNImputer`
  - `RobustScaler`
  - `zscore`

---

## 📊 Visualizations

| Before Cleaning | After Imputation & Outlier Removal |
|----------------|--------------------------------------|
| ![Before Hist](images/before_hist.png) | ![After Hist](images/after_hist.png) |
| ![Before Boxplot](images/before_boxplot.png) | ![After Boxplot](images/after_boxplot.png) |
| ![Correlation Before](images/corr_before.png) | ![Correlation After](images/corr_after.png) |

> *(Replace with actual image paths if you have them)*

---

## 🚀 How to Run

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/diabetes-prediction.git
   cd diabetes-prediction

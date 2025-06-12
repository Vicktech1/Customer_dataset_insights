# Diabetes Dataset Analysis & Preprocessing

This project focuses on cleaning, preprocessing, and exploring a medical dataset related to diabetes diagnosis. The dataset provides medical and personal attributes of patients and indicates whether each patient has been diagnosed with diabetes.

---

## Table of Contents

- [Introduction](#-introduction)
- [Dataset Overview](#-dataset-overview)
- [Data Cleaning and Preprocessing](#-data-cleaning-and-preprocessing)
- [Exploratory Data Analysis (EDA)](#-exploratory-data-analysis-eda)
- [Key Insights](#-key-insights)
- [Conclusion](#-conclusion)
- [Tools Used](#-tools-used)

## Introduction

Diabetes is a chronic condition that affects how the body processes blood sugar. Early detection and monitoring are crucial for managing the disease. This project aims to prepare and analyze a structured dataset to better understand the patterns and indicators associated with diabetes. The ultimate goal is to enable future predictive modeling or decision-support systems.


## Dataset Overview

The dataset was loaded from:
```python
data = pd.read_excel("datasets/diabetes.xlsx")
````

It contains the following features:

| Column                   | Description                                                            |
| ------------------------ | ---------------------------------------------------------------------- |
| Pregnancies              | Number of times pregnant                                               |
| Glucose                  | Plasma glucose concentration                                           |
| BloodPressure            | Diastolic blood pressure (mm Hg)                                       |
| SkinThickness            | Triceps skin fold thickness (mm)                                       |
| Insulin                  | 2-Hour serum insulin (mu U/ml)                                         |
| BMI                      | Body mass index (weight in kg/(height in m)^2)                         |
| DiabetesPedigreeFunction | A function which scores likelihood of diabetes based on family history |
| Age                      | Age in years                                                           |
| Outcome                  | 0 = Non-diabetic, 1 = Diabetic                                         |

---

## Data Cleaning and Preprocessing

### Steps Performed:

1. **Missing Value Treatment**

   * No `NaN` values were found, but columns like `Glucose`, `BloodPressure`, `SkinThickness`, `Insulin`, and `BMI` had **zero values**, which are biologically implausible.
   * These zero values were replaced with:

     * Median for `Glucose`, `BloodPressure`, `BMI`
     * Mean for `Insulin` and `SkinThickness`

2. **Data Type Checks**

   * All features were numeric and correctly typed.

3. **Outlier Detection**

   * Boxplots and Z-score methods were used to identify outliers.
   * Outliers were either capped or retained depending on their medical validity.

4. **Normalization/Scaling**

   * Applied **MinMaxScaler** for feature scaling if required for visualization or modeling:

     ```python
     from sklearn.preprocessing import MinMaxScaler
     ```

5. **Target Distribution**

   * Outcome is binary and imbalanced (\~65% non-diabetic, \~35% diabetic). Awareness of this imbalance is crucial for future modeling.

---

## Exploratory Data Analysis (EDA)

### 1. **Outcome Distribution**

```python
sns.countplot(data['Outcome'])
```

* Clear imbalance between diabetic and non-diabetic patients.

### 2. **Glucose vs Outcome**

```python
sns.boxplot(x='Outcome', y='Glucose', data=data)
```

* Diabetic patients tend to have significantly higher glucose levels.

### 3. **Age Distribution**

```python
sns.histplot(data['Age'], kde=True)
```

* Most patients are between 20 and 45 years old.

### 4. **BMI vs Diabetes Pedigree**

```python
sns.scatterplot(x='BMI', y='DiabetesPedigreeFunction', hue='Outcome')
```

* High BMI and family history increase diabetes risk.

### 5. **Correlation Heatmap**

```python
sns.heatmap(data.corr(), annot=True, cmap='coolwarm')
```

* Strongest correlation with Outcome: **Glucose**, **BMI**, **Age**, and **Pregnancies**

### 6. **Pairplot**

```python
sns.pairplot(data, hue='Outcome')
```

* Gives a multi-dimensional view of class separation.

---

## Key Insights

* **Glucose level** is the most significant feature related to diabetes outcome.
* Higher **BMI**, **age**, and **pregnancy count** also increase the likelihood of diabetes.
* **Insulin** and **SkinThickness** had many zero entries, indicating possibly unreliable data collection.
* There is a **class imbalance** which needs to be addressed in future modeling (e.g., with SMOTE or resampling).

---

## Conclusion

This project successfully prepared the diabetes dataset for future modeling by addressing missing data, correcting zero anomalies, and performing insightful exploratory analysis. The visualizations confirm several known risk factors for diabetes, including high glucose levels, increased BMI, and family history.

With the cleaned dataset, the next logical step is building a **classification model** (e.g., Logistic Regression, Random Forest, or XGBoost) to predict diabetes presence based on the input features.

---

## Tools Used

* Python 3.x
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn (for future modeling)

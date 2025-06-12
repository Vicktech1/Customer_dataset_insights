# Customer Dataset – Data Cleaning & Exploratory Analysis

## Table of Contents

- [Introduction](#introduction)
- [Dataset Overview](#dataset-overview)
- [Data Cleaning](#data-cleaning)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Preprocessing](#data-preprocessing)
- [Summary](#summary)
- [Tools Used](#tools-used)
- [Conclusion](#conclusion)

---

## Introduction

This project focuses on cleaning and analyzing a customer dataset to uncover insights into customer behavior and prepare the data for future modeling tasks. The dataset includes demographic and transactional information such as gender, age, profession, purchase amount, product category, and subscription status. The goal is to ensure data quality, explore patterns, and format the dataset for downstream machine learning or business intelligence tasks.

---

## Dataset Overview

The dataset is composed of the following features:

| Column Name         | Description                                               |
|---------------------|-----------------------------------------------------------|
| CustomerID          | Unique ID assigned to each customer                      |
| Gender              | Customer’s gender (Male/Female)                          |
| Age                 | Age of the customer in years                             |
| Items Purchased     | Item bought by the customer                              |
| Category            | Category the purchased item belongs to (e.g., Clothing)  |
| Purchase Amount     | Monetary amount spent on the purchase                    |
| Shipping Type       | Type of shipping selected (e.g., Express, Standard)      |
| Profession          | Customer’s profession (e.g., Healthcare, Education)      |
| Subscription Status | Whether the customer has an active subscription (Yes/No)|
| Season              | Season when purchase was made (e.g., Summer, Spring)     |
| Country             | Country of the customer                                  |

---

## Data Cleaning

Several cleaning steps were performed to improve data quality:

- **Handled missing values**: Rows with critical missing information were removed; non-critical columns were imputed.
- **Standardized categorical entries**: For example, inconsistencies like "yes"/"Yes" were unified.
- **Converted data types**: Categorical features were encoded properly for modeling and analysis.
- **Removed duplicate records** to avoid biased analysis.
- **Corrected typos and formatting issues**, especially in string-based columns like `Category`, `Country`.

---

## Exploratory Data Analysis

The dataset was explored using a variety of visual and statistical techniques:

- **Count plots** to show distribution of customers by gender, profession, and shipping type.
- **Histograms** and **boxplots** for age and purchase amount to identify trends and outliers.
- **Bar plots** comparing purchase behavior across seasons and professions.
- **Pie charts** for subscription status and item categories to understand overall preferences.

These insights highlighted key patterns, such as:
- Younger customers tend to spend more in Spring.
- Certain professions (e.g., Tech and Healthcare) have higher subscription rates.
- Clothing is the most purchased category across all demographics.

---

## Data Preprocessing

The dataset was preprocessed to make it ready for analysis and modeling:

- **Label Encoding** was applied to binary variables like `Gender` and `Subscription Status`.
- **One-Hot Encoding** for multi-class categorical variables like `Category`, `Profession`, and `Season`.
- **Feature scaling** was done on numerical features like `Purchase Amount` and `Age` to normalize them.
- **Feature engineering** ideas include combining `Category` and `Season` to detect seasonal product demand.

---

## Summary

- Cleaned raw customer data and removed inconsistencies.
- Explored distributions and relationships across key attributes.
- Transformed data into a usable format for predictive modeling or clustering.
- Gained valuable insights into seasonal and professional buying patterns.

---

## Tools Used

- **Python**
  - `pandas` for data manipulation
  - `numpy` for numerical operations
  - `matplotlib` & `seaborn` for data visualization

---

## Conclusion

This analysis enhanced the usability of the customer dataset through rigorous cleaning and insightful visualizations. The refined data is now ready for advanced analytics, such as customer segmentation, purchase prediction, or churn modeling. These insights can help businesses tailor marketing strategies, improve product targeting, and enhance customer satisfaction.


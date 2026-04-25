# 📊 Data Preprocessing & Multi-Source Data Integration Project

## 📌 Overview

This project focuses on **real-world data preprocessing** using data from multiple sources:

* CSV file (customer data)
* JSON file (transaction data)
* API (user data)

The goal is to clean, transform, and merge these datasets into a single structured dataset for analysis and machine learning.

---

## 📂 Data Sources

### 1. CSV (customers_messy_80.csv)

Contains basic customer information:

* customer_id
* age
* city

### 2. JSON (transactions_messy_80.json)

Contains transaction details:

* customer_id
* purchase_amount
* payment_method

### 3. API (Random User API)

Fetched using:

```python
https://randomuser.me/api/?results=50
```

Contains:

* gender
* location.city
* email

---

## 🔧 Steps Performed

### 1. Data Loading

* Loaded CSV using `pd.read_csv()`
* Loaded JSON using `json` + `pd.json_normalize()`
* Fetched API data using `requests`

---

### 2. Data Cleaning

* Handled missing values using:

  * `fillna()`
  * `mode()[0]`
* Converted data types (e.g., age → numeric)
* Standardized text values (e.g., payment_method → uppercase)

---

### 3. Feature Selection

Selected important columns:

* CSV → `customer_id`, `age`, `city`
* JSON → `customer_id`, `purchase_amount`, `payment_method`
* API → `customer_id`, `gender`, `location.city`

---

### 4. Data Merging

Merged datasets using:

```python
pd.merge(df1, df2, on="customer_id", how="outer")
```

* Used `customer_id` as common key
* Applied outer join to retain all data

---

### 5. Handling Issues

* Duplicate columns after merge (`_x`, `_y`)
* Missing values
* Inconsistent formats
* No common key in API → created `customer_id`

---

## 📊 Analysis Performed

* Gender-wise count:

```python
df_final["gender"].value_counts()
```

* Missing value handling
* Correlation heatmap (numeric features only)

---

## 🚫 Important Learnings

* Never use `customer_id` in analysis (only for merging)
* Always check `.columns` after merge
* Avoid overwriting DataFrame:

```python
df = df["column"] ❌
```

* Use:

```python
col = df["column"] ✔
```

---

## 📈 Future Improvements

* Add visualization (bar chart, heatmap)
* Build ML model (Customer Churn Prediction)
* Automate preprocessing pipeline

---

## 🧠 Skills Used

* Python (Pandas, NumPy)
* Data Cleaning
* Data Merging
* API Handling
* Exploratory Data Analysis (EDA)

---

## 🚀 Conclusion

This project simulates real-world data challenges where:

* Data comes from multiple sources
* Data is messy and inconsistent
* Proper preprocessing is required before analysis

---

## 📎 Author

Macwan Alex

---

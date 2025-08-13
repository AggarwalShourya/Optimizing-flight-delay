# Optimizing Air Travel – Flight Delay Analysis & Prediction

## 📌 Project Overview
This project analyzes and predicts **flight delays** using historical airline operational data.  
It combines **Exploratory Data Analysis (EDA)**, **feature engineering**, and **machine learning models** to:
- Identify patterns in delays
- Understand the main causes
- Predict whether a flight will be delayed
- Estimate delay duration

The project also introduces a **custom Operational Adjustability Index (OAI)** to prioritize **controllable delays** for airlines and airports.

---

## 📂 Data Sources
- **Airline_Delay_Cause.csv** – Flight delay records and causes
- **Download_Column_Definitions.xlsx** – Column descriptions

---

## 🔍 Key Analyses & Findings

### Exploratory Data Analysis (EDA)
- **Delta Airlines @ ATL** had the highest delay counts for a single month
- **DFW Airport** recorded:
  - Highest weather-related delays in a month
  - Highest security-related delays (possibly due to stricter protocols)
- **Seasonality:** Minimal; weather-related delays consistent across months

**Visuals Produced:**
- Top 20 airports by weather, carrier, and security delays
- Delay trends across months
- Delay counts per airline and airport

---

## 🛠 Preprocessing Steps

### 1. **Missing Values**
- ~300–500 NaN values (~0.3% of data)  
- Dropped rows with NaNs due to small percentage

### 2. **Feature Engineering**
- **Carrier-Airport Delay Score:** Mean carrier-caused delays per airport
- **Weather-Month Score:** Mean weather delays per month
- **Security-Airport Score:** Mean security delays per airport
- **Delay Rate:** `arr_del15 / arr_flights`  
  - Threshold **0.2** chosen (from histogram distribution) for binary classification target `is_delayed`
- **Operational Adjustability Index (OAI):**
    OAI = 2.0 × Carrier Delay +2.0 × Late Aircraft Delay +1.5 × NAS Delay +1.0 × Weather Delay +0.5 × Security Delay


- **Label Encoding** for categorical variables:
  - `carrier_name` → `carrier_label`
  - `airport` → `airport_label`

### 3. **Target Variables**
- **Classification:** `is_delayed` (binary: 0 or 1)
- **Regression:** Average arrival delay (`avg_arr_delay`) for delayed flights

---

## 📊 Modelling Approach

### Classification Models
- **Random Forest Classifier** – Baseline model
- **XGBoost Classifier** – Tuned and achieved best performance

**Handling Class Imbalance:**
- Used `scale_pos_weight = (negative / positive)` in XGBoost

**Performance Metrics:**

| Model | Accuracy | Precision | Recall | F1 Score |
|-------|----------|-----------|--------|----------|
| **Random Forest** | **0.84** | **0.70** | **0.78** | **0.74** |
| **XGBoost** | **0.85** | **0.72** | **0.80** | **0.76** |

---

### Regression Models
- **Random Forest Regressor** – Baseline
- **XGBoost Regressor** – Lower MAE and better generalization

**Best Regression Results (XGBoost):**
- Mean Absolute Error (MAE): **4.52 minutes**

---

### OAI Prediction
- **Model:** Random Forest Regressor
- **Performance:**
  - MAE: **333.5 minutes**
  - R² Score: **0.996**
- **Goal:** Identify controllable delay factors for operational planning

---

## 📦 Libraries Used
- **Data Processing:** pandas, numpy
- **Visualization:** matplotlib, seaborn
- **Machine Learning:** scikit-learn, xgboost
- **Model Explainability:** SHAP (Kernel crash during OAI evaluation)

---

## 🚀 How to Run

1. Clone the repository:
```bash
git clone https://github.com/yourusername/flight-delay-analysis.git
cd flight-delay-analysis




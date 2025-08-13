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

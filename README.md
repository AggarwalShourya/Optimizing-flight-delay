✈️ Optimizing Air Travel – Flight Delay Analysis & Prediction
📌 Project Overview
This project focuses on analyzing, predicting, and understanding flight delays using historical airline data.
We perform extensive Exploratory Data Analysis (EDA), feature engineering, and apply Machine Learning models to classify and predict delays.

The dataset includes delay causes, airline details, airports, and time-related features.
The aim is to uncover patterns, priority delay causes, and predictive insights for operational improvements.

📂 Data Sources
Airline_Delay_Cause.csv – Flight delay records and causes

Download_Column_Definitions.xlsx – Column descriptions

🔍 Key Analyses & Findings
1. Exploratory Data Analysis
Delta Airlines @ ATL – Highest delay counts for a single month.

DFW Airport –

Highest weather-related delays in a single month.

Highest security-related delays (indicating strict protocols).

Seasonality Impact – Minimal; weather-related delays consistent across months.

Visuals Generated:

Top 20 airports by weather, carrier, and security delays

Delay trends over months

Airport & airline delay distributions

2. Feature Engineering
Custom features were added to improve prediction:

Carrier-Airport Delay Score – Avg. carrier-caused delay per airport.

Weather-Month Score – Avg. weather delays per month.

Security-Airport Score – Avg. security delays per airport.

Delay Rate – arr_del15 / arr_flights (threshold: 0.2 for classification).

Operational Adjustability Index (OAI) – Weighted score focusing on controllable delays:

OAI
=
2.0
×
Carrier Delay
+
2.0
×
Late Aircraft Delay
+
1.5
×
NAS Delay
+
1.0
×
Weather Delay
+
0.5
×
Security Delay
OAI=2.0×Carrier Delay+2.0×Late Aircraft Delay+1.5×NAS Delay+1.0×Weather Delay+0.5×Security Delay
3. Machine Learning Models
Classification (Delay Prediction)
Target: is_delayed (1 if delay rate > 0.2, else 0)

Models Used:

Random Forest Classifier

XGBoost Classifier (Best performer)

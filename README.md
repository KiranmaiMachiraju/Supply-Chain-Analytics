# Supply Chain Analytics & Machine Learning Pipeline

## Project Overview
This project implements an **end-to-end analytics and machine learning workflow** on supply chain shipment data to analyze operational performance, model delivery delays, detect anomalies, and forecast product demand. The notebook reflects a realistic analytical pipeline, progressing from exploratory analysis to feature engineering and predictive modeling.

The focus is on **business-relevant insights**, model interpretability, and practical applicability rather than academic experimentation.

---

## Dataset Summary
- **Total Records:** 9,215 shipment-level observations  
- **Data Type:** Structured, order-level operational data  
- **Key Dimensions:**
  - Orders & Dates
  - Customers & Products
  - Carriers, Service Levels, Plants, Ports
- **Key Measures:**
  - Unit Quantity
  - Shipment Weight
  - Ship Ahead / Ship Late Day Counts

---

## Notebook Structure & Analysis Flow

### 1. Data Loading & Exploration
- Loaded shipment data and validated schema, data types, and record counts.
- Checked for missing values and duplicates.
- Analyzed distributions of **unit quantity** and **shipment weight**.
- Identified top customers contributing to shipment volume and weight.
- Established baseline understanding of operational concentration and skew.

**Outcome:**  
Confirmed data suitability for downstream modeling and identified key drivers of shipment volume.

---

### 2. Feature Engineering
Business-driven features were created to support predictive modeling:

- **Delivery Delay Metric:**  
  Net delay calculated using ship-ahead and ship-late day counts.
- **Temporal Features:**  
  Extracted order month and weekday to capture ordering patterns.
- **Weight-Based Features:**  
  Total shipment weight and weight-per-unit metrics.
- **Categorical Encoding:**  
  Operational dimensions (carrier, service level, ports, customers, plants) encoded for ML compatibility.
- **Target Variable:**  
  Binary delay flag (`is_delayed`) for classification modeling.

**Outcome:**  
Converted raw operational data into model-ready features while preserving interpretability.

---

### 3. Machine Learning Models

#### Delay Prediction
- **Regression:**  
  Random Forest Regressor used to predict the number of delay days.
- **Classification:**  
  Random Forest Classifier used to predict whether a shipment will be delayed.

Tree-based models were selected due to their ability to:
- Handle mixed feature types
- Capture non-linear relationships
- Require minimal feature scaling

**Evaluation Metrics Used:**  
MAE, RMSE, R², Accuracy, Precision, Recall, F1-score

---

### 4. Anomaly Detection
- Applied **Isolation Forest** to identify shipments that deviate significantly from typical operational behavior.
- Approximately **2% of shipments** were flagged as anomalous.

**Interpretation:**  
Anomalies may represent operational exceptions, data quality issues, or high-risk shipments requiring investigation.

---

### 5. Demand Forecasting
- Aggregated shipment data at the **monthly product level**.
- Implemented **rolling average forecasting** as a transparent baseline approach.

**Rationale:**  
Rolling averages provide an interpretable benchmark suitable for operational planning discussions and model comparison.

---
## Key Insights

- The dataset represents a **non-delayed operational snapshot**, with no observed shipment delays across orders.
- Shipment volume and weight are **highly concentrated among a small subset of customers and products**.
- Operational activity is unevenly distributed across carriers and plants, highlighting potential dependency risks.
- Anomaly detection identified a small percentage of shipments with unusual characteristics based on weight and quantity patterns.
- Aggregated demand patterns provide a usable signal for short-term forecasting despite limited temporal depth.

---

## Design Decisions
- Prioritized **interpretability and business usability** over overly complex models.
- Selected algorithms suitable for operational datasets with categorical-heavy features.
- Structured the notebook to mirror a real-world analytics workflow rather than isolated experiments.

---

## Business Value
This project demonstrates how analytics and machine learning can:
- Predict shipment delay risk before execution
- Identify operational outliers proactively
- Support demand planning with data-backed forecasts
- Enable data-driven logistics and carrier discussions

---

## Tools & Technologies
- **Language:** Python  
- **Libraries:** Pandas, NumPy, Scikit-learn, Matplotlib  
- **Environment:** Databricks / Jupyter Notebook  
- **Version Control:** GitHub  

---

## Limitations & Future Enhancements
- Introduce advanced forecasting models (ARIMA, Prophet, LSTM).
- Incorporate cost, supplier reliability, and product hierarchy features.
- Integrate model outputs into an interactive BI dashboard.
- Transition from batch analysis to a production-grade ML pipeline.

---

## Skills Demonstrated
- Exploratory Data Analysis  
- Feature Engineering for Machine Learning  
- Regression & Classification Modeling  
- Anomaly Detection  
- Time-Series Aggregation  
- Business-Focused Insight Communication  

---

## Author
**Kiran Machiraju**  

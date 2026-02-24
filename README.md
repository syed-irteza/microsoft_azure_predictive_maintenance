# Microsoft Azure Predictive Maintenance Analysis (PdM)

## 📌 Purpose of the Project

This project performs a data-driven predictive maintenance analysis
using the Microsoft Azure Predictive Maintenance dataset.

Objectives: - Predict machine failure within the next 24 hours -
Identify leading indicators of breakdown - Evaluate maintenance
effectiveness - Generate actionable risk scores

## 📁 Dataset Overview

-   PdM_telemetry.csv → Sensor readings (volt, rotate, pressure,
    vibration)
-   PdM_errors.csv → Error logs
-   PdM_failures.csv → Failure events
-   PdM_maint.csv → Maintenance records
-   PdM_machines.csv → Machine metadata

## 🧹 Data Engineering

-   Datetime parsing
-   Duplicate removal
-   Event one-hot encoding
-   Rolling 24-hour statistics
-   Failure labeling (next 24h)

## 📊 Analysis Performed

1.  Rolling sensor mean & volatility
2.  Error accumulation detection
3.  Maintenance impact analysis
4.  Failure risk segmentation
5.  Random Forest baseline model
6.  Feature importance ranking
7.  Machine-level risk scoring

## 📈 Key Insights

-   Sensor volatility increases before failure
-   Error frequency spikes precede breakdown
-   Older machines exhibit higher risk
-   Recent maintenance reduces near-term failure probability

## 🧠 Business Value

-   Reduced downtime
-   Proactive maintenance scheduling
-   Inventory optimization
-   Risk-based asset prioritization

## 🧰 Technologies Used

Python (Pandas, NumPy, Scikit-learn, Matplotlib) Jupyter Notebook /
Google Colab

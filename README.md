# Predictive Maintenance Analysis (Azure PdM Dataset)

## 📌 Purpose of the Project

This project performs a **data cleaning + exploratory analysis (EDA)** of an industrial **Predictive Maintenance (PdM)** dataset consisting of **telemetry**, **error logs**, **maintenance events**, **machine metadata**, and **failure events**.

The goal is to uncover **operational risk patterns** and translate them into **business recommendations** for reducing downtime and improving maintenance planning.

## ✅ Core Questions Answered

1. **Which component drives the most downtime events?**  
2. **Which machine model fails most frequently?**  
3. **Do older machines fail more often?**  
4. **Do sensors show early warning signals before specific failure types?**  
5. **Are error logs correlated with failures?**  
6. **Is maintenance mostly preventive or reactive (timing effectiveness)?**

> **Note on “downtime”:** The dataset does not include repair duration. In this analysis, **failure event counts** are used as a **downtime proxy** (more failures ⇒ more likely downtime impact).

---

## 📁 Data Files

| File | Description |
|------|-------------|
| `PdM_telemetry.csv` | Hourly sensor readings (volt, rotate, pressure, vibration) |
| `PdM_errors.csv` | Error events (error1–error5) |
| `PdM_maint.csv` | Maintenance events (component replacements) |
| `PdM_failures.csv` | Failure events (comp1–comp4) |
| `PdM_machines.csv` | Machine attributes (model, age) |

---

## 🧼 Cleaning Workflow (What to do)

- Convert `datetime` columns with robust parsing (`errors='coerce'`)
- Drop rows with invalid timestamps
- Remove duplicates
- Validate hourly telemetry frequency per machine
- Standardize column names (`machine_id`, `error_id`)
- Build **joined analytical table** by machine-hour for EDA

---

## 🔍 Analysis Performed

### 1) Component Downtime Proxy
- Counted failures by component to identify highest downtime driver.

### 2) Model Risk
- Computed **failures per machine** by model to compare reliability.

### 3) Age Risk
- Compared failure rates for machines **older than 12 years** vs younger machines.

### 4) Sensor Early-Warning Signals
- Measured **24-hour pre-failure sensor shift** vs each machine’s baseline.
- Focused on **vibration** to test comp4 early-warning behavior.

### 5) Error Logs vs Failures
- Measured correlation between **error frequency** and **failure frequency** at machine level.

### 6) Maintenance Timing
- Estimated **hours since last maintenance** at each failure timestamp to assess whether maintenance is preventive or reactive.

---

## 📊 Key Results & Insights

### 1) Component with Highest Downtime Proxy
- **comp2** has the highest failure count: **259 events (34.0%)** out of **761** total failures.

### 2) Highest-Risk Model
- **model1** has the highest average failures per machine: **11.81**.

### 3) Age Risk (Older than 12 Years)
- Machines **age > 12**: **9.73 failures/machine**  
- Machines **age <= 12**: **5.57 failures/machine**  
- **Risk multiplier:** ~**1.75x**

### 4) Vibration Spikes Before comp4 Failures
- Average vibration in the **24 hours before comp4 failures** is **+24.3%** above baseline.

### 5) Error Logs Correlate with Failures
- Machine-level correlation between **error counts** and **failure counts**: **r = 0.54**  
  (machines with more errors tend to experience more failures).

### 6) Maintenance Timing Suggests Reactive Pattern
- **97.6%** of failures occur at the **same timestamp as a maintenance event**, indicating maintenance is often **corrective/reactive**.
- Recommendation: shift toward **preventive maintenance**, targeted using **model + age + sensor signals**.

---

## 🧰 Technologies Used

- **Python:** pandas, numpy, matplotlib  
- **Methods:** time-series aggregation, rolling windows, correlation analysis, segment-based pre-failure analysis  
- **Deliverables:** README + PDF report

---

## 📈 Business Value

This analysis supports:
- **Downtime reduction** by prioritizing **comp2** reliability efforts
- **Risk-based maintenance scheduling** (model1 + age>12 prioritized)
- **Early-warning monitoring** (vibration-based alerts for comp4 risk)
- **Process improvement** by identifying reactive maintenance patterns and enabling preventive strategies

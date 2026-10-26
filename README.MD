# 🚛 Supply Chain & Logistics Fleet Operations Analysis

[![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-Latest-orange.svg)](https://pandas.pydata.org/)
[![Statsmodels](https://img.shields.io/badge/Statsmodels-Latest-green.svg)](https://www.statsmodels.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 📌 Project Overview
This project performs an end-to-end data analytics optimization on a massive operational database consisting of over 85,000+ relational logistics records tracking a fictional Class 8 trucking company over a 3-year period (2022–2024). 

By executing multi-table joins, exploratory data analysis (EDA), time-series asset tracking, and **LOWESS (Locally Weighted Scatterplot Smoothing) non-parametric regressions**, this project answers business-critical questions regarding lane profitability, vehicle lifecycle costs, maintenance scheduling, and seasonal demand.

---

## 🛠️ Tech Stack & Dependencies
* **Data Manipulation:** `pandas`, `numpy`
* **Statistical Modeling & Regression:** `statsmodels`
* **Data Visualization:** `matplotlib`, `seaborn`
* **Environment/Format:** Jupyter Notebook

---

## 📂 Data Architecture & Relational Schema
The analytics engine ingests normalized relational schemas mapping across 14 tables. The key functional areas include:
* **Core Reference Tables:** `drivers.csv` (150 records), `trucks.csv` (120 records), `customers.csv` (200 records), `routes.csv` (60 pairs).
* **Transactional Logs:** `loads.csv` (57k+ records), `trips.csv` (57k+ records), `fuel_purchases.csv` (131k+ records), `maintenance_records.csv` (6.5k records).
* **Aggregated Performance Metrics:** `driver_monthly_metrics.csv`, `truck_utilization_metrics.csv`.

---

## 📊 Key Executive Findings & Data Discoveries

### 1. Route Margin Profitability (Net Fuel & Accessorials)
* **Objective:** Find the most profitable routes after accounting for high fuel surcharges and accessorial drains.
* **Code Implementation:** Aggregates load revenue and dynamically maps net profit deductions by `route_id`.
* **Top Asset Lane:** Route **`RTE00016`** leads fleet profitability generating a clean net profit floor of **\$9,281,621.77**, closely followed by `RTE00012` (\$8,970,770.01).

### 2. Driver Tenure vs. Fleet Performance Correlations
* **Fuel Efficiency Correlation:** **`0.108`** (Very weak positive relationship). Experienced driver habits yield marginally tighter fuel controls.
* **On-Time Performance Correlation:** **`0.032`** (Zero statistical relationship). Driver tenure inside the company does not strictly dictate delivery punctuality, implying routing bottlenecks or detention delays out of the driver's control.

### 3. Predictive TCO Preventive Maintenance Interval
* **Methodology:** Merged monthly time-series maintenance costs alongside preventable safety incident penalty records. Applied a **LOWESS non-parametric Cost Valley model**.
* **Operational Optimization Rule:** Every individual Class 8 truck asset should undergo a scheduled preventive maintenance cycle precisely every **48 days** to hit the projected minimum Total Cost of Ownership (TCO) floor.

* **Dynamically Detected Assets:**     120 active units
* **OPTIMAL PM INTERVAL PER ASSET:**   48.33 DAYS (~7 Weeks)
* **Projected Minimum TCO Floor:**     Reached at optimal cadence curve valley minimum.


### 4. High-Value Customer Profiling
* **Top Performer:** Customer **`CUST00187`** stands out as the highest-value client. It maximizes asset returns with an excellent actual revenue load profile of **\$7,381.21 per load** matched with highly aggressive **15-day payment credit terms** to optimize company cash flows.

### 5. Seasonal Capacity and Asset Utilization Trajectories
* Fleet utilization hits maximum capacity peaks in **June** and **October** (Q4 volume surges).
* Marked operational throughput and cash-flow dips occur simultaneously in **February** and **November/December**, leaving opportunities for planned container positioning shifts during these windows.

### 6. Safety Incidents by Driver Experience
* **Pattern:** Preventable accidents/moving violations peak drastically in drivers with **0–5 years of CDL experience**. 
* The accident rate plummets by over 60% as drivers shift past the 10-year experience baseline, signaling that the company should target safety tracking toward newer hires.

---

## 🚀 How to Run and Reproduce
1. Clone this repository to your local architecture:
   ```bash
   git clone https://github.com/yourusername/logistics-operations-analysis.git
   cd logistics-operations-analysis
   ```
2. Download the source `.csv` datasets and position them within a structured directory named `data/` in the root folder.
3. Install required Python packages:
   ```bash
   pip install -r requirements.txt
   ```
4. Fire up the Jupyter environment and execute all cells in sequence:
   ```bash
   jupyter notebook
   ```
   Open and execute `logistics_fleet_analysis.ipynb`.

---
## 📜 Source 

**Logistics Operations Database by Yogape Rodriguez**
https://www.kaggle.com/datasets/yogape/logistics-operations-database/data

---

## 📜 License
This project is open-source and available under the terms of the [MIT License](https://opensource.org/licenses/MIT).
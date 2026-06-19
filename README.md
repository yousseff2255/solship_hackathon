# ⚡ Energy AI Forecaster & Battery Optimizer

## Welcome to the repository for the **Energy AI Management System**! This project was developed during a high-frequency Energy AI Hackathon to tackle two critical challenges in smart grid management: accurately forecasting electricity load and executing an optimal battery dispatch strategy using predictive control.

## 🏗️ System Architecture

The repository contains an end-to-end pipeline that combines machine learning forecasting with a mathematical optimization framework:

```text
┌────────────────────────┐
│  Historical Grid Data  │
└───────────┬────────────┘
            ▼
┌────────────────────────┐
│     XGBoost Model      │  ──► Predicts future load demands
│   (Load Forecaster)    │
└───────────┬────────────┘
            ▼
┌────────────────────────┐
│ Causal Model Predictive│
│    Control (MPC)       │  ──► Optimizes charge/discharge cycles
└───────────┬────────────┘
            ▼
┌────────────────────────┐
│ Optimal Grid Dispatch  │  ──► Minimizes costs & peak grid reliance
└────────────────────────┘

```

---

## 📁 Repository Structure

```text
energy_ai_hackathon/
├── forecaster + optimizer.ipynb   # Main Jupyter notebook containing data pipeline & models
├── data/                          # Market pricing and historical energy
├── README.md                      # Project documentation

```

---

## 🧠 Core System Modules

### 1. Load Forecaster (Machine Learning Layer)

- **Model Stack:** Built using **XGBoost** (Extreme Gradient Boosting) to capture complex, non-linear patterns in high-frequency energy consumption data.
- **Features:** Processes historical grid loads, timestamps, and temporal trends to output highly accurate, short-term energy demand forecasts.

### 2. Battery Dispatch Optimizer (Control Layer)

- **Strategy:** Implements a causal **Model Predictive Control (MPC)** framework.
- **Logic:** \* Looks ahead at the predicted load curve and fluctuating market prices.
- Calculates the mathematically optimal times to charge the battery bank (when grid energy is cheap or demand is low) and discharge it (during peak hours to save costs).
- Enforces strict physical hardware constraints (battery capacity limits, maximum charge/discharge rates, and efficiency losses).

---

## 📡 Pipeline Workflow

1. **Feature Engineering:** Historical load data is cleaned, structured, and transformed into lag features and rolling windows.
2. **Train & Predict:** The XGBoost model trains on the processed data to forecast upcoming grid demand cycles.
3. **Optimize:** The predictive control loop takes the forecast profile, evaluates market pricing, and runs an algorithmic optimizer to generate an ideal battery schedule.
4. **Evaluate:** Outputs metrics visualizing cost reductions, peak-shaving efficiency, and battery state-of-charge (SoC) profiles over time.

---

## 🛠️ Requirements & Stack

- **Language:** Python
- **Data & ML:** `pandas`, `numpy`, `xgboost`, `scikit-learn`
- **Optimization & Math:** `scipy.optimize` or `cvxpy` (for handling the MPC matrix formulations)
- **Visualization:** `matplotlib`, `seaborn`

---

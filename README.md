# ⚡ Delhi Electricity Demand Prediction System

[![Python](https://img.shields.io/badge/Python-3.11%20%7C%203.14-blue.svg)](https://www.python.org/)
[![React](https://img.shields.io/badge/Frontend-React%20%2B%20Vite-61DAFB.svg)](https://reactjs.org/)
[![Flask](https://img.shields.io/badge/Backend-Flask-000000.svg)](https://flask.palletsprojects.com/)
[![ML](https://img.shields.io/badge/ML-XGBoost%20%7C%20LightGBM%20%7C%20CatBoost-FF6F00.svg)](https://catboost.ai/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

A machine learning-powered web platform designed to forecast 24-hour electricity demand curves across Delhi state and its 5 distribution regions (DISCOMs). The system combines an **ensemble of CatBoost, XGBoost, and LightGBM** models with automated weather integration from Open-Meteo.

---

## 🌟 Key Features

- 🔮 **24-Hour Multi-Region Demand Forecasting:** Simultaneous hourly prediction for Delhi State and DISCOM sub-regions (`BRPL`, `BYPL`, `NDPL`, `NDMC`, `MES`).
- 🧠 **Weighted Ensemble ML Model:** Blends CatBoost, XGBoost, and LightGBM with pre-evaluated regional weights for optimal accuracy.
- 🌤️ **Automated Weather Feature Extraction:** Fetches real-time hourly temperature, humidity, feels-like temperature, wind speed, and precipitation via Open-Meteo API.
- 📊 **Peak & Off-Peak Analytics:** Automatically identifies daily peak demand (MW), peak hour, minimum demand, and total MWh energy load.
- 📅 **Domain Knowledge & Seasonality:** Integrates cyclic time encodings (`sin/cos`), Delhi public holiday calendar, and seasonal peak window shifting (Summer, Monsoon, Winter).
- 💻 **Modern Responsive UI:** Built with React, Vite, and interactive visualization charts.

---

## 📁 Repository Structure

```text
.
├── electricity-demand/
│   ├── backend/                                   # Flask API Server
│   │   ├── app.py                                 # Core API & prediction engine
│   │   ├── models/                                # Trained ensemble model weights (.pkl)
│   │   └── requirements.txt                       # Backend Python dependencies
│   │
│   └── frontend/                                  # React + Vite Application
│       ├── src/                                   # Components, Pages, & UI logic
│       └── package.json                           # Frontend NPM dependencies
│
├── DataSet_Training/                              # Notebooks & ML Training Pipeline
│   ├── Training-80-20-Final.ipynb                 # Model evaluation (80-20 split)
│   ├── FullDataTrainingFinal.ipynb                # Production model training
│   ├── WEATHER DATA FETCH AND CONVERSION.ipynb    # Weather data pipeline
│   ├── SLDC DATA FETCH.ipynb                      # Delhi SLDC electricity data fetcher
│   ├── Delhi_Weather_5M.csv                       # Processed weather dataset
│   └── delhi_sldc_5min_2022_2026.csv              # Historical electricity load dataset
│
└── README.md
```

---

## 🧠 Machine Learning Architecture

| Model | Purpose | Strength |
| :--- | :--- | :--- |
| **XGBoost** | Gradient Boosting | Fast gradient-driven tree optimization |
| **LightGBM** | Leaf-wise Tree Growth | Handles high-capacity numerical features efficiently |
| **CatBoost** | Categorical & Feature Interactions | High generalization on non-linear seasonal interactions |
| **Ensemble** | Weighted Averaging | Combines all three models for minimum variance |

---

## 🏙️ DISCOM Regions Covered

| Region ID | Area Description |
| :--- | :--- |
| **DELHI** | Delhi State Aggregated Total |
| **BRPL** | BSES Rajdhani Power Ltd (South & West Delhi) |
| **BYPL** | BSES Yamuna Power Ltd (East & Central Delhi) |
| **NDPL** | Tata Power Delhi Distribution Ltd (North Delhi) |
| **NDMC** | New Delhi Municipal Council (VIP/Govt Area) |
| **MES** | Military Engineer Services (Delhi Cantonment) |

---

## 🚀 Quick Start (Local Setup)

### 1. Clone the repository
```bash
git clone https://github.com/Sjoshi10262/PowerDemand.git
cd PowerDemand
```

### 2. Run Backend (Flask API)
```bash
cd electricity-demand/backend
pip install -r requirements.txt
python app.py
```
> Server will start at `http://127.0.0.1:5000`

### 3. Run Frontend (React UI)
```bash
cd electricity-demand/frontend
npm install
npm run dev
```
> UI will start at `http://localhost:5173` (or `5174`)

---

## 📄 License
Distributed under the MIT License. See `LICENSE` for details.

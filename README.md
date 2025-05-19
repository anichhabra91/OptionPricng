
# 📈 Apple Options Pricing & Volatility Forecasting (2016–2023)

This project models implied volatility and prices options for Apple Inc. (AAPL) using historical options data from **2016 to 2023**, sourced from **Kaggle**. It compares Black-Scholes and Monte Carlo Simulation approaches, and uses **Random Forest Regressors** to forecast implied volatility (IV) from key features such as moneyness, strike distance, and days to expiration.

---

## 📊 Dataset

- **Source**: [Kaggle: Apple Options Data (2016–2023)](https://www.kaggle.com/datasets/kylegraupe/aapl-options-data-2016-2020)
- **Additional**: Risk-free rate from `^FVX` via `yfinance`

---

## 🎯 Objectives

- Estimate historical annualized volatility from stock prices
- Price options using:
  - **Black-Scholes**
  - **Monte Carlo Simulation (MCS)**
- Use **ML (Random Forest)** to predict implied volatility
- Evaluate pricing accuracy and feature influence

---

## 🧠 ML Model Performance

Trained **Random Forest Regressors** separately for call and put implied volatility (`call_iv`, `put_iv`).

### 🔹 Model 1 (Use ML to predict Volatility and MCS to calculate prices)
**Call IV**
- **R²**: 0.9109

**Put IV** 
- **R²**: 0.9738

### 🔹 Model 2 (Use ML to predict Prices)
**Call IV**
- **R²**: 0.9999

**Put IV**
- **R²**: 0.9998

---

## 🧮 Feature Importances

Below are the most influential features used to predict implied volatility:

| Rank | Feature              | Importance (Call) | Importance (Put) |
|------|----------------------|-------------------|------------------|
| 1    | `moneyness`          | 0.660             | 0.705            |
| 2    | `strike_distance`    | 0.322             | 0.264            |
| 3    | `time_to_expiry_days`| 0.010             | 0.016            |
| 4    | `strike`             | 0.0001            | 0.011            |
| 5    | `risk_free_rate`     | 0.001             | 0.003            |
| 6    | `underlying_last`    | 0.003             | 0.001            |
| 7    | `annualized_vol`     | 0.003             | 0.0004           |

---

## 📌 Methodology

- **Volatility Estimation**:  
  Used log returns and a 252-day rolling window to compute **annualized volatility**.

- **Option Pricing**:  
  Implemented both:
  - **Black-Scholes** (closed-form)
  - **Monte Carlo Simulation** for European call options

- **ML Modeling**:
  - Features: moneyness, strike distance, expiry, etc.
  - Target: `call_iv`, `put_iv`
  - Algorithm: Random Forest Regressor with 80-20 train-test split

---

## 📈 Future Work

- Use LSTM models for time-dependent volatility prediction

---

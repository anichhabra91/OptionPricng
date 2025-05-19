
# 📈 Apple Options Pricing & Volatility Forecasting (2016–2023)

This project models implied volatility and prices options for Apple Inc. (AAPL) using historical options data from **2016 to 2023**, sourced from **Kaggle**. It compares Black-Scholes and Monte Carlo Simulation approaches, and uses **Random Forest Regressors** to forecast implied volatility (IV) from key features such as moneyness, strike distance, and days to expiration.

---

## 📊 Dataset

- **Source**: [Kaggle: Apple Options Data (2016–2023)]([https://www.kaggle.com/datasets/kylegraupe/aapl-options-data-2016-2020])
- **Content**: Options chains for AAPL, including:
  - Call/Put bid-ask, last prices
  - Strike prices, expiration dates
  - Implied volatilities (IV)
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

### 🔹 Model 1 (Earlier Run)
**Call IV**
- **MSE**: 0.0651  
- **R²**: 0.9109

**Put IV**
- **MSE**: 0.0066  
- **R²**: 0.9738

### 🔹 Model 2 (Final Run with Cleaned Features)
**Call IV**
- **MSE**: 0.2808  
- **R²**: 0.9999

**Put IV**
- **MSE**: 0.2934  
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

## 🧰 Tech Stack

- Python, Jupyter Notebook  
- `pandas`, `numpy`, `matplotlib`, `seaborn`  
- `yfinance`, `scikit-learn`, `tqdm`, `scipy`

---

## 🚀 How to Run

1. Clone the repo  
2. Add the CSV file (`aapl_2016_2020.csv`) in the same directory  
3. Launch `project.ipynb` in Jupyter  
4. Run all cells sequentially

---

## 📈 Future Work

- Add GARCH models for volatility
- Use LSTM models for time-dependent volatility prediction
- Extend pricing to American options

---

## 📬 Contact

If you'd like to collaborate or have questions, feel free to reach out via issues or pull requests!

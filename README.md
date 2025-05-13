# SmartVaR: Machine Learning for Daily Market Risk Forecasting

🚨 A Machine Learning model that predicts extreme risk days in the S&P 500 using historical returns, volatility, and technical indicators.

---

## 📌 Project Overview

This project aims to predict whether a given trading day will breach the **historical Value at Risk (VaR)** at 95% confidence, using only market data.

We train a supervised ML model to classify daily returns as:
- `0` → normal market behavior
- `1` → extreme loss beyond the 5% historical threshold

---

## 📊 Data

- 📈 Asset: [`SPY`](https://finance.yahoo.com/quote/SPY) (ETF tracking the S&P 500)
- 📅 Period: 2010–2024
- 📦 Source: Downloaded using [`yfinance`](https://github.com/ranaroussi/yfinance)

---

## 🧠 Features

The following features were used to predict daily risk:

- **Lagged returns**: `Lag_1`, `Lag_2`, `Lag_5`
- **Rolling volatility**: `Volatility_10`, `Volatility_20`
- **Technical indicators**:
  - `SMA_10`: 10-day simple moving average
  - `RSI_14`: Relative Strength Index (14-day)
  - `Momentum_5`: 5-day momentum

---

## ⚙️ Model

- 🎯 **XGBoostClassifier** with:
  - `scale_pos_weight` to handle class imbalance
  - Custom probability threshold (`0.4`) to favor recall on extreme days

---

## ✅ Results

| Metric              | Value    |
|---------------------|----------|
| Accuracy            | 85.2%    |
| Recall (class 1)    | 63.2%    |
| Precision (class 1) | 20.3%    |
| F1-score (class 1)  | 30.8%    |

📉 Out of 731 test days, the model correctly identified 24 out of 38 extreme risk days.

---





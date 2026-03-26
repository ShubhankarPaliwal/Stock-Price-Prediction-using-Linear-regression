# Stock-Price-Prediction-using-Linear-regression
# 📈 Stock Price Prediction with Linear Regression

A beginner-friendly quantitative finance project that uses machine learning to predict next-day stock closing prices. Built with Python and fully runnable in Google Colab — no local setup required.

---

## 🔍 Overview

This project pulls historical stock data from Yahoo Finance, engineers a set of technical features (moving averages, momentum, volatility), and trains a Linear Regression model to forecast the next trading day's closing price. Results are evaluated with standard regression metrics and visualised with Matplotlib.

---

## 🛠️ Tech Stack

| Library | Purpose |
|---|---|
| `yfinance` | Download historical OHLCV data from Yahoo Finance |
| `pandas` | Data manipulation and feature engineering |
| `scikit-learn` | Model training, scaling, and evaluation |
| `matplotlib` | Visualising predictions and residuals |

---

## ⚙️ How It Works

1. **Data collection** — Downloads 2 years of daily OHLCV data for any ticker (default: `AAPL`)
2. **Feature engineering** — Creates predictive signals from raw prices:
   - Simple Moving Averages (SMA 5, 10, 20)
   - Exponential Moving Average (EMA 10)
   - Daily return (momentum)
   - High-low range (volatility proxy)
   - Volume change ratio
   - Lag features (yesterday's and 2-days-ago close)
3. **Train/test split** — 80% train / 20% test, preserving time order (no shuffling)
4. **Feature scaling** — `StandardScaler` fitted on training data only to prevent leakage
5. **Model training** — Ordinary Least Squares Linear Regression via scikit-learn
6. **Evaluation** — MAE, RMSE, and R² on the held-out test set
7. **Prediction** — Forecasts the next trading day's closing price
8. **Visualisation** — Actual vs predicted price chart + residuals plot

---

## 📊 Sample Output

```
✅  Downloaded 502 rows  (2023-03-27 → 2025-03-26)
🔀  Train: 401 samples  |  Test: 101 samples
✅  Model trained!

  MAE  : $1.83
  RMSE : $2.41
  R²   : 0.9912

📌  Last known close : $213.49
🔮  Predicted close  : $214.76  ▲ +0.60%
```

---

## 📁 Project Structure

```
stock-prediction/
├── stock_prediction_colab.ipynb   # Main notebook (Colab-ready)
├── stock_prediction.py            # Plain Python script version
├── requirements.txt               # Dependencies
└── README.md
```

---

## 📦 Installation (local)

```bash
git clone https://github.com/your-username/stock-prediction.git
cd stock-prediction
pip install -r requirements.txt
python stock_prediction.py
```

---

## ⚠️ Disclaimer

This project is for **educational purposes only**. Predictions made by this model should not be used as financial advice or to make real investment decisions. Stock markets are inherently unpredictable and past performance does not guarantee future results.

---

## 📌 Future Improvements

- [ ] Add RSI, Bollinger Bands, and MACD as features
- [ ] Compare against Random Forest and XGBoost models
- [ ] Add walk-forward validation for more realistic backtesting
- [ ] Build an interactive ticker selector with `ipywidgets`

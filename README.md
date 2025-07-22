# Forecasting Bond Yield Spread Using Macroeconomic Factors

**Authors**: Haining Han, Yuting Bu, Zhiyuan Li, Changle Li  
**Date**: December 6, 2024  

---

## Overview

This project develops and compares time series and machine learning models to forecast the U.S. 10Y–2Y Treasury yield spread using macroeconomic indicators. The yield spread is a key predictor of economic cycles and monetary policy impacts.

---

## Data

- **Target**: 10Y–2Y Treasury Yield Spread (`T10Y2YM`)  
- **Features** (1973–2023, monthly):  
  - CPI (`CPIAUCSL`), PPI (`PPIACO`), Unemployment (`UNRATE`), Industrial Production (`INDPRO`), Federal Funds Rate (`FEDFUNDS`), VIX (`VIXCLS`), Nonfarm Payrolls (`PAYEMS`), Recession Probabilities (`RECPROUSM156N`)  
- **Source**: FRED API via `tidyquant::tq_get()`

---

## Models

| Model | Description                                   |
|-------|-----------------------------------------------|
| 1     | TSLM with macroeconomic predictors            |
| 2     | TSLM + Cross-Validation                       |
| 3     | ETS (Exponential Smoothing State Space)       |
| 4     | ARIMA                                         |
| 5     | Regression with ARIMA errors                  |
| 6     | TSLM with PCA-reduced macro factors           |
| 7     | OLS with PCA components                       |
| 8     | Dynamic regression with lags & PCs            |
| 9     | VAR (Vector Autoregression) + IRFs            |
| 10    | Feedforward Neural Network with PCs           |

---

## Results Summary

- **Best trade-off (accuracy & interpretability)**: Model 8 – Dynamic regression with lagged PCs.  
- **Lowest forecast error (RMSE)**: Model 9 – VAR with PCs.  
- PCA effectively reduced multicollinearity, enabling stable models.  
- Pure time-series models (ARIMA, ETS) performed well for short horizons but lacked explanatory power.

---

## Dependencies

R packages:  

```r
dynlm, tidyverse, tidyquant, tsibble, fable, feasts, forecast,
vars, nnet, caret, tseries, ggplot2, lubridate



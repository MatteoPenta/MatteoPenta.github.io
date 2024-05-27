---
title: Time-Series Forecasting - Predicting Stock Prices Using An ARIMA Model
draft: false
tags:
  - work_in_progress
  - article
related:
  - "[[Time Series Forecasting]]"
timestamp: "202405111904"
---

# Time-Series Forecasting - Predicting Stock Prices Using An ARIMA Model

## 1. Introduction
- **Non-stationary data**: data whose statistical properties (e.g. the mean and standard deviation) are not constant over time.
- **Time series**: a sequence taken at successive equally spaced points in (discrete) time.

## 2. The Autoregressive Integrated Moving Average (ARIMA) model
- **Autoregressive model**: the output variable depends linearly on its own previous values and on a stochastic term.
- **Integrated**: the model employs **differencing of raw observations** (e.g. it subtracts an observation from an observation at the previous time step) in order to make the time-series **stationary**.
- 

--- 
# References
- [Towards Data Science article | Medium](https://towardsdatascience.com/time-series-forecasting-predicting-stock-prices-using-an-arima-model-2e3b3080bd70)
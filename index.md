# Marilyn's Dow Jones Index Project

## **Introduction**  
This project explores the application of machine learning to investigate trends in stock price data using the Dow Jones Index dataset. While stock price forecasting is challenging due to the stochastic nature of markets, this analysis aims to uncover patterns and relationships within the data.  

Two approaches are considered:  
1. Forecasting stock price trends using autoregression models to capture temporal dependencies.  
2. Investigating feature relationships, such as the connection between trading volume and volatility.  

To ensure meaningful comparisons across stocks, price data is normalized by expressing changes as percentage differences.

---

## **Data**  
The dataset is the Dow Jones Index dataset from the UCI Machine Learning Repository, which contains weekly stock data from 2011. It includes attributes like opening, closing, high, and low prices, as well as trading volumes. The data is normalized to percentage changes for easier analysis across different stock values.  

### **Data Visualization**  
Below is a plot of the weekly percentage changes in closing prices for stock 'AA':

![Figure 1: Weekly Percentage Change in Closing Price of Stock 'AA'](/assets/figures/stock_aa_pct_change.png)

---

## **Modeling**  
Initially, an autoregression approach was applied to predict stock price trends. This model uses historical data to forecast future prices, leveraging patterns in the time series. If forecasting proves unreliable, we pivot to examining feature relationships, such as the correlation between volume and price volatility, to uncover insights at the current time step.

Sample code snippet for autoregression:
```python
from statsmodels.tsa.ar_model import AutoReg
from sklearn.metrics import mean_squared_error

# Example of autoregression
model = AutoReg(train_data, lags=5)
model_fitted = model.fit()
predictions = model_fitted.predict(start=len(train_data), end=len(train_data)+len(test_data)-1)
error = mean_squared_error(test_data, predictions)
print(f"Mean Squared Error: {error}")

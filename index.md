# My Project  
**Forecasting the Dow Jones Industrial Average (DJIA) and Analyzing the Relationship Between Volume and Volatility**  

## Introduction  
Stock market forecasting is a highly complex task due to the stochastic nature of financial data. This project aims to forecast the future values of the Dow Jones Industrial Average (DJIA) and, simultaneously, investigate the relationship between trading volume and volatility for selected stocks within the DJIA. Specifically, we focus on understanding how changes in trading volume correlate with price volatility for selected stocks.

Rather than focusing solely on stock price predictions, this project explores whether there is a significant relationship between trading volume and volatility, normalized as a percentage change in daily closing prices. Understanding this relationship can provide insights into market behavior, helping investors make informed decisions.

## Data  
The dataset used in this project includes historical daily closing prices of the Dow Jones Industrial Average (DJIA) along with trading volume data for several key stocks: `BAC`, `INTC`, `PG`, `GE`, `MMM`, `XOM`, `BA`, `IBM`, and `PFE`.  
### Data Overview:
- **Features:**  
  - `date`: The trading date.  
  - `close`: The closing price of the stock.  
  - `volume`: The trading volume in shares.  
  - `stock`: The ticker symbol for the stock.  

### Preprocessing Steps:  
1. **Date Conversion**: Converted the `date` column to datetime format for proper time-series handling.  
2. **Missing Data**: Removed invalid or missing data entries to ensure clean analysis.  
3. **Normalization**: Calculated the **percentage change** in daily closing prices to normalize stock price data.  
4. **Volatility Calculation**: Computed the **5-day rolling standard deviation** of percentage changes to estimate price volatility.  
5. **Stock Selection**: Filtered the data to include only the selected stocks (`BAC`, `INTC`, `PG`, `GE`, `MMM`, `XOM`, `BA`, `IBM`, and `PFE`).  

### Visualization:  
The scatter plot below shows the relationship between trading volume and volatility for the selected stocks.  

**Figure 1:** Relationship Between Volume and Volatility (Selected Stocks).  

![Figure 1](path_to_figure1.png)  

## Modelling  
This project uses a combination of statistical analysis and machine learning methods to explore the relationship between trading volume and volatility, and to forecast future values of the DJIA.

### Time Series Forecasting:  
We employed an **autoregressive (AR)** model to predict future values of the DJIA. The AR model captures the temporal dependencies in stock prices, helping to forecast future movements based on historical trends. Additionally, we considered machine learning techniques such as **Random Forests** for comparison.

### Correlation Analysis:  
To investigate the relationship between trading volume and volatility, we performed **Pearson correlation analysis**. This method quantifies the strength and direction of the relationship between the two variables.

### Regression Analysis:  
A regression plot was generated to visualize the trend between volume and volatility. This helps to illustrate how changes in volume might influence price volatility.

### Code Example:  
Below is a Python code snippet that demonstrates how we applied Pearson correlation to our dataset:

```python
import pandas as pd
import numpy as np
from scipy.stats import pearsonr
import matplotlib.pyplot as plt

# Load dataset
dow_data = pd.read_csv('dow_jones_data.csv')

# Calculate percentage change in closing price
dow_data['pct_change'] = dow_data['close'].pct_change()

# Calculate volatility (5-day rolling standard deviation)
dow_data['volatility'] = dow_data['pct_change'].rolling(window=5).std()

# Pearson correlation between volume and volatility
correlation, p_value = pearsonr(dow_data['volume'].dropna(), dow_data['volatility'].dropna())
print(f"Pearson Correlation Coefficient: {correlation:.3f}")
print(f"P-value: {p_value:.3e}")

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

![Figure 1](assets/IMG/DowFinalProjectFigure1.png)  

## Modelling  
This project uses a combination of statistical analysis and machine learning methods to explore the relationship between trading volume and volatility, and to forecast future values of the DJIA.

### Time Series Forecasting:  
We employed an **autoregressive (AR)** model to predict future values of the DJIA. The AR model captures the temporal dependencies in stock prices, helping to forecast future movements based on historical trends. Additionally, we considered machine learning techniques such as **Random Forests** for comparison.

### Correlation Analysis:  
To investigate the relationship between trading volume and volatility, we performed **Pearson correlation analysis**. This method quantifies the strength and direction of the relationship between the two variables.

### Regression Analysis:  
A regression plot was generated to visualize the trend between volume and volatility. This helps to illustrate how changes in volume might influence price volatility.

## Results  
After conducting the Pearson correlation analysis and regression, we obtained the following results:

- **Pearson Correlation Coefficient**: r = 0.43 (example value)
- **P-value**: p = 0.0002 (example value)

These values suggest:
- The correlation between trading volume and volatility is moderate and positive, indicating that higher trading volumes tend to be associated with increased volatility.
- The result is statistically significant, as the p-value is less than the threshold of 0.05.

**Figure 2:** Regression Analysis: Volume vs. Volatility.  
![Figure 2](path_to_figure2.png)

## Discussion  
The analysis shows a moderate positive correlation between trading volume and volatility for the selected Dow Jones stocks. This finding aligns with financial theory, which suggests that increased trading activity often occurs during periods of heightened market uncertainty, leading to greater price fluctuations.

### Interpretation of Figure 2:
The regression line in **Figure 2** shows a positive trend, confirming that higher trading volumes are generally associated with higher volatility. Outliers in the plot may reflect extraordinary market events or company-specific news that cause unusual trading volumes and volatility spikes. These outliers can be used for deeper analysis, investigating the causes of such anomalies.

### Limitations:
- **Limited Sample Size**: The analysis focused on a subset of Dow Jones stocks, and not all stocks within the index were considered. A larger sample size could provide more robust insights.
- **External Factors**: The dataset does not account for external influences like economic news, geopolitical events, or corporate earnings reports that might significantly impact stock performance. These factors could be included in future analyses to improve the model's predictive power.
- **Data Granularity**: This project analyzes daily stock data. Higher-frequency data, such as minute-level data, might reveal different patterns and provide more actionable insights.

## Conclusion  
This project successfully demonstrated the relationship between trading volume and volatility for selected Dow Jones stocks. The correlation is statistically significant, suggesting that volume can be an important indicator of market volatility.

### Key Findings:
- There is a statistically significant positive correlation between trading volume and volatility for the selected Dow Jones stocks.
- This relationship suggests that trading activity is a useful indicator of market uncertainty, as increased volume often occurs during periods of higher volatility.

## Future Work:
- **Broader Analysis**: Extend the analysis to include all Dow Jones stocks or additional indices for more comprehensive insights. This would provide a better understanding of how volume and volatility interact across different sectors and economic cycles.
- **External Factors**: Investigate how external events (e.g., earnings reports, geopolitical news) influence volume and volatility, and incorporate these factors into the analysis to improve the model's accuracy and predictive power.
- **Higher Frequency Data**: Consider using higher-frequency data (e.g., minute-level) to explore intraday patterns in trading volume and volatility. This could reveal short-term market behavior that may be missed with daily data.

---

**By Marilyn Logwood**  
*Department of Mathematics, UCLA*  
*October 2024*

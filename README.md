# Cryptocurrency Price Prediction
## Predict Prices Using Machine Learning

**by Murat Tulca**

#### Summary
This project aims to predict cryptocurrency prices using machine learning. We will explore different ML models and evaluate their performance.<br>
A reasonably accurate price prediction model can help cryptocurrency traders by anticipating changes in prices and set up their trades accordingly.<br>
Let's find out if cryptocurrency prices be predicted using machine learning.

#### Data Source
The CryptoCompare.com API provides historical price data for cryptocurrencies.
The data can be retrieved as daily, hourly, or minutely data. In this project, we will be using daily data.

Below is a sample of bitcoin historical data retrieved using the [CryptoCompare API](https://min-api.cryptocompare.com):
```
	time    	high    	low     	open    	volumefrom	volumeto    	close   	conversionType
0	1610755200	37942.44	35395.88	36790.17	54226.28	1.995054e+09	36025.26	direct	
1	1610841600	36860.67	33854.83	36025.26	50913.30	1.806688e+09	35839.51	direct	
2	1610928000	37429.24	34784.40	35839.51	43063.97	1.554687e+09	36623.04	direct	
3	1611014400	37867.53	35917.28	36623.04	48457.45	1.787957e+09	35932.79	direct	
4	1611100800	36409.96	33519.59	35932.79	66302.02	2.316776e+09	35501.38	direct	
```
While there are multiple columns in this dataset that can potentially be helpful to us, our goal will be to predict the `close` price.

#### Methodology
In this project we will train models based on past (historical) price data to forecast future data.
We will explore the following ML models:
- ARIMA (Autoregressive integrated moving average)
- Linear Regression
- LSTM (Long short-term memory)

We will also create a base model that predicts the future `close` price as the exact same value as the previous day's `close` price.
Our goal is to beat the performance of the base model with the ML models above.
In each instance, we will try to predict the `close` price of bitcoin (or other cryptocurrency) for the past 90 days.
We will then evalute the results using MAPE (mean average percentage error) as our metric.

#### Results
The table below shows the best performing model of each type for predicting the `close` price of bitcoin.
```
              Model  Train Size  Predictions      MAPE  Run Time (s)  Window Size  Features
0              Base           1           30  0.017564           0.0          NaN       NaN
1             ARIMA         300           30  0.017886           0.5          NaN       NaN
2  LinearRegression         300           30  0.016671           0.3         60.0       1.0
3              LSTM         300           30  0.028890         301.0         60.0       1.0
```
#### Summary
We can see that the only model that managed to beat our Base model is Linear Regression, but by an extremely small amount. This suggests that using ML to make predictions on cryptocurrency prices using only the historical data as input does not yield better results than simply using the price of the previous day as the next day prediction.

#### Next Steps
A possible next step would be to use technical indicators as input features. Technical features are often used when making predictions in the real world. Another option would be to try to improve the LSTM model by using more layers and increasing training time. However, this is a computationally expensive approach.

#### Jupyter Notebook:

https://github.com/spybart/cryptocurrency_price_prediction/blob/main/cryptocurrency_price_prediction.ipynb
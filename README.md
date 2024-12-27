# Cryptocurrency Price Prediction
## Predict Prices Using Machine Learning

**by Murat Tulca**

#### Summary
This project aims to predict cryptocurrency prices using machine learning. We will explore different ML models and evaluate their performance.

A reasonably accurate price prediction model can help cryptocurrency traders by anticipating changes in prices and set up their trades accordingly.

Can cryptocurrency prices be predicted using machine learning?

#### Data Source
The CryptoCompare.com API provides historical price data for cryptocurrencies.
The data can be retrieved as daily, hourly, or minutely data. In this project, we will be using daily data.

Below is a sample of daily bitcoin price data retrieved using the CryptoCompare.com API:
```
	time    	high    	low     	open    	volumefrom	volumeto    	close   	conversionType
0	1610755200	37942.44	35395.88	36790.17	54226.28	1.995054e+09	36025.26	direct	
1	1610841600	36860.67	33854.83	36025.26	50913.30	1.806688e+09	35839.51	direct	
2	1610928000	37429.24	34784.40	35839.51	43063.97	1.554687e+09	36623.04	direct	
3	1611014400	37867.53	35917.28	36623.04	48457.45	1.787957e+09	35932.79	direct	
4	1611100800	36409.96	33519.59	35932.79	66302.02	2.316776e+09	35501.38	direct	
```
While there are multiple columns in this dataset that can potentially be helpful to us, our goal will be to predict the close price.

#### Methodology
In this project we will train models based on past (historical) price data to forecast future data.
As this is a time series problem, we will explore the following ML models:
- ARIMA (Autoregressive integrated moving average)
- XGBoost (eXtreme Gradient Boosting)
- LSTM (Long short-term memory)

We will also create a base model that predicts the future price as the exact same value as the previous day close price.
Our goal is to beat the performance of this base model with the ML models above.
In each instance, we will try to predict the close price of bitcoin (or other cryptocurrency) for the past 90 days, where each prediction is based on a model that is trained on the previous 60 days of close prices.
We will then evalute the results using MAPE (mean average percentage error) as our metric.

#### Results

      Model  Train Size  Predictions      MAPE  Run Time (s)
0      Base          30           90  0.018602           0.1
1     ARIMA          30           90  0.019380           1.2
2   XGBoost          30           90  0.018602           4.1
3      Base          60           90  0.018602           0.1
4     ARIMA          60           90  0.018820           0.9
5   XGBoost          60           90  0.018602           2.5
6      Base          90           90  0.018602           0.1
7     ARIMA          90           90  0.018815           1.0
8   XGBoost          90           90  0.018601           2.6
9      Base         120           90  0.018602           0.1
10    ARIMA         120           90  0.018671           1.0
11  XGBoost         120           90  0.018603           6.7

Because there is no seasonality in the historical price data, it is inaccurate to predict prices using the ARIMA model. When comparing the actual and predicted data, we can observe that the predictions seem to be 1 step behind the actual data. This is due to the fact that the model is making a prediction based on the trend of the historical data, which is not a guaranteed indicator of the direction the data will go.

Based on the current results, the ARIMA model is not a reliable way to predict prices, as it shows a delay during forecasting.

#### Next Steps
Using a technique known as window sliding, we can frame the task into a supervised learning problem. By doing so, we can utilize the suite of standard linear and nonlinear machine learning algorithms on this problem.

Another option would be to explore recurrent neural networks, which seems to a modern solution to time series tasks.

#### Jupyter Notebook:

https://github.com/spybart/cryptocurrency_price_prediction/blob/main/cryptocurrency_price_prediction.ipynb
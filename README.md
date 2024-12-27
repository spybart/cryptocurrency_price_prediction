# Cryptocurrency Price Prediction
## Predict Prices Using Machine Learning

**by Murat Tulca**

#### Executive summary
This project aims to predict cryptocurrency prices using machine learning. We will explore different ML models and evaluate their performance.

#### Rationale
Cryptocurrency prices are generally on the rise but are also very volatile. A reasonably accurate price prediction model can help cryptocurrency traders by anticipating changes in prices and set up their trades accordingly.

#### Research Question
Can cryptocurrency prices be predicted using machine learning?

#### Data Sources
The CryptoCompare.com API provides historical price data for cryptocurrencies. The data can be retrieved as daily, hourly, or minutely data.

#### Methodology
In this project we will train models based on past (historical) price data to forecast future data.
As this is a time series problem, we will explore the following ML models:
- ARIMA (Autoregressive integrated moving average)
- XGBoost (eXtreme Gradient Boosting)
- LSTM (Long short-term memory)

We will also create a base model that predicts the future price as the exact same value as the price of the previous day.
Our goal is to beat the performance of this base model with the ML models above.
In each instance, we will try to predict the close price of bitcoin (or other cryptocurrency) for the past 90 days, where each prediction is based on a model that is trained on the previous 60 days of close prices.
We will then evalute the results using MAPE (mean average percentage error) as our metric.

#### Results
Because there is no seasonality in the historical price data, it is inaccurate to predict prices using the ARIMA model. When comparing the actual and predicted data, we can observe that the predictions seem to be 1 step behind the actual data. This is due to the fact that the model is making a prediction based on the trend of the historical data, which is not a guaranteed indicator of the direction the data will go.

Based on the current results, the ARIMA model is not a reliable way to predict prices, as it shows a delay during forecasting.

#### Next Steps
Using a technique known as window sliding, we can frame the task into a supervised learning problem. By doing so, we can utilize the suite of standard linear and nonlinear machine learning algorithms on this problem.

Another option would be to explore recurrent neural networks, which seems to a modern solution to time series tasks.

#### Jupyter Notebook:

https://github.com/spybart/cryptocurrency_price_prediction/blob/main/cryptocurrency_price_prediction.ipynb
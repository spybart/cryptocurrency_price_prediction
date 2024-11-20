# Cryptocurrency Price Prediction
## Predict Prices Using Machine Learning

**by Murat Tulca**

#### Executive summary
This project aims to predict cryptocurrency prices using machine learning. By building models that are trained on historical data, future data will be predicted.

#### Rationale
Cryptocurrency prices are generally on the rise but are also very volatile. A reasonably accurate price prediction model can help cryptocurrency traders make profits by knowing when to buy and sell.

#### Research Question
Can cryptocurrency prices be predicted using machine learning?

#### Data Sources
The CryptoCompare API provides historical price data for cryptocurrencies. The data can be retrieved as daily, hourly, or minutely data.

#### Methodology
Because this is a time series problem, I will use the ARIMA model. Specifically, I will use the auto-ARIMA model, which automatically finds the optimal parameters for an ARIMA model based on the training data.

#### Results
Because there is no seasonality in the historical price data, it is inaccurate to predict prices using the ARIMA model. When comparing the actual and predicted data, we can observe that the predictions seem to be 1 step behind the actual data. This is due to the fact that the model is making a prediction based on the trend of the historical data, which is not a guaranteed indicator of the direction the data will go.

Based on the current results, the ARIMA model is not a reliable way to predict prices, as it shows a delay during forecasting.

#### Next Steps
Using a technique known as window sliding, we can frame the task into a supervised learning problem. By doing so, we can utilize the suite of standard linear and nonlinear machine learning algorithms on this problem.

Another option would be to explore recurrent neural networks, which seems to a modern solution to time series tasks.

#### Jupyter Notebook:

https://github.com/spybart/cryptocurrency_price_prediction/blob/main/cryptocurrency_price_prediction.ipynb
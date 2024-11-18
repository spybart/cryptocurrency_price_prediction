### Cryptocurrency Price Prediction

**by Murat Tulca**

#### Executive summary

#### Rationale
An accurate price prediction model will help cryptocurrency traders make profits.

#### Research Question
Can cryptocurrency prices be predicted using machine learning?

#### Data Sources
The CryptoCompare API provides historical price data for cryptocurrencies. The data can be retrieved as daily, hourly, or minutely data.

#### Methodology
Because this is a time series problem, I will use the ARIMA model on historical price data to forecast future prices. Specifically, I will use the auto-ARIMA model, which automatically finds the optimal parameters for an ARIMA model based on the training data.

#### Results
Because there is no seasonality in the historical price data, it is difficult to predict future prices using ARIMA. When comparing the actual vs predicted data, we can observe that the predictions seem to be 1 step behind the actual data. This is due to the fact that the model is making a prediction based on the trend of the historical data, which is not a guaranteed indicator of the direction the future data will go.

Based on the current results, this price prediction is not necessarily a reliable way to predict prices, as it shows a delay during forecasting.

#### Next Steps
Currently the ARIMA model is only trained on 1 feature, the price of the cryptocurrency. Perhaps by forecasting using multiple features, the model can forecast more accurately. One way to achieve this is to use the other features that are provided by the CryptoCompare API, which are the `high`, `low`, `open`, `volumefrom`, `volumeto`	fields. Another way would be to create various technical indicators by generating them from the price data.

Exploring other types of models that can work on time series can potentially yield better results.

#### Jupyter Notebook:

https://github.com/spybart/cryptocurrency_price_prediction/blob/main/cryptocurrency_price_prediction.ipynb
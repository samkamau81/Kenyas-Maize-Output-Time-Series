# Kenyas-Maize-Output-Time-Series
This is a time series project that utilizes Facebook prophet to predict what Kenya's Maize Output will be in 2027.
Time forecasting models use historical data to predict future values of these indicators, allowing analysts to anticipate economic trends and adjust policies accordingly.

I've created a simple Dashboard using Microsoft Power BI , a powerful tool for Data Visualization, to show how Kenya Maize Yield 
behaves interms of Imports and Exports , Location where it is grown and When is the yield mostly gotten. I have used data from FAO
(Food and Agriculture Organization) to come up with the dashboard and Time series analysis.

![image](https://user-images.githubusercontent.com/63351043/230066193-4e79fbc5-46d2-4f1a-a881-a90b404944b1.png)

- - - -

# Data Preparation 

## Handling Missing Data 
The most common methods to address missing data in time series are: 
- **Imputation**
When we fill in missing data based on observations about the entire data set.
- **Interpolation**
When we use neighboring data points to estimate the missing value. Interpolation can also be a form of imputation.
- **Deletion of affected time periods**
When we choose not to use time periods that have missing data at all
- **Smoothing Data**
__Smoothing data__ can be done for a variety of reasons, and often real-world time series data is smoothed before analysis, especially for visualizations that aim to tell an understandable story about the data. 

While outlier detection is a topic in and of itself, if you have reason to believe your data should be smoothed, you can do so with a moving average to eliminate measurement spikes, errors of measurement, or both. Even if the spikes are accurate, they
may not reflect the underlying process and may be more a matter of instrumentation problems; this is why it’s quite common to smooth data.

__Smoothing data__ is strongly related to imputing missing data, and so some of those techniques are relevant here as well. For example, you can smooth data by applying a rolling mean, with or without a lookahead, as that is simply a matter of the point’s
position relative to the window used to calculate its smoothed value.
When you are smoothing, you want to think about a number of questions:

**Why are you smoothing ?**

Smoothing can serve a number of purposes: 
- *Data preparation* - Is your raw data unsuitable? For example, you may know very high values are unlikely or unphysical, but you need a principled way to deal with them. Smoothing is the most straightforward solution.
- *Feature generation* - The practice of taking a sample of data, be it many characteristics about a person, image, or anything else, and summarizing it with a few metrics. In this way a fuller sample is collapsed along a few dimensions or down to a few
traits. Feature generation is especially important for machine learning.
Prediction - The simplest form of prediction for some kinds of processes is mean reversion, which you get by making predictions from a smoothed feature.
- *Visualization* - Do you want to add some signal to what seems like a noisy scatter plot? If so, what is your intention in doing so?

*Therefore __Smoothing data__ is the process of removing noise from a dataset*

![image](https://www.investopedia.com/thmb/AlWZjs7tasYiBJGyzVOl1cObsKU=/750x0/filters:no_upscale():max_bytes(150000):strip_icc():format(webp)/dotdash_Final_Strategies_Applications_Behind_The_50_Day_EMA_INTC_AAPL_Jul_2020-03-4913804fedb2488aa6a3e60de37baf4d.jpg)

#### Pros 
- Helps identify real trends by eliminating noise from the data 
- Allows for seasonal adjustments of economic data 
- Easily achieved through several techniques including moving averages 
#### Cons
- Removing data always comes with less information to analyze, increasing the risk of errors in analysis
- Smoothing may emphasize analysts' biases and ignore outliers that may be meaningful

***This being said, it is essential to smooth data despite its cons.***

### Moving average
The moving average model is probably the most naive approach to time series modelling. This model simply states that the next observation is the mean of all past observations.
### Exponential smoothing

You often won’t want to treat all time points equally when smoothing. In particular, you may want to treat more recent data as more informative data, in which case exponential smoothing is a good option. In contrast to the moving average where each point where data was missing could be imputed to the mean of its surrounding points—exponential smoothing is geared to be more temporally aware, weighting more recent points higher than less recent points. So, for a given window, the nearest point in time is weighted most heavily and each point earlier in time is weighted exponentially less (hence the name).
This can also include Double , triple and the simple exponential smoothing.

### Seasonal autoregressive integraded moving average model (SARIMA)
SARIMA is actually the combination of simpler models to make a complex model that can model time series exhibiting non-stationary properties and seasonality. At first, we have the autoregression model AR(p). This is basically a regression of the time series onto itself. Here, we assume that the current value depends on its previous values with some lag. It takes a parameter p which represents the maximum lag. To find it, we look at the partial autocorrelation plot and identify the lag after which most lags are not significant.

In my project, I have used Exponential Smoothing which as researched is the most suitable.
Facebook Prophet is designed to handle time series data with multiple seasonality and trends, and it includes a built-in method for performing exponential smoothing. In Prophet, exponential smoothing can be achieved by specifying a parameter called "seasonality_mode" when creating the model.

By default, Prophet uses a parameter called "seasonality_mode" set to "additive", which implies that the seasonal component of the time series is added to the trend component. However, if you want to use exponential smoothing, you can set the parameter "seasonality_mode" to "multiplicative".
To perform exponential smoothing using Prophet, you can follow these steps:
- Import the necessary libraries and load your time series data into a Pandas DataFrame.
- Create a new Prophet model object by calling the Prophet() function.
- Set the "seasonality_mode" parameter to "multiplicative" to enable exponential smoothing.
- Fit the model to your data using the fit() function.
- Generate a forecast for a specified period of time using the make_future_dataframe() and predict() functions.

```python:
model = Prophet(seasonality_mode='multiplicative') #Create a new Prophet model object
model.fit(df) # Fit the model to the data
future_df = model.make_future_dataframe(periods=30)   # Generate a forecast for the next 30 days
forecast = model.predict(future_df)

model.plot(forecast) # Plot the forecasted values
```
- - - - 

I recommend on getting this book to understand how to analyze Time Series like a Pro !!

![image](https://user-images.githubusercontent.com/63351043/231533189-1ebbbe73-c3cf-4dab-b1e4-29acbf147d1c.png)

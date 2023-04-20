# Kenyas-Maize-Output-Time-Series
This is a time series project that utilizes Facebook prophet to predict what Kenya's Maize Output will be in 2027

![image](https://user-images.githubusercontent.com/63351043/230066193-4e79fbc5-46d2-4f1a-a881-a90b404944b1.png)

I recommend on getting this book to understand how to analyze Time Series like a Pro !!

![image](https://user-images.githubusercontent.com/63351043/231533189-1ebbbe73-c3cf-4dab-b1e4-29acbf147d1c.png)

## Handling Missing Data 
The most common methods to address missing data in time series are: 

### Imputation
When we fill in missing data based on observations about the entire data set.

### Interpolation
When we use neighboring data points to estimate the missing value. Interpolation can also be a form of imputation.

### Deletion of affected time periods
When we choose not to use time periods that have missing data at all


## Smoothing Data
Smoothing data can be done for a variety of reasons, and often real-world time series data is smoothed before analysis, especially for visualizations that aim to tell an understandable story about the data. 

While outlier detection is a topic in and of itself, if you have reason to believe your data should be smoothed, you can do so with a moving average to eliminate measurement spikes, errors of measurement, or both. Even if the spikes are accurate, they
may not reflect the underlying process and may be more a matter of instrumentation problems; this is why it’s quite common to smooth data.

Smoothing data is strongly related to imputing missing data, and so some of those techniques are relevant here as well. For example, you can smooth data by applying a rolling mean, with or without a lookahead, as that is simply a matter of the point’s
position relative to the window used to calculate its smoothed value.
When you are smoothing, you want to think about a number of questions:
- Why are you smoothing? 
Smoothing can serve a number of purposes: 
*Data preparation* - Is your raw data unsuitable? For example, you may know very high values are unlikely or unphysical, but you need a principled way to deal with them. Smoothing is the most straightforward solution.
*Feature generation* - The practice of taking a sample of data, be it many characteristics about a person, image, or anything else, and summarizing it with a few metrics. In this way a fuller sample is collapsed along a few dimensions or down to a few
traits. Feature generation is especially important for machine learning.
Prediction - The simplest form of prediction for some kinds of processes is mean reversion, which you get by making predictions from a smoothed feature.
*Visualization*
Do you want to add some signal to what seems like a noisy scatter plot? If so, what is your intention in doing so?
**Therefore Smoothing data is the process of removing noise from a dataset**

![image](https://www.investopedia.com/thmb/AlWZjs7tasYiBJGyzVOl1cObsKU=/750x0/filters:no_upscale():max_bytes(150000):strip_icc():format(webp)/dotdash_Final_Strategies_Applications_Behind_The_50_Day_EMA_INTC_AAPL_Jul_2020-03-4913804fedb2488aa6a3e60de37baf4d.jpg)

#### Pros | 
- Helps identify real trends by eliminating noise from the data |
- Allows for seasonal adjustments of economic data |
- Easily achieved through several techniques including moving averages |
#### Cons
- Removing data always comes with less information to analyze, increasing the risk of errors in analysis
- Smoothing may emphasize analysts' biases and ignore outliers that may be meaningful

This being said, it is essential to smooth data despite its cons.

### Exponential smoothing
You often won’t want to treat all time points equally when smoothing. In particular, you may want to treat more recent data as more informative data, in which case exponential smoothing is a good option. In contrast to the moving average where each point where data was missing could be imputed to the mean of its surrounding points—exponential smoothing is geared to be more temporally aware, weighting more recent points higher than less recent points. So, for a given window, the nearest point in time is weighted most heavily and each point earlier in time is weighted exponentially less (hence the name).

In my project, I have used Exponential Smoothing which as researched is the most suitable.

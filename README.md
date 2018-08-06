# time-series-clustering
Time series Clustering - Dynamic Time Warping
Clustering techniques are used in a variety of setups. In simple terms clustering techniques are methods used to group similar observations based on various definitions of “close proximity”. I would stress upon the term “close proximity” as this connotes different meaning in different setups. The measure of distance between observations could be varying and requires an understanding of the data and the business problem at hand. It is a main task for any exploratory data mining exercise, and a common technique for statistical data analysis, used in many fields.When working with data measured over time, it is sometimes useful to group the time series. Time Series Clustering can be used to find stocks that behave in a similar way, products with similar sales cycles, or regions with similar temperature profiles.

Time series clustering can also help incorporate time series in traditional data mining applications such as customer churn prediction and fraud identification. For example, suppose one has a hunch that customer’s behavior over time would help predict churn or fraud. How would one incorporate the temporal pattern as a predictor in the model, where the unit of analysis is the customer? This can be achieved by categorizing each of the original series and using the category labels as inputs in the predictive model.

Dynamic Time Warping

Dynamic time warping is a method used to align two sequences of data by finding an optimal match. It is a time series alignment algorithm developed originally for speech recognition. It aims at aligning two sequences of feature vectors by warping the time axis iteratively until an optimal match (according to a suitable metrics) between the two sequences is found. A similarity measure between the two sequences, a so called "warping path" is produced, by warping according to this path the two signals may be aligned in time. The signal with an original set of points X (original), Y (original) is transformed to X (warped), Y (original). Although this method was originally developed for applications in genetic sequence and audio synchronization, it finds widespread applications in a variety of applications in business.  

My Experiments with Dynamic Time Warping  

Recently I have been posed with a mammoth amount of time series data for a retailer looking to get some insights into the weekly sales patterns at the SKU level. This presented me with an opportunity to explore various data mining techniques. This is when I started to dabble with time series clustering. Although the data used was proprietary, I wanted to illustrate the use of this technique with some simulated dataset.

Hence I created a synthetic data set containing 3 distinct types of time series

<p> A random process <p>

<p>A autoregressive process <p>

<p>A moving average process<p>

Further I applied the time series clustering technique to illustrate how the combined data set could be grouped into 3 clusters.

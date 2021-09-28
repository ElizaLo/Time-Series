<img src="https://github.com/ElizaLo/Time-Series/blob/main/header.png" width="900" height="100">

## Courses

- [Time Series Forecasting](https://www.udacity.com/course/time-series-forecasting--ud980), Udacity
  > The Time Series Forecasting course provides students with the foundational knowledge to build and apply time series forecasting models in a variety of business contexts 
- [Методы анализа и прогнозирования временных рядов](https://openedu.ru/course/urfu/METHODS/)

## Books

- [Forecasting: Principles and Practice](https://otexts.com/fpp2/#) **(3rd ed)** by Rob J Hyndman and George Athanasopoulos, Monash University, Australia
  > This textbook is intended to provide a comprehensive introduction to forecasting methods and to present enough information about each method for readers to be able to use them sensibly. We don’t attempt to give a thorough discussion of the theoretical details behind each method, although the references at the end of each chapter will fill in many of those details. 
- [Practical Time Series Analysis: Prediction with Statistics and Machine Learning](https://www.amazon.com/Practical-Time-Analysis-Prediction-Statistics/dp/1492041653) by Aileen Nielsen
- [Introduction to Time Series Forecasting With Python](https://machinelearningmastery.com/introduction-to-time-series-forecasting-with-python/) by Jason Brownlee
- [Analysis of Financial Time Series](https://www.amazon.com/Analysis-Financial-Time-Ruey-Tsay/dp/0470414359/) by Ruey S. Tsay
- [Economic Forecasting](https://press.princeton.edu/books/hardcover/9780691140131/economic-forecasting) by Graham Elliott and Allan Timmermann, 2016
- [Forecasting Economic Time Series](https://www.amazon.com/Forecasting-Economic-ECONOMETRICS-MATHEMATICAL-ECONOMICS-ebook/dp/B01DY7LSWO) (ECONOMIC THEORY, ECONOMETRICS, AND MATHEMATICAL ECONOMICS) by C. W. J. Granger, 1986

## YouTube 

- [Time Series Analysis](https://www.youtube.com/playlist?list=PLvcbYUQ5t0UHOLnBzl46_Q6QKtFgfMGc3) playlist

## Blogs

- []()
- []()
- []()

## Useful Articles

- [An overview of time series forecasting models](https://towardsdatascience.com/an-overview-of-time-series-forecasting-models-a2fa7a358fcb)
  > We describe 10 forecasting models and we apply them to predict the evolution of an industrial production index 
- [21 Great Articles and Tutorials on Time Series](https://www.datasciencecentral.com/profiles/blogs/21-great-articles-and-tutorials-on-time-series?utm_content=bufferfc0a4&utm_medium=social&utm_source=linkedin.com&utm_campaign=buffer)
- []()
- []()

## Useful tools

### Frameworks

| Title | Description |
| :---:         |          :--- |
|[Kats](https://facebookresearch.github.io/Kats/) by Facebook|Kats is a toolkit to analyze time series data, a lightweight, easy-to-use, and generalizable framework to perform time series analysis. Time series analysis is an essential component of Data Science and Engineering work at industry, from understanding the key statistics and characteristics, detecting regressions and anomalies, to forecasting future trends. Kats aims to provide the one-stop shop for time series analysis, including detection, forecasting, feature extraction/embedding, multivariate analysis, etc. Kats is released by Facebook's Infrastructure Data Science team. It is available for download on [PyPI](https://pypi.org/project/kats/).|
|[Prophet](https://facebook.github.io/prophet/) by Facebook|Prophet is a forecasting procedure implemented in R and Python. It is fast and provides completely automated forecasts that can be tuned by hand by data scientists and analysts. Prophet is open source software released by Facebook’s Core Data Science team. It is available for download on CRAN and PyPI.|
|[Orbit](https://eng.uber.com/orbit/) by Uber|Orbit (**O**bject-**OR**iented **B**ayes**I**an **T**ime Series) is a general interface for Bayesian time series modeling. The goal of Orbit development team is to create a tool that is easy to use, flexible, interitible, and high performing (fast computation). Under the hood, Orbit uses the probabilistic programming languages (PPL) including but not limited to Stan and Pyro for posterior approximation (i.e, MCMC sampling, SVI). Below is a quadrant chart to position a few time series related packages in our assessment in terms of flexibility and completeness. Orbit is the only tool that allows for easy model specification and analysis while not limiting itself to a small subset of models. For example Prophet has a complete end to end solution but only has one model type and Pyro has total specification model flexibility but does not give an end to end solution. Thus Orbit bridges the gap between business problems and statistical solutions.<ul><li>[Orbit: A Python Package for Bayesian Forecasting](https://github.com/uber/orbit)</li><li>[Orbit’s Documentation](https://uber.github.io/orbit/)</li><li>[Quick Start](https://uber.github.io/orbit/tutorials/quick_start.html)</li><li>[Orbit: Probabilistic Forecast with Exponential Smoothing](https://arxiv.org/abs/2004.08492) Paper</li></ul>|
|[Greykite](https://linkedin.github.io/greykite/) by LinkedIn|<ul><li>The Greykite library provides flexible, intuitive and fast forecasts through its flagship algorithm, Silverkite.</li><li>Silverkite algorithm works well on most time series, and is especially adept for those with changepoints in trend or seasonality, event/holiday effects, and temporal dependencies. Its forecasts are interpretable and therefore useful for trusted decision-making and insights.</li><li>The Greykite library provides a framework that makes it easy to develop a good forecast model, with exploratory data analysis, outlier/anomaly preprocessing, feature extraction and engineering, grid search, evaluation, benchmarking, and plotting. Other open source algorithms can be supported through Greykite’s interface to take advantage of this framework.</li><li>[Greykite](https://github.com/linkedin/greykite)</li><li>[Getting Started](https://linkedin.github.io/greykite/get_started)</li><li>[A flexible forecasting model for production systems](https://arxiv.org/abs/2105.01098) Paper</li><li>[Greykite: A flexible, intuitive, and fast forecasting library](https://engineering.linkedin.com/blog/2021/greykite--a-flexible--intuitive--and-fast-forecasting-library)</li></ul>|
|[statsmodels](https://www.statsmodels.org/stable/index.html)| statsmodels is a Python module that provides classes and functions for the estimation of many different statistical models, as well as for conducting statistical tests, and statistical data exploration. An extensive list of result statistics are available for each estimator. The results are tested against existing statistical packages to ensure that they are correct. The package is released under the open source Modified BSD (3-clause) license. The online documentation is hosted at statsmodels.org.|

### Comparing 

|  | Kats | Prophet |
| :---:         |          :--- |          :--- |
|**Supporting Models**|We currently support the following 10 base forecasting models:<ul><li>Linear</li><li>Quadratic</li><li>ARIMA</li><li>SARIMA</li><li>Holt-Winters</li><li>Prophet</li><li>AR-Net</li><li>LSTM</li><li>Theta</li><li>VAR</li></ul> | |

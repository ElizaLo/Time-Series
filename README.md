<img src="https://github.com/ElizaLo/Time-Series/blob/main/header.png" width="900" height="100">

## University courses 👩‍🎓

| Title | Description |
| :---:         |          :--- |
|[MIT 18.S096 Topics in Mathematics w Applications in Finance](https://ocw.mit.edu/courses/mathematics/18-s096-topics-in-mathematics-with-applications-in-finance-fall-2013/)|<ul><p>The purpose of the class is to expose undergraduate and graduate students to the mathematical concepts and techniques used in the financial industry. Mathematics lectures are mixed with lectures illustrating the corresponding application in the financial industry. MIT mathematicians teach the mathematics part while industry professionals give the lectures on applications in finance.</p><li>[Video lectures](https://www.youtube.com/playlist?list=PLUl4u3cNGP63ctJIEC1UnZ0btsphnnoHR)</li></ul>|

## Courses

- [Time Series Forecasting](https://www.udacity.com/course/time-series-forecasting--ud980), Udacity
  > The Time Series Forecasting course provides students with the foundational knowledge to build and apply time series forecasting models in a variety of business contexts 
- [Методы анализа и прогнозирования временных рядов](https://openedu.ru/course/urfu/METHODS/)

## Books 📚

- [Forecasting: Principles and Practice](https://otexts.com/fpp2/#) **(3rd ed)** by Rob J Hyndman and George Athanasopoulos, Monash University, Australia
  > This textbook is intended to provide a comprehensive introduction to forecasting methods and to present enough information about each method for readers to be able to use them sensibly. We don’t attempt to give a thorough discussion of the theoretical details behind each method, although the references at the end of each chapter will fill in many of those details. 
- [Practical Time Series Analysis: Prediction with Statistics and Machine Learning](https://www.amazon.com/Practical-Time-Analysis-Prediction-Statistics/dp/1492041653) by Aileen Nielsen
- [Introduction to Time Series Forecasting With Python](https://machinelearningmastery.com/introduction-to-time-series-forecasting-with-python/) by Jason Brownlee
- [Analysis of Financial Time Series](https://www.amazon.com/Analysis-Financial-Time-Ruey-Tsay/dp/0470414359/) by Ruey S. Tsay
- [Economic Forecasting](https://press.princeton.edu/books/hardcover/9780691140131/economic-forecasting) by Graham Elliott and Allan Timmermann, 2016
- [Forecasting Economic Time Series](https://www.amazon.com/Forecasting-Economic-ECONOMETRICS-MATHEMATICAL-ECONOMICS-ebook/dp/B01DY7LSWO) (ECONOMIC THEORY, ECONOMETRICS, AND MATHEMATICAL ECONOMICS) by C. W. J. Granger, 1986
- [sits: Data Analysis and Machine Learning on Earth Observation Data Cubes with Satellite Image Time Series](https://e-sensing.github.io/sitsbook/)

## YouTube 

- [Time Series Analysis](https://www.youtube.com/playlist?list=PLvcbYUQ5t0UHOLnBzl46_Q6QKtFgfMGc3) playlist

## Blogs

- []()
- []()
- []()

## Articles

- [An overview of time series forecasting models](https://towardsdatascience.com/an-overview-of-time-series-forecasting-models-a2fa7a358fcb)
  > We describe 10 forecasting models and we apply them to predict the evolution of an industrial production index 
- [21 Great Articles and Tutorials on Time Series](https://www.datasciencecentral.com/profiles/blogs/21-great-articles-and-tutorials-on-time-series?utm_content=bufferfc0a4&utm_medium=social&utm_source=linkedin.com&utm_campaign=buffer)
- [Introduction to the Fundamentals of Time Series Data and Analysis](https://www.aptech.com/blog/introduction-to-the-fundamentals-of-time-series-data-and-analysis/)
- [The Complete Guide to Time Series Analysis and Forecasting](https://towardsdatascience.com/the-complete-guide-to-time-series-analysis-and-forecasting-70d476bfe775)

### Small Time Series Dataset

- [Making predictions on a very small time series dataset](https://medium.com/@amit.arora15/making-predictions-using-a-very-small-dataset-230dd579dca8)
- [Forecasting very short time series](https://otexts.com/fpp2/long-short-ts.html)

### Topic specific

- [Difference between **estimation** and **prediction**?](https://stats.stackexchange.com/questions/17773/what-is-the-difference-between-estimation-and-prediction)

## Models, Algorithms

| Title | Description, key points, related links |
| :---:         |          :--- |
|**MEAN**|<ul><li>[Is it unusual for the MEAN to outperform ARIMA?](https://stats.stackexchange.com/questions/124955/is-it-unusual-for-the-mean-to-outperform-arima)</li><li>[]()</li><li>[]()</li><li>[]()</li></ul>|

## Tools

### Frameworks

| Title | Description |
| :---:         |          :--- |
|[Kats](https://facebookresearch.github.io/Kats/) by Facebook|Kats is a toolkit to analyze time series data, a lightweight, easy-to-use, and generalizable framework to perform time series analysis. Time series analysis is an essential component of Data Science and Engineering work at industry, from understanding the key statistics and characteristics, detecting regressions and anomalies, to forecasting future trends. Kats aims to provide the one-stop shop for time series analysis, including detection, forecasting, feature extraction/embedding, multivariate analysis, etc. Kats is released by Facebook's Infrastructure Data Science team. It is available for download on [PyPI](https://pypi.org/project/kats/).|
|[Prophet](https://facebook.github.io/prophet/) by Facebook|<ul><p>Prophet is a forecasting procedure implemented in R and Python. It is **Generalized additive model (GAM)** with three main components:  non-linear trends are fit with seasonality and holidays. </p><p> It is fast and provides completely automated forecasts that can be tuned by hand by data scientists and analysts. </p><p> g<sub>t</sub> is the piecewise linear or logistic growth curve to model the non-periodic changes in the time series, s<sub>t</sub> is the seasonality term, h<sub>t</sub> is the holiday effect with irregular schedules, and εt is the error term. </p><p> On a high level, Prophet is framing the forecasting problem as a curve-fitting exercise rather than looking explicitly at the time based dependence of each observation within a time series. </p><p> As a computational tool/software, moreover, Prophet allows users to manually supply change points in fitting the trend term and set the boundaries for saturation growth, which gives great flexibility in business applications. </p><p> Prophet is open source software released by Facebook’s Core Data Science team. It is available for download on CRAN and PyPI.</p></ul>|
|[Orbit](https://eng.uber.com/orbit/) by Uber|Orbit (**O**bject-**OR**iented **B**ayes**I**an **T**ime Series) is a general interface for **Bayesian exponential smoothing model**. The goal of Orbit development team is to create a tool that is easy to use, flexible, interitible, and high performing (fast computation). Under the hood, Orbit uses the probabilistic programming languages (PPL) including but not limited to Stan and Pyro for posterior approximation (i.e, MCMC sampling, SVI). Below is a quadrant chart to position a few time series related packages in our assessment in terms of flexibility and completeness. Orbit is the only tool that allows for easy model specification and analysis while not limiting itself to a small subset of models. For example Prophet has a complete end to end solution but only has one model type and Pyro has total specification model flexibility but does not give an end to end solution. Thus Orbit bridges the gap between business problems and statistical solutions.<ul><li>[:octocat: Orbit: A Python Package for Bayesian Forecasting](https://github.com/uber/orbit)</li><li>[Orbit’s Documentation](https://uber.github.io/orbit/)</li><li>[Quick Start](https://uber.github.io/orbit/tutorials/quick_start.html)</li><li>[Orbit: Probabilistic Forecast with Exponential Smoothing](https://arxiv.org/abs/2004.08492) Paper</li></ul>|
|[Greykite](https://linkedin.github.io/greykite/) by LinkedIn|<ul><p>The Greykite library provides flexible, intuitive and fast forecasts through its flagship algorithm, Silverkite.</p><p>Silverkite algorithm works well on most time series, and is especially adept for those with changepoints in trend or seasonality, event/holiday effects, and temporal dependencies. Its forecasts are interpretable and therefore useful for trusted decision-making and insights.</p><p>The Greykite library provides a framework that makes it easy to develop a good forecast model, with exploratory data analysis, outlier/anomaly preprocessing, feature extraction and engineering, grid search, evaluation, benchmarking, and plotting. Other open source algorithms can be supported through Greykite’s interface to take advantage of this framework.</p><li>[:octocat: Greykite](https://github.com/linkedin/greykite)</li><li>[Getting Started](https://linkedin.github.io/greykite/get_started)</li><li>[A flexible forecasting model for production systems](https://arxiv.org/abs/2105.01098) Paper</li><li>[Greykite: A flexible, intuitive, and fast forecasting library](https://engineering.linkedin.com/blog/2021/greykite--a-flexible--intuitive--and-fast-forecasting-library)</li></ul>|
|[statsmodels](https://www.statsmodels.org/stable/index.html)| statsmodels is a Python module that provides classes and functions for the estimation of many different statistical models, as well as for conducting statistical tests, and statistical data exploration. An extensive list of result statistics are available for each estimator. The results are tested against existing statistical packages to ensure that they are correct. The package is released under the open source Modified BSD (3-clause) license. The online documentation is hosted at statsmodels.org.|
|[Merlion](https://opensource.salesforce.com/Merlion/v1.0.0/index.html)|Merlion is a Python library for time series intelligence. It features a unified interface for many commonly used models and datasets for anomaly detection and forecasting on both univariate and multivariate time series, along with standard pre-processing and post-processing layers. It has several modules to improve ease-of-use, including visualization, anomaly score calibration to improve interpetability, AutoML for hyperparameter tuning and model selection, and model ensembling. Merlion also provides a unique evaluation framework that simulates the live deployment and re-training of a model in production. This library aims to provide engineers and researchers a one-stop solution to rapidly develop models for their specific time series needs, and benchmark them across multiple time series datasets.|
|[Auto_TS: Auto_TimeSeries](https://github.com/AutoViML/Auto_TS)|Automatically build ARIMA, SARIMAX, VAR, FB Prophet and XGBoost Models on Time Series data sets with a Single Line of Code. Now updated with Dask to handle millions of rows.|
|[TensorFlow Probability](https://www.tensorflow.org/probability)|TensorFlow Probability (TFP) is a Python library built on TensorFlow that makes it easy to combine probabilistic models and deep learning on modern hardware (TPU, GPU). It's for data scientists, statisticians, ML researchers, and practitioners who want to encode domain knowledge to understand data and make predictions.|
|[Pyro](https://pyro.ai)|<ul><p>Deep Universal Probabilistic Programming.</p><li>[:octocat: Pyro](https://github.com/pyro-ppl/pyro)</li></ul>|
|[ArviZ: Exploratory analysis of Bayesian models](https://arviz-devs.github.io/arviz/#)|ArviZ is a Python package for exploratory analysis of Bayesian models. Includes functions for posterior analysis, data storage, sample diagnostics, model checking, and comparison.|
|[PyStan](https://pystan.readthedocs.io/en/latest/)|PyStan is a Python interface to Stan, a package for Bayesian inference.|
|[StatsForecast](https://github.com/Nixtla/statsforecast)|<ul><li>**StatsForecast** offers a collection of widely used univariate time series forecasting models, including automatic `ARIMA` and `ETS` modeling optimized for high performance using `numba`. It also includes a large battery of benchmarking models.</li><li>[Fast Time Series Forecasting with StatsForecast](https://towardsdatascience.com/fast-time-series-forecasting-with-statsforecast-694d1670a2f3)</li><li>[]()</li><li>[]()</li></ul>|


## GitHub Repositories :octocat:

| Title | Description |
| :---:         |          :--- |
|[awesome_time_series_in_python](https://github.com/MaxBenChrist/awesome_time_series_in_python)|This curated list contains python packages for time series analysis|

## Podcasts 🎧

| Title | Description |
| :---:         |          :--- |
|[Data Skeptic](https://podcasts.apple.com/ua/podcast/data-skeptic/id890348705)|Episode - [Forecasting Principles and Practice](https://podcasts.apple.com/ua/podcast/forecasting-principles-and-practice/id890348705?i=1000522928916)|
|[Seriously Social](https://podcasts.apple.com/ua/podcast/seriously-social/id1509419418)|Episode - [Forecasting the future: the science of prediction](https://podcasts.apple.com/ua/podcast/forecasting-the-future-the-science-of-prediction/id1509419418?i=1000516647970) |
|[The Curious Quant](https://podcasts.apple.com/ua/podcast/the-curious-quant/id1481550488)|Episode - [Forecasting COVID, time series, and why causality doesnt matter as much as you think‪](https://podcasts.apple.com/ua/podcast/ep20-prof-rob-hyndman-forecasting-covid-time-series/id1481550488?i=1000485268452)|
|[Forecasting Impact](https://podcasts.apple.com/ua/podcast/forecasting-impact/id1550584556)||
|[The Random Sample](https://podcasts.apple.com/ua/podcast/the-random-sample/id1439750898)|Episode - [Forecasting the future & the future of forecasting](https://podcasts.apple.com/ua/podcast/forecasting-the-future-the-future-of-forecasting/id1439750898?i=1000475866199) |
|[Thought Capital](https://podcasts.apple.com/ua/podcast/thought-capital/id1434491776)|Episode - [Forecasts are always wrong (but we need them anyway)](https://podcasts.apple.com/ua/podcast/forecasts-are-always-wrong-but-we-need-them-anyway/id1434491776?i=1000452853638)|

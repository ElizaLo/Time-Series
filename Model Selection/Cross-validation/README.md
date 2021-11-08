# Cross validation of Time Series data

Time series data is characterised by the correlation between observations that are near in time (autocorrelation). However, classical cross-validation techniques such as KFold and ShuffleSplit assume the samples are independent and identically distributed, and would result in unreasonable correlation between training and testing instances (yielding poor estimates of generalisation error) on time series data. Therefore, it is very important to evaluate our model for time series data on the “future” observations least like those that are used to train the model. To achieve this, one solution is provided by TimeSeriesSplit.

| Title | Description, Information |
| :---:         |          :--- |
|**K-Folds cross-validator**|<ul><p>KFold divides all the samples in _k_ groups of samples, called folds (if _k = n_, this is equivalent to the Leave One Out strategy), of equal sizes (if possible). The prediction function is learned using _k−1_ folds, and the fold left out is used for test.</p><li>[K-fold](https://scikit-learn.org/stable/modules/cross_validation.html#k-fold)</li><li>[sklearn.model_selection.KFold](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.KFold.html#sklearn.model_selection.KFold)</li></ul>|
|**Time Series Split**|<ul><p>TimeSeriesSplit is a variation of k-fold which returns first _k_ folds as train set and the _(k + 1)_- th fold as test set. Note that unlike standard cross-validation methods, successive training sets are supersets of those that come before them. Also, it adds all surplus data to the first training partition, which is always used to train the model.</p><p>This class can be used to cross-validate time series data samples that are observed at fixed time intervals.</p><li>[Time Series Split](https://scikit-learn.org/stable/modules/cross_validation.html#time-series-split)</li><li>[sklearn.model_selection.TimeSeriesSplit](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.TimeSeriesSplit.html)</li></ul>|
|**Backtest Orbit Model**|<ul><p>The way to gauge the performance of a time-series model is through re-training models with different historic periods and check their forecast within certain steps. This is similar to a time-based style cross-validation. More often, we called it `backtest` in time-series modeling.</p><p>There are two schemes for the back-testing engine: **expanding window** and **rolling window.**</p><li>**expanding window:** for each back-testing model training, the train start date is fixed, while the train end date is extended forward. The expanding window form, on the other hand, is used more often in _**weekly, monthly, or quarterly time series**_ where the number of historical points are limited.</li><li>**rolling window:** for each back-testing model training, the training window length is fixed but the window is moving forward. The sliding window form achieves a favorable balance between model accuracy and training time, especially when it comes to testing high frequency data such as _**daily and hourly time series**_.</li><p> </p><li>[A Gentle Introduction to Backtesting for Evaluating the Prophet Forecasting Models](https://blog.exploratory.io/a-gentle-introduction-to-backtesting-for-evaluating-the-prophet-forecasting-models-66c132adc37c)</li><li>[How To Backtest Machine Learning Models for Time Series Forecasting](https://machinelearningmastery.com/backtest-machine-learning-models-time-series-forecasting/)</li><li>[The basics of backtesting](https://www.datapred.com/blog/the-basics-of-backtesting)</li><li>[Omphalos, Uber’s Parallel and Language-Extensible Time Series Backtesting Tool](https://eng.uber.com/omphalos/)</li></ul>|
|**Decompose Prediction**|<ul><p>Decomposition is a technique that can be used to separate a series into components and predict each one individually. Each part can be treated in the most appropriate way and thereby improve the total prediction.</p><p>First, we do the prediction on the training data before the year N. Next, we do the predictions on the test data after the year N. This plot is useful to help check the overall model performance on the out-of-sample period.</p><li>[Decompose Prediction in Orbit](https://orbit-ml.readthedocs.io/en/latest/tutorials/decompose_prediction.html)</li><li>[Forecasting with decomposition](https://otexts.com/fpp2/forecasting-decomposition.html) in "Forecasting: Principles and Practice" (2nd ed) book by Rob J Hyndman and George Athanasopoulos</li><li>[Using decomposition to improve time series prediction](https://quantdare.com/decomposition-to-improve-time-series-prediction/)</li></ul>|


- [Building a Backtesting Service to Measure Model Performance at Uber-scale](https://eng.uber.com/backtesting-at-scale/)
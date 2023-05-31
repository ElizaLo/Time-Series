# Time Series Forecast Error Metrics

<img src="https://github.com/ElizaLo/Data-Science/blob/master/Statistics/img/Overview%20Time%20Series_Forecast_Error_Metrics.png" width="971" height="322"/>

Keep in mind that **there is no silver bullet, no single best error metric**. The fundamental challenge is, that every statistical measure condenses a large number of data into a single value, so it only provides one projection of the model errors emphasizing a certain aspect of the error characteristics of the model performance _(Chai and Draxler 2014)_.

Therefore it is better to have a more practical and pragmatic view and work with a selection of metrics that fit for your use case or project.

# 💠 Scale Dependent Metrics

Many popular metrics are referred to as **scale-dependent** _(Hyndman, 2006)_. Scale-dependent means the error metrics are **expressed in the units** _(i.e. Dollars, Inches, etc.)_ of the underlying data.

The main advantage of scale dependent metrics is that they are usually **easy to calculate** and **interpret**. However, they can **not be used to compare different series**, because of their **scale dependency** _(Hyndman, 2006)_.

> Please note here that _Hyndman (2006)_ includes Mean Squared Error into a scale-dependent group (claiming that the error is “on the same scale as the data”). However, Mean Squared Error has a dimension of the squared scale/unit. To bring MSE to the data’s unit we need to take the square root which leads to another metric, the RMSE. _(Shcherbakov et al., 2013)_

## 🔹 Mean Absolute Error (MAE)

<img src="https://github.com/ElizaLo/Data-Science/blob/master/Statistics/img/MAE.png" width="304" height="105"/>

The **Mean Absolute Error (MAE)** is calculated by taking the mean of the **absolute differences between the actual values** (also called _y_) **and the predicted values** (_y_hat_).

It is **easy to understand** (even for business users) and **to compute**. It is recommended for **assessing accuracy on a single series** _(Hyndman, 2006)_. 

However if you want to compare different series (with different units) it is not suitable. Also you should **not use** it if you want to **penalize outliers**.

```python
import numpy as np

def mae(y, y_hat):
    return np.mean(np.abs(y - y_hat))
```

## 🔹 Mean Squared Error (MSE)

If you want to put **more attention on outliers (huge errors)** you can consider the **Mean Squared Error (MSE)**. Like it’s name implies it takes the mean of the squared errors (differences between _y_ and _y_hat_). 

Due to its squaring, it **heavily weights large errors more than small ones**, which can be in some situations a **disadvantage**. Therefore the MSE is suitable for situations where you **really want to focus on large errors**. 

Also keep in mind that due to its squaring the metric **loses its unit**.

```python
import numpy as np

def mse(y, y_hat):
    return np.mean(np.square(y - y_hat))
```

## 🔹 Root Mean Squared Error (RMSE)

<img src="https://github.com/ElizaLo/Data-Science/blob/master/Statistics/img/RMSE.png" width="326" height="119"/>

To **avoid the MSE’s loss of its unit** we can take the square root of it. The outcome is then a new error metric called the Root Mean Squared Error (RMSE).

It comes with the same **advantages** as its siblings MAE and MSE. However, like MSE, it is also **sensitive to outliers**.

Some authors like _Willmott and Matsuura (2005)_ argue that the RMSE is an inappropriate and misinterpreted measure of an average error and recommend MAE over RMSE.

However, Chai and Drexler (2014) partially refuted their arguments and **recommend RMSE over MAE for your model optimization** as well as for **evaluating different models where the error distribution is expected to be Gaussian**.

# 💠 Percentage Error Metrics

As we know from the previous chapter, **scale dependent metrics are not suitable for comparing different time series**.

Percentage Error Metrics solve this problem. They are **scale independent** and **used to compare forecast performance between different time series**. However, their **weak spots are zero values in a time series**. Then they become **infinite or undefined** which makes them not interpretable _(Hyndman 2006)_.

## 🔹 Mean Absolute Percentage Error (MAPE)

<img src="https://github.com/ElizaLo/Data-Science/blob/master/Statistics/img/MAPE.png" width="355" height="119"/>

The mean absolute percentage error (MAPE) is one of the **most popular used error metrics** in time series forecasting. It is calculated by taking the average (mean) of the absolute difference between actuals and predicted values divided by the actuals.

> _Please note, some MAPE formulas do not multiply the result(s) with 100. However, the MAPE is presented as a percentage unit so I added the multiplication._

MAPE’s **advantages** are it’s **scale-independency** and **easy interpretability**. As said at the beginning, percentage error metrics can be used to compare the outcome of multiple time series models with different scales.

However, MAPE also comes with some **disadvantages**. First, **it generates infinite or undefined values for zero or close-to-zero actual values** _(Kim and Kim 2016)_.

Second, it also puts a **heavier penalty on negative than on positive errors** which leads to an **asymmetry** _(Hyndman 2014)_.

And last but not least, MAPE **can not be used when using percentages make no sense**. This is for example the case when measuring temperatures. The units Fahrenheit or Celsius scales have relatively arbitrary zero points, and it makes no sense to talk about percentages _(Hyndman and Koehler, 2006)_.

```python
import numpy as np

def mape(y, y_hat):
    return np.mean(np.abs((y - y_hat)/y)*100)
```

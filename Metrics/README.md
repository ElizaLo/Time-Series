# Time Series Forecast Error Metrics

<img src="https://github.com/ElizaLo/Data-Science/blob/master/Statistics/img/Overview%20Time%20Series_Forecast_Error_Metrics.png" width="971" height="322"/>

Keep in mind that **there is no silver bullet, no single best error metric**. The fundamental challenge is, that every statistical measure condenses a large number of data into a single value, so it only provides one projection of the model errors emphasizing a certain aspect of the error characteristics of the model performance _(Chai and Draxler 2014)_.

Therefore it is better to have a more practical and pragmatic view and work with a selection of metrics that fit for your use case or project.

# 💠 Scale Dependent Metrics

Many popular metrics are referred to as **scale-dependent** _(Hyndman, 2006)_. Scale-dependent means the error metrics are **expressed in the units** _(i.e. Dollars, Inches, etc.)_ of the underlying data.

The main advantage of scale dependent metrics is that they are usually **easy to calculate** and **interpret**. However, they can **not be used to compare different series**, because of their **scale dependency** _(Hyndman, 2006)_.

> Please note here that _Hyndman (2006)_ includes Mean Squared Error into a scale-dependent group (claiming that the error is “on the same scale as the data”). However, Mean Squared Error has a dimension of the squared scale/unit. To bring MSE to the data’s unit we need to take the square root which leads to another metric, the RMSE. _(Shcherbakov et al., 2013)_

## 🔹 Mean Absolute Error (MAE)

<img src="" width="1050" height="150"/>

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

<img src="" width="1050" height="150"/>

To avoid the MSE’s loss of its unit we can take the square root of it. The outcome is then a new error metric called the Root Mean Squared Error (RMSE).
It comes with the same advantages as its siblings MAE and MSE. However, like MSE, it is also sensitive to outliers.

Some authors like Willmott and Matsuura (2005) argue that the RMSE is an inappropriate and misinterpreted measure of an average error and recommend MAE over RMSE.

However, Chai and Drexler (2014) partially refuted their arguments and recommend RMSE over MAE for your model optimization as well as for evaluating different models where the error distribution is expected to be Gaussian.

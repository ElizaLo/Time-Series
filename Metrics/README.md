# Time Series Forecast Error Metrics

<img src="https://github.com/ElizaLo/Data-Science/blob/master/Statistics/img/Overview%20Time%20Series_Forecast_Error_Metrics.png" width="971" height="322"/>

Keep in mind that **there is no silver bullet, no single best error metric**. The fundamental challenge is, that every statistical measure condenses a large number of data into a single value, so it only provides one projection of the model errors emphasizing a certain aspect of the error characteristics of the model performance _(Chai and Draxler 2014)_.

Therefore it is better to have a more practical and pragmatic view and work with a selection of metrics that fit for your use case or project.

# 💠 Scale Dependent Metrics

Many popular metrics are referred to as **scale-dependent** _(Hyndman, 2006)_. Scale-dependent means the error metrics are **expressed in the units** _(i.e. Dollars, Inches, etc.)_ of the underlying data.

The main advantage of scale dependent metrics is that they are usually **easy to calculate** and **interpret**. However, they can **not be used to compare different series**, because of their **scale dependency** _(Hyndman, 2006)_.

> Please note here that _Hyndman (2006)_ includes Mean Squared Error into a scale-dependent group (claiming that the error is “on the same scale as the data”). However, Mean Squared Error has a dimension of the squared scale/unit. To bring MSE to the data’s unit we need to take the square root which leads to another metric, the RMSE. _(Shcherbakov et al., 2013)_

## 🔹 Mean Error

The mean error is an informal term that usually refers to the average of all the errors in a set. An _“error”_ in this context is an [uncertainty](https://www.statisticshowto.com/uncertainty-in-statistics/) in a measurement, or the difference between the measured value and true/correct value. The more formal term for error is [measurement error](https://www.statisticshowto.com/measurement-error/), also called [observational error](https://www.statisticshowto.com/measurement-error/).

**The mean error usually results in a number that isn’t helpful** because positives and negatives cancel each other out. For example, two errors of +100 and -100 would give a mean error of zero

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

## 🔹 Symmetric Mean Absolute Percentage Error (sMAPE)

To **avoid the asymmetry** of the MAPE a new error metric was proposed. The **Symmetric Mean Absolute Percentage Error (sMAPE)**. The sMAPE is probably one of the **most controversial** error metrics, since not only different definitions or formulas exist but also critics claim that this metric **is not symmetric** as the name suggests _(Goodwin and Lawton, 1999)_.

The original idea of an **“adjusted MAPE”** was proposed by _Armstrong (1985)_. However by his definition the **error metric can be negative or infinite** since the values in the denominator **are not set absolute** (which is then correctly mentioned as a disadvantage in some articles that follow his definition).

<img src="https://github.com/ElizaLo/Data-Science/blob/master/Statistics/img/MAPE_formula.png" width="458" height="71"/>

_Makridakis (1993)_ proposed a similar metric and called it SMAPE. His formula which can be seen below **avoids the problems Armstrong’s formula** had by setting the values in the denominator to absolute _(Hyndman, 2014)_.

<img src="https://github.com/ElizaLo/Data-Science/blob/master/Statistics/img/sMAPE_%20Makridakis_formula.png" width="385" height="94"/>

> _**Note:** Makridakis (1993) proposed the formula above in his paper “Accuracy measures: theoretical and practical concerns’’. Later in his publication (Makridakis and Hibbon, 2000) “The M3-Competition: results, conclusions and implications’’ he used Armstrong’s formula (Hyndman, 2014). This fact has probably also contributed to the confusion about SMAPE’s different definitions._

The sAMPE is the average across all forecasts made for a given horizon. It’s **advantages** are that it **avoids MAPE’s problem of large errors** when y-values are close to zero and the large difference between the absolute percentage errors when y is greater than y-hat and vice versa. Unlike MAPE which has no limits, **it fluctuates between 0% and 200%** _(Makridakis and Hibon, 2000)_.

For the **sake of interpretation** there is also a **slightly modified version of SMAPE** that ensures that the metric’s results **will be always between 0% and 100%**:

<img src="https://github.com/ElizaLo/Data-Science/blob/master/Statistics/img/sMAPE_%20modified.png" width="385" height="94"/>

The following code snippet contains the sMAPE metric proposed by _Makridakis (1993)_ and the modified version.

```python
import numpy as np

# SMAPE proposed by Makridakis (1993): 0%-200%
def smape_original(a, f):
    return 1/len(a) * np.sum(2 * np.abs(f-a) / (np.abs(a) + np.abs(f))*100)


# adjusted SMAPE version to scale metric from 0%-100%
def smape_adjusted(a, f):
    return (1/a.size * np.sum(np.abs(f-a) / (np.abs(a) + np.abs(f))*100))
```

As mentioned at the beginning, there are **controversies around the sMAPE**. And they are true. _Goodwin and Lawton (1999)_ pointed out that sMAPE **gives more penalties to under-estimates more than to over-estimates** _(Chen et al., 2017)_. _Cánovas (2009)_ proofs this fact with an easy example.

- **_Table 1:_** Example with a **symmetric sMAPE**:

<img src="https://github.com/ElizaLo/Data-Science/blob/master/Statistics/img/symmetric_sMAPE.png" width="632" height="127"/>

- **_Table 2:_** Example with an **asymmetric sMAPE**:

<img src="https://github.com/ElizaLo/Data-Science/blob/master/Statistics/img/asymmetric_sMAPE.png" width="632" height="127"/>

Starting with **_Table 1_** we have two cases. In **case 1** our actual value **_y_** is **100** and the prediction **_y_hat_** **150**. This leads to a sMAPE value of 20 %. **Case 2** is the opposite. Here we have an actual value _**y**_ of **150** and a prediction **_y_hat_** of **100**. This also leads to a sMAPE of 20 %. 

Let us now have a look at **_Table 2_**. We also have here two cases and as you can already see the sMAPE values **are not the same anymore**. The second case **leads to a different SMAPE value** of 33 %.

**Modifying the forecast while holding fixed actual values and absolute deviation do not produce the same sMAPE’s value. Simply biasing the model without improving its accuracy should never produce different error values _(Cánovas, 2009)_.**

# 💭 Conclusions

- As you have seen there is **no silver bullet, no single best error metric**. Each category or metric has its **advantages** and **weaknesses**. So it **always depends on your individual use case** or **purpose and your underlying data**. It is important **not to just look at one single error metric** when evaluating your model’s performance. It is necessary to measure several of the main metrics described above in order to analyze several parameters such as deviation, symmetrical deviation and largest outliers.
- If all series **are on the same scale**, the **data preprocessing procedures** were performed (data cleaning, anomaly detection) and the task is **to evaluate the forecast performance** then the **MAE can be preferred** because it is simpler to explain _(Hyndman and Koehler, 2006; Shcherbakov et al., 2013)_.
- _Chai and Draxler (2014)_ recommend to **prefer RMSE over MAE** when the error distribution is **expected to be Gaussian**.
- In case the data **contain outliers** it is advisable to apply scaled measures like **MASE**. In this situation the **horizon should be large enough, no identical values should be**, the normalized factor **should be not equal to zero** _(Shcherbakov et al., 2013)_.

# 📰 Articles

- [Time Series Forecast Error Metrics You Should Know](https://towardsdatascience.com/time-series-forecast-error-metrics-you-should-know-cc88b8c67f27)
- [Choosing the correct error metric: MAPE vs. sMAPE](https://towardsdatascience.com/choosing-the-correct-error-metric-mape-vs-smape-5328dec53fac)
- [Types of error](https://www.abs.gov.au/statistics/understanding-statistics/statistical-terms-and-concepts/types-error#:~:text=Error%20(statistical%20error)%20describes%20the,data%20are%20of%20the%20population.)

---

# 💠 Measures

## 🔹 Percentage of Correct Direction (PCD)

**PCD measures the proportion of time steps where the predicted direction _(e.g., increase or decrease)_ matches the actual direction.** It is useful when the direction of the predicted values is more important than the magnitude of the errors.

The resulting boolean values are then converted to `1` for **True (correct direction)** and `0` for **False (incorrect direction)**.

```python
# Calculate Percentage of Correct Direction (PCD) for each row
df['PCD'] = (df['Actual'].diff() > 0) == (df['Predicted'].diff() > 0)

# Convert boolean values to 1 for True and 0 for False
df['PCD'] = df['PCD'].astype(int)

# Calculate PCD for the whole dataset
overall_pcd = df['PCD'].sum() / len(df) * 100

# Display the updated DataFrame with PCD column
print(df)

# Display the overall PCD for the whole dataset
print('Overall PCD:', overall_pcd)
```

## 🔹 Uncertainty coefficient, Theil's U

The term **“U statistic”** can have several meanings:

- Unbiased (U) statistics
- Mann Whitney U Statistic
- U statistic in L-estimators
- Theil’s U

Theil's U statistic compares the root mean squared error of the model predictions to the root mean squared error of a simple benchmark, such as the naive forecast _(e.g., using the previous observation as the prediction)_. It provides a measure of the model's improvement over a naive approach.

Theil proposed two U statistics, used in finance. The first _**U1**_ is a measure of forecast accuracy _(Theil, 1958, pp 31-42)_; The second _**U2**_ is a measure of forecast quality _(Theil, 1966, chapter 2)_.

```python
# Calculate Theil's U statistic for each row
df['U'] = np.sqrt(((df['Predicted'] - df['Actual']) ** 2).mean()) / np.sqrt(((df['Actual'].diff()) ** 2).mean())
```

### 📰 Articles

- [Uncertainty coefficient](https://en.wikipedia.org/wiki/Uncertainty_coefficient) - Wikipedia
- [U Statistic: Definition, Different Types; Theil’s U](https://www.statisticshowto.com/u-statistic-theils/)
- [Theil’s U](https://docs.oracle.com/cd/E40248_01/epm.1112/cb_statistical/frameset.htm?ch07s02s03s04.html) - Oracle

## 🔹 Forecast Error Variance Decomposition (FEVD)

FEVD decomposes the variance of the forecast errors into components attributed to different factors, such as model bias, model variance, and random fluctuations. It provides insights into the sources of forecast errors and can help identify areas for improvement in the model.

### 📰 Articles

- [Variance decomposition of forecast errors](https://en.wikipedia.org/wiki/Variance_decomposition_of_forecast_errors)
- [The Intuition Behind Impulse Response Functions and Forecast Error Variance Decomposition](https://www.aptech.com/blog/the-intuition-behind-impulse-response-functions-and-forecast-error-variance-decomposition/)

## 🔹 Forecast Coverage

Forecast coverage measures the proportion of actual values that fall within a certain prediction interval or range. It can be explained as the percentage of the actual values that are captured within the model's prediction bounds, providing an assessment of the model's reliability in capturing the range of possible outcomes.

```python
# Calculate Forecast Coverage for each row
df['Coverage'] = ((df['Actual'] >= df['Predicted - Lower Bound']) &
                  (df['Actual'] <= df['Predicted - Upper Bound'])).astype(int)

# Calculate Forecast Coverage for the whole dataset
overall_coverage = df['Coverage'].sum() / len(df) * 100

# Display the updated DataFrame with Coverage column
print(df)

# Display Forecast Coverage for the whole dataset
print('Overall Forecast Coverage:', overall_coverage)
```

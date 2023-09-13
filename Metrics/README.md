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

# 💠 Margin of Error

The **margin of error** is defined a the [range](https://www.statisticshowto.com/types-of-functions/domain-and-range-of-a-function/) of values below and above the [sample statistic](https://www.statisticshowto.com/sample-statistic-definition-examples/) in a [confidence interval](https://www.statisticshowto.com/probability-and-statistics/confidence-interval/). The confidence interval is a way to show what the [**uncertainty**](https://www.statisticshowto.com/uncertainty-in-statistics/) is with a certain [statistic](https://www.statisticshowto.com/statistic/) _(i.e. from a poll or survey)_.

A statistical value that determines, with a certain degree of probability, the maximum value by which the results of the sample differ from the results of the general population. It is half the length of the confidence interval.

> **Предельная ошибка выборки** (также _предельная погрешность выборки_) — статистическая величина, определяющая, с определенной степенью вероятности, максимальное значение, на которое результаты выборки отличаются от результатов генеральной совокупности. Составляет половину длины доверительного интервала.

**_Examples:_**

- _For example,_ a survey indicates that **72%** of respondents favor Brand A over Brand B with a 3% margin of error. In this case, the actual population percentage that prefers Brand A likely falls within the range of **72% ± 3%**, or **69 – 75%**.
- A margin of error tells you how many percentage points your results will differ from the real population value. _For example,_ a 95% confidence interval with a 4 percent margin of error means that your statistic will be within 4 percentage points of the real population value 95% of the time.

A **smaller margin of error** suggests that **the survey’s results will tend to be close to the correct values**. Conversely, **larger MOEs** indicate that **the survey’s estimates can be further away from the population values**.

The margin of error is influenced by several factors, including the sample size, variability in the data, and the desired level of confidence. A larger sample size generally results in a smaller margin of error, indicating a more precise estimate. Similarly, a higher level of confidence requires a larger margin of error to account for the increased certainty.

The margin of error provides a measure of the precision and reliability of a sample-based estimate. It helps researchers and analysts interpret and communicate the level of confidence and uncertainty associated with the estimated values.

The code calculates the error (residual) between the actual and predicted values and adds it as a new column 'Error' in the DataFrame. Then, it calculates the mean and standard deviation of the error.

Next, you specify the desired confidence level _(e.g., 95% confidence level)_ and use the `stats.norm.ppf` function from the `scipy.stats` module to calculate the critical value based on the confidence level. Finally, the margin of error is computed by multiplying the critical value by the standard error, which is the standard deviation divided by the square root of the number of observations.

```python
import numpy as np
import pandas as pd
import scipy.stats as stats

# Example DataFrame with actual and predicted values
df = pd.DataFrame({'Actual': [10, 15, 20, 25, 30],
                   'Predicted': [12, 18, 22, 28, 32]})

# Calculate the error (residual) between actual and predicted values
df['Error'] = df['Actual'] - df['Predicted']

# Calculate the mean and standard deviation of the error
error_mean = df['Error'].mean()
error_std = df['Error'].std()

# Define the desired confidence level (e.g., 95%)
confidence_level = 0.95

# Calculate the critical value based on the confidence level
z_score = stats.norm.ppf((1 + confidence_level) / 2)

# Calculate the margin of error
margin_of_error = z_score * (error_std / np.sqrt(len(df)))

print('Margin of Error:', margin_of_error)
```
The formula to calculate the margin of error is: **Margin of Error = Critical Value * Standard Error**

Here's an example code that calculates the margin of error given a sample size, standard deviation, and confidence level:

```python
import scipy.stats as stats
import math

# Example variables
sample_size = 500
standard_deviation = 0.05
confidence_level = 0.95

# Calculate critical value
z_score = stats.norm.ppf((1 + confidence_level) / 2)  # For a two-tailed test
critical_value = z_score * standard_deviation / math.sqrt(sample_size)

# Calculate margin of error
margin_of_error = critical_value * standard_deviation

print('Margin of Error:', margin_of_error)
```

In this example, `sample_size` represents the size of the sample, `standard_deviation` represents the standard deviation of the population (or an estimate if it is unknown), and `confidence_level` represents the desired level of confidence _(e.g., 0.95 for 95% confidence)_. The code uses the `stats.norm.ppf` function from the `scipy.stats` module to calculate the critical value based on the confidence level. It then multiplies the critical value by the standard deviation divided by the square root of the sample size to calculate the margin of error.

## 📰 Articles

- [Margin of error](https://en.wikipedia.org/wiki/Margin_of_error), Wikipedia
- [Margin of Error: Formula and Interpreting](https://statisticsbyjim.com/hypothesis-testing/margin-of-error/)
- [Margin of Error: Definition, Calculate in Easy Steps](https://www.statisticshowto.com/probability-and-statistics/hypothesis-testing/margin-of-error/)
- [Margin of Error: Definition + Easy Calculation with Examples](https://www.questionpro.com/blog/margin-of-error/)

---

# 💠 Measures

## 🔹 Mean directional accuracy (MDA)

**Mean directional accuracy (MDA)**, also known as mean direction accuracy, is a measure of prediction accuracy of a forecasting method in statistics. It compares the forecast direction (upward or downward) to the actual realized direction. 

It is a popular metric for forecasting performance in economics and finance. MDA is used where we are often interested only in the directional movement of variables of interest.

**The formula for calculating the MDA**

MDA measures how often the predicted direction of a time series matches the actual direction of the time series. To calculate MDA, you look at the signs of the differences between consecutive actual values and the signs of the differences between consecutive predicted values. If the signs are the same (i.e., both positive or both negative), that means the predicted direction matches the actual direction. You count how many times this happens, and divide by the total number of possible comparisons (which is one less than the length of the time series, because you can’t compare the first value to anything). This gives you the MDA value, which ranges from 0 to 1, with 1 indicating perfect directional accuracy.

MDA = Number of times the signs of the differences between consecutive actual values are the same as the signs of the differences between consecutive predicted values / (N – 1)

where N is the length of the time series.

In mathematical notation, this can be expressed as:

`MDA = sum(i=2 to N) sign(actual[i] – actual[i-1]) * sign(predicted[i] – predicted[i-1]) / (N – 1)`

where sign(x) returns the sign of x (i.e., -1 if x < 0, 0 if x == 0, and 1 if x > 0).

```python
import numpy as np

def mda(actual, predicted):
    """
    Calculates the Mean Directional Accuracy (MDA) for two time series.
    
    Parameters:
    actual (array-like): The actual values for the time series.
    predicted (array-like): The predicted values for the time series.
    
    Returns:
    float: The MDA value.
    """
    actual = np.array(actual)
    predicted = np.array(predicted)
    
    # calculate the signs of the differences between consecutive values
    actual_diff = np.diff(actual)
    actual_signs = np.sign(actual_diff)
    predicted_diff = np.diff(predicted)
    predicted_signs = np.sign(predicted_diff)
    
    # count the number of times the signs are the same
    num_correct = np.sum(actual_signs == predicted_signs)
    
    # calculate the MDA value
    mda = num_correct / (len(actual) - 1)
    
    return mda
```

### 📰 Articles

- [Mean directional accuracy](https://en.wikipedia.org/wiki/Mean_directional_accuracy#:~:text=Mean%20directional%20accuracy%20(MDA)%2C,to%20the%20actual%20realized%20direction.), Wikipedia
- [Mean directional accuracy of time series forecast](https://datasciencestunt.com/mean-directional-accuracy-of-time-series-forecast/)

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

# :octocat: GitHub

- [forecasting_metrics.py](https://gist.github.com/bshishov/5dc237f59f019b26145648e2124ca1c9)

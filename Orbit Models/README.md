# Orbit
> by UBER

- **Paper:** [Orbit: Probabilistic Forecast with Exponential Smoothing](https://arxiv.org/abs/2004.08492)

Orbit (**O**bject-**OR**iented **B**ayes**I**an **T**ime Series) is a general interface for **Bayesian exponential smoothing model**. The goal of Orbit development team is to create a tool that is easy to use, flexible, interitible, and high performing (fast computation). Under the hood, Orbit uses the probabilistic programming languages (PPL) including but not limited to Stan and Pyro for posterior approximation (i.e, MCMC sampling, SVI). Below is a quadrant chart to position a few time series related packages in our assessment in terms of flexibility and completeness. Orbit is the only tool that allows for easy model specification and analysis while not limiting itself to a small subset of models. For example Prophet has a complete end to end solution but only has one model type and Pyro has total specification model flexibility but does not give an end to end solution. Thus Orbit bridges the gap between business problems and statistical solutions.

## Models

### Local Global Trend (LGT)

Local Global Trend (LGT) was created to be able to work with outliers, anomalies data. This model is devised to forecast non-seasonal time series. This model is particularly useful for short time series. The LGT model is constructed based on Holt’s linear trend method. The model is designed to allow for a more general term of error by allowing for heteroscedasticity and the addition of a constant “global” trend in the model.

In this model taking a two-sided 68% confidence interval (or mean).

> On a normal distribution about 68% of data will be within one standard deviation of the mean


## Stable version

- [Orbit: A Python Package for Bayesian Forecasting](https://github.com/uber/orbit/tree/master)
- [Orbit’s Documentation](https://orbit-ml.readthedocs.io/en/stable/)
- [Quick Start](https://orbit-ml.readthedocs.io/en/stable/tutorials/quick_start.html#)


Orbit is a general interface for **Bayesian time series modeling**. 
Currently, it supports concrete implementations for the following models:
1. Exponential Smoothing (ETS)
2. Damped Local Trend (DLT)
3. Local Global Trend (LGT)
4. Kernel Time-based Regression (KTR-Lite)

It also supports the following sampling methods for model estimation:
1. Markov-Chain Monte Carlo (MCMC) as a full sampling method
2. Maximum a Posteriori (MAP) as a point estimate method
3. Variational Inference (VI) as a hybrid-sampling method on approximate distribution

Orbit enables the easy decomposition of a KPI time series into **trend**, **seasonality**, and **marketing channels effects**. This decomposition enables unbiased forecasting and dynamic insights, including cost curves and ROAS of marketing channels.

### Installation

**Install from PyPi:**

      pip install orbit-ml

**Install from source:**

```@bash
$ git clone https://github.com/uber/orbit.git
$ cd orbit
$ pip install -r requirements.txt
$ pip install .
```

## Latest dev version

- [Orbit: A Python Package for Bayesian Forecasting](https://github.com/uber/orbit/tree/dev)
- [Orbit’s Documentation](https://orbit-ml.readthedocs.io/en/latest/) latest dev version
- [Quick Start](https://orbit-ml.readthedocs.io/en/latest/tutorials/quick_start.html)

### Installation

**Installing from Dev Branch:**

      pip install git+https://github.com/uber/orbit.git@dev

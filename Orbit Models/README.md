# Orbit

> by UBER

Orbit (**O**bject-**OR**iented **B**ayes**I**an **T**ime Series) is a general interface for Bayesian time series modeling. The goal of Orbit development team is to create a tool that is easy to use, flexible, interitible, and high performing (fast computation). Under the hood, Orbit uses the probabilistic programming languages (PPL) including but not limited to Stan and Pyro for posterior approximation (i.e, MCMC sampling, SVI). Below is a quadrant chart to position a few time series related packages in our assessment in terms of flexibility and completeness. Orbit is the only tool that allows for easy model specification and analysis while not limiting itself to a small subset of models. For example Prophet has a complete end to end solution but only has one model type and Pyro has total specification model flexibility but does not give an end to end solution. Thus Orbit bridges the gap between business problems and statistical solutions.

- [Orbit: A Python Package for Bayesian Forecasting](https://github.com/uber/orbit)
- [Orbit’s Documentation](https://uber.github.io/orbit/)
- [Quick Start](https://uber.github.io/orbit/tutorials/quick_start.html)
- [Orbit: Probabilistic Forecast with Exponential Smoothing](https://arxiv.org/abs/2004.08492) Paper

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
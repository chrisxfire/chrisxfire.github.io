---
title: maximum likelihood estimation and confidence intervals
date: 2021-06-20T00:00:00-06:00
draft: false
weight: 1
---

# maximum likelihood estimation
- **Maximum likelihood estimation** – a method of estimating the parameters of a probability distribution by maximizing a *likelihood function*.  
	- It finds the values of *parameters* (like mean and standard deviation for a normal distribution, or lambda for a Poisson distribution) that result in the curve that best fits the data. 
- **Likelihood function** – measures the fit (support) of a statistical model to a sample of data for given values of the unknown parameters.
	- It measures the evidential support provided by data for particular parameter values.
	- It is formed from the joint probability distribution of a sample.
	- It treats random variables as fixed at the observed values.
- **Parameter** – a value that summarizes or describes an aspect of a statistical population.
- **Confidence interval** – an estimated interval within which an unknown parameter may plausibly lie.
	- It describes ranges of parameter values that are consistent with data.
		
# Probability model parameters (mean, SD, etc) can be estimated from the data via MLE
- Estimating parameters is fitting the model to the data.
- Parametric distributions, regression models, Markov chain models, etc. can all be fit by MLE.

# Poisson rate (lambda) can be estimated from the data with MLE
- `n` = arrivals
- `lambda` = expected arrivals
- `dpois(n, lambda)` = probability of n arrivals if lambda arrivals are expected.
- Keep `n` fixed and vary `lambda` to find the maximum value.

If n is known (fixed), and lambda is varied, this returns a likelihood function.
- For Poisson, the MLE of `lambda = n / time`.

# poisson regression
- Normally-distributed random variables can be extended to let their means depend on other variables via simple formulas:  `E(Y | x) = a + bx` (expected value of Y given x)
- Poisson probability models can be extended similarly:  `lambda = a + bx`
- This results in a Poisson regression model.
  - The parameters in this model are estimated from data by MLE.

# calculate confidence intervals for mean of a poisson distribution
```r
install.packages("DescTools")
library(DescTools)
PoissonCI(n)			# return the confidence interval for n where n is the mean of a Poisson distribution
```

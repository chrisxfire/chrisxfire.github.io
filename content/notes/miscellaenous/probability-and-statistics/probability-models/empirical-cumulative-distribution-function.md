---
title: notes > miscellaenous > probability and statistics > probability models > empirical cumulative distribution function
date: 2021-06-18T00:00:00-06:00
draft: false
weight: 1
---

# ECDF
If we do not have a probability model (like `pnorm()`), we can use the data itself as a model with ECDF.

# Prediction via simulation using rdist() and ecdf()
`ecdf(x)(y)` returns a fraction of numbers in data vector x that are no greater than value y.
- x is a data vector
- y is where we evaluate `ecdf(x)`

`rnorm(n, mean, sd)` samples n times from a normal distribution with parameters mean and sd.
- also: `rbinom()`, `rexp()`, `rpois()`

Example:
- The waiting time at a shop is approximately normally distributed with mean = 75 minutes and SD = 25 mins.  What is the probability that a customer's waiting time will exceed 90 minutes?
```r
set.seed(1)					        # set the seed value for the RNG
data = rnorm(100, mean=75, sd=25)	# samples 100 times from normal distribution model
ecdf(data)(60) = 0.233			    # empirical fraction of waiting times <= 60 minutes
1 - ecdf(data)(90) = 0.225			# empirical fraction of waiting times < 90 minutes
```

# Plotting an ECDF using plot()
```r
plot(ecdf(dv))
```

# Goodness-of-Fit Testing
- **Goodness of fit** – describes how well a model fits a set of observations.
- This is hypothesis testing of whether a model fits the data.
- Even the best-fitting model may not describe the data adequately.
- It is a test of the null hypothesis that observations (data) are drawn from a specified distribution, or from a specified family of distributions (ie: normal).
- We test the null hypothesis that the ECDF for the model we have fit does not differ from the ECDF of the data.
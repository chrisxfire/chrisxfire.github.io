---
title: probability model statistics
date: 2021-06-19T00:00:00-06:00
draft: false
weight: 1
---

# means
Definitions:
- The mean of a random variable (rv) is its average value.
- The mean of a discrete random variable (rv) is the sum of all its possible values weighted (multiplied by) their probabilities:  
	- `sum over x values of x * p(x)`
- **Bernoulli rv** – single binomial trial
- The mean of a Bernoulli random variable having value 1 with probability p and otherwise value 0 with probability 1 - p: 
	- `p * 1 + (1 - p) * 0 = 0 p`
- The mean of a continuous random variable is the sum of all its possible values weighted by their probability densities
- `E(X)` = "expectation" of X = mean(X)

# Variance (Population)
Definitions:
- The variance of an rv is the average squared distance of its values from its mean value:
	- var(X) = E[X - mean(X)]^2 = mean squared error of estimate
	- Any constant has variance = 0
	- Alternative notation: E[X - E(X)]^2
- Variance of Bernoulli rv (value 1, prob p, else 0): 
	- `p * (1 - p)^2 + (1 - p) * (0 - p)^2 = p * (1 - p) * (1 - p + p) = p(1 - p)`

# Standard Deviation (Population)
Definitions:
- $\sigma$ = standard deviation
- $\sigma^2$ = variance
- $\sigma(x)$ = average distance of values from $\overline{x}$
- $\sigma(x)$ indicates how spread out the Probability Density Function of $x$ is around its mean

# Means, Variances, Standard Deviations (Sample)
- For Samples,  `mean = (sum of values) / (number of values - 1)`
- This changes the output of variance and standard deviation.
- Sample mean $Y \over n$ is an unbiased estimate of the population mean $\sum_{x}$

```r
mean(x)	# calculate the sample mean of x
var(x)	# calculate the sample variance of x
sd(x)	# calculate the sample standard deviation of x
```

# Useful Laws of Means, Variances, Standard Deviations
1. Mean of a sum of RVs is the sum of their means
    - `E(X + Y) = E(X) + E(Y)`
    - Mean of binomial RV with size = n, prob = p, is `n * p`
1. Variance of a sum (or difference) of independent RVs = Sum of their variances
    - `var(X + Y) = var(X) + var(Y)` if X, Y are independent
    - Variance of binomial RV with size = n, prob = p, is `np(1 - p)`
1. If X is rescaled (multiplied by value a)
    - `E(aX + b) = aE(X) + b` for any a, b
1. The SD of sample mean = SD of population / `sqrt(n)`:
    - `sd(aX + b) = a * sd(X)`
    - This is the standard error of sample mean `Y/n`

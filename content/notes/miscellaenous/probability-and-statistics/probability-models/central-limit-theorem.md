---
title: notes > miscellaenous > probability and statistics > probability models > central limit theorem
date: 2021-06-19T00:00:00-06:00
draft: false
weight: 1
---

# Central Limit Theorem(s)
Definition: 
- The sum of many independent RVs has an approximately normal distribution.
Rule: 
- 30 RVs is usually enough to justify a normal approximation for their sample mean (or for their sum).

# Checking CLT with repeated samples using sample()
```r
x = c(0, 0, 10, 50)
set.seed(1)
sample(x, 10, replace = TRUE) # randomly sample 10 times from x
```

# Practice Problem
- Q: Suppose that each of 1,000 members of an insurance pool independently has a 0.6 probability of submitting a claim in a year.  Using CLT, what is the approximate probability of receiving more than 630 claims?
- A: 
	- Y = total number of claims submitted
		- This is a binomial RV with n = 1000, p = 0.6
	- `E(Y) = n * p = 1000 * 0.6 = 600`
	- `var(Y) = np(1 - p) = 1000 * 0.6 * 0.4 = 240`
	- `sd(Y) = var(Y)^0.5 = 15.491`
```r
1 - pnorm(630, 600, 15.491) 
```
> = 0.02639662
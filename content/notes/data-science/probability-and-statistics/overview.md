---
title: overview
date: 2021-06-06T00:00:00-06:00
draft: false
weight: -1
---

# Concepts
## Null hypothesis 
A default hypothesis that a quantity to be measured is zero (null).
- The null hypothesis is true if data values are drawn from the hypothesized distribution.

## p-value 
The probability of obtaining observed, or more extreme, results when the null hypothesis is true.
- The probability that an observed difference could have just occurred by chance.
- A p-value near zero provides evidence *against* the null hypothesis.

## t-test
A t-test automatically tests the null hypothesis that the mean value of the data is zero.
- T-tests assume:
  - The distribution is normal
  - The distribution remains fixed

### Example
Example:
- A random sample of 5 customers spent $10.24, $12.31, $9.38, $14.03, and $11.72.  
- Predict how much the next 100 customers will spend.

```r
x = c(10.24, 12.31, 9.38, 14.03, 11.72)
t.test(x)
```

## OSEMN data science framework
- Obtain — gather data from relevant sources
- Scrub — clean data to formats that machine understands
- Explore — Find significant patterns and trends using statistical methods
- Model — Construct models to predict and forecast
- iNterpret — put the results into good use

# Simpson's Paradox
- A phenomenon in which a trend appears in several groups of data but disappears or reverses when the groups are combined.

Lessons:
- What is true for a population may be false for each subpopulation.
- Many proportions and differences of proportions can only be interpreted clearly in the context of multiple causally relevant variables (multivariate models).

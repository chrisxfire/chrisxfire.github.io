---
title: notes > miscellaenous > probability and statistics > probability models > overview
date: 2021-06-12T00:00:00-06:00
draft: false
weight: -1
---

# Probability Models
Analysis starts with exploration, visualization, summary…  
…and then often continues with building probability models (OSMEN framework).

# The Data Science Process
1. Ask an interesting question
   1. What is the scientific goal?
   2. What would you do if you had all the data?
   3. What do you want to predict or esimate?
2. Get the data
   1. How was the data sampled?
   2. Which data is relevant?
   3. Are there privacy issues?
1. Explore the data
   1. Plot the data.
   2. Anomalies?
   3. Patterns?
1. Model the data
   1. Build a model.
   2. Fit the model.
   3. Validate the model.
1. Communicate and visualize the results
   1. What did we learn?
   2. Do the results make sense?
   3. Can we tell a story?

# Probability Distribution Models
Definitions:
- **Probability model** — predicts values of uncertain quantities.
- **Uncertain quantities** are modeled as **random variables** (assuming the quantities are discrete and not continuous).
- **Random variable** — a variable with more than one possible value; each value occurs with some probability.

Notes:
- `P(x)` denotes probability distribution that random variable `X` has value `x`.
  - May also be denoted as `P(X = x)`
- For a single random variable X, a probability distribution `P(x)` is the probabiliy model for its value. 
- **Probability Density Function** (PDF) – Returns the probability distribution for a continuous random variable.
- **Probability Density** – The probability of a continuous probability distribution.
  - Example: A man does not have a probability of being 6 feet tall, but he does have a probability of being between 5 and 6 feet tall.

# Multivariate Probability Models
A **multivariate probability model** provides a **conditional probability distribution** for output `y` given observed values of input `x`.
`P(y | x)` – conditional probability of `y` given `x` (R uses `~` instead of `|`)
- x = **independent variables** (aka explanatory variables, predictors)
- y = **dependent variable** (aka response, risk, output)
- Predicted probability of y depend on (or are "conditioned on") both the x values and the model assumptions.
- Examples of conditional probability relationships: 
    - `disease ~ symptoms`, `future ~ past`, `classification ~ features`, `risk ~ factors`, `behavior ~ offers`

**Cumulative Distribution Function** (CDF) – Returns the probabilities that the outcome falls inside a specified interval.

# Main Steps in Probability Modeling
1. Select a model to describe data (or, learn models from data (ie: machine learning))
2. Fit the model to data
   1. Estimate parameters (ie: regression coefficients)
   1. Provide best guesses ("point estimates") and confidence intervals
3. Validate model's predictive accuracy
   1. Use cross-validation to characterize prediction errors (splitting data into subsets and fit/train model using subsets not used in other parts of the model)
   2. Error measures: Mean Squared Error for continuous variables; misclassification rates for binary or discrete variables
4. Use model to make predictions and characterize remaining uncertainties 
   1. A probabilisitic prediction is a probability distribution
5. Apply the model to decisions

# Useful Probability Models
These are all probability models because they all calculate conditional probabilities for outputs given observed inputs.

## Probability distribution models
- Bionomial distribution (2 outcomes)
- Normal distribution (continuous outcome, sums of independent random variables)
- Poisson distribution (count outcome, number of rare events)

## Regression models
- Logistic (binary dependent variable (ie: death, pregnancy))
- Linear (for continuous dependent variable)
- Poisson or generalized Poisson (for count dependent variables)
- Flexible regression models (nonparametric (smoothing) regression)

## Others
- Time series and dynamic regression models (Trends; changes over time)
- Bayesian networks (many variables affecting each other)
- Surival models
- Transition models and generalizations
    - Dynamic causal models; simulation of changes over time
    - Markov models of policy impacts
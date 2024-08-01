---
title: overview
date: 2023-12-05T00:00:00-06:00
draft: false
weight: -1
---

# Abstract
The goal of machine learning is to use data to create a predictive model. Machine learning models encapsulate a *function* to calculate an output based on one or more inputs. It creates a model from data.

Consists of two phases:
1. **Training** — the process of defining the function.
2. **Inferencing** — using the model to predict new values.

# Training Machine Learning Models
Consider an ML model that predicts ice cream sales based on the weather:
- Training data comes from past *observations*.
    - *Features* ($x$) — attributes of the thing being observed (temperature; rainfall; wind speed).
      - Usually a *vector*: [$x_1, x_2, x_3, ...$]
    - *Labels* ($y$) — values (the number of ice creams sold on a day).
- Algorithms are applied to the training data to find a relationship between the features and the labels and then generalize that relationship as a calculation.
  - This is *fitting* the data to a function.
- The algorithm's output ($\hat{y}$) is a *model* that encapsulates the calculation it performs as a function.

# Types of Machine Learning
- [Supervised Machine Learning](../supervised/)
- [Unsupervised Machine Learning](../unsupervised/)
- [Deep Learning](../deep-learning)
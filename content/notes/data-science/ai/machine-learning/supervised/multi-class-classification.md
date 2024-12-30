---
title: multi class classification
date: 2023-12-05T00:00:00-06:00
draft: false
weight: 1
---

# Abstract [[Reference](https://learn.microsoft.com/en-us/training/modules/fundamentals-machine-learning/6-multiclass-classification)]
In multi-class classification supervised machine learning, the label represents one of multiple possible classes.
- Usually, the labels are mutually exclusive.
  - In *multi-label classification models*, there may be more than one valid label for an observation.
- Follows the same train > iterate > evaluate process as regression and binary classification.
- Examples:
  - The specifies of penguin based on its physical measurements.
  - The genre of a movie based on its cast, director and budget.

## Training Multi-class Classification Models
Use an algorithm to fit the training data to a function that calculates a probability value for each possible class.

### One-vs-Rest (Ovr) Algorithm
A binary classification function is trained for each class:
- $f^0(x)=P(y=0 | x)$
- $f^1(x)=P(y=1 | x)$
- ...

That function — a sigmoid function — calculates the probability that the observation is an example of that class.

### multinomial algorithms
These algorithms create a single function that returns a multi-valued output.
- The output is a vector (array of values) that contains the probability distribution for all possible classes with a probability score for each class:
  - $f(x)= [P(y=0|x), P(y=1|x), ...]$
- In the resulting vector (for example, $[0.2, 0.3, 0.5]$) the elements represent the probabilities for class 0, 1, 2 and so on.
- An example of such a function is the *softmax* function.

## Multi-class Classification Model Evaluation Metrics
Multi-class classification models are evaluated calculating binary classification metrics for each individual class.
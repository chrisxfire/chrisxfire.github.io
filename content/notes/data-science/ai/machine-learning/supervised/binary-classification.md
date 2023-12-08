---
title: binary classification
date: 2023-12-05T00:00:00-06:00
draft: false
weight: 1
---

# Abstract [[Reference](https://learn.microsoft.com/en-us/training/modules/fundamentals-machine-learning/5-binary-classification)]
In binary classification supervised machine learning, the label represents a *class* that describes whether the observed item *is* or *is not* an instance of a specific class.
- Predict one of two mutually exclusive outcomes.
- Example: whether a patient is at risk for diabetes based on weight, age, blood glucose level, etc.

# Training Binary Classification Models
- Use an algorithm to fit the training data to a function that calculates the *probability* of the class label being $true$.
- The *total probability* of all classes is $1.0$.

## Logistic Regression Algorithm
A binary classification algorithm that derives a *sigmoid* (S-shaped) function:   
![A logistic regression](../logistic-regression.png)

- Despite the name, it is a *classification* algorithm, not a *regression* algorithm.
- The function the algorithm produces describes the probability of $y$ being $true$ for a given value of $x$: $f(x)=P(y=1 | x)$

# Binary Classification Model Evaluation Metrics
## Confusion Matrix
A matrix of the number of correct and incorrect predictions for each possible label class:  
![A confusion matrix](../confusion-matrix.png)
- Where
  - $y=0$ and $\hat{y}=0$ — true negatives ($TN$)
  - $y=0$ and $\hat{y}=1$ — false positive ($FP$)
  - $y=1$ and $\hat{y}=0$ — false negatives ($FN$)
  - $y=1$ and $\hat{y}=1$ — true positives ($TP$)
- The correct (true) predictions are from top left to bottom right.

## Accuracy 
The proportion of predictions that are correct.
- `(TN + TP) / (TN+FN+FP+TP)`
- Can be misleading. Consider: 11% of the population has diabetes.  If a model always predicts 0, it would achieve an accuracy of 89%. 
  - Accuracy **does not** distinguish how well the model performs at predicting $1$ for positive cases and $0$ for negative cases.

## Recall (aka True Positive Rate (TPR))
- The proportion of positive cases that the model identified correctly.
- `(TP / (TP + FN)`
- From the number of patients who *have* diabetes, the number the model *predicted* to have diabetes.

## Precision
- Similar to Recall
- The proportion of *predicted* positive cases where the true label is *actually* positive.
- `(TP / (TP + FP))`
- From the number of patients the model *predicted* to have diabetes, the number that *have* diabetes. 

## F1-score 
An overall metric that combines recall and precision.
- `(2x Precision x Recall) / (Precision + Recall)`

## False Positive Rate (FPR)
- `FP / (FP + TN)`

# Received operator characteristic (ROC) curve 
Compares the TPR and FPR for every possible threshold value between 0.0 and 1.0:  
![A ROC curve](../roc.png)
- *Area Under the Curve* (AUC)
  - A perfect model would go straight up the TPR axis then across the FPR axis.
  - The dotted blue line represents the results that would be achieved by randomly guessing a binary label (50%).
    - Any AUC higher than 0.5 indicates the model performs better at the prediction that random guessing.
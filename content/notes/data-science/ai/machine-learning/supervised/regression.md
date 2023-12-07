---
title: regression
date: 2023-12-05T00:00:00-06:00
draft: false
weight: 1
---

# Abstract [[Reference](https://learn.microsoft.com/en-us/training/modules/fundamentals-machine-learning/4-regression)]
In regression-based supervised machine learning, the label predicted by the model is a numeric value.

# Training Regression Models
1. Split the data (randomly) to create a training dataset and a validation dataset.
2. Use a regression algorithm (perhaps linear regression) to *fit* the training data to a model.
3. Use the validation dataset to test the model by predicting labels for the features.
4. Evaluate the model's performance by comparing the known *actual* labels in the validation dataset to the labels that the model predicted.
5. Repeat with different algorithms and/or parameters.

# Regression Model Evaluation Metrics
## Mean Absolute Error (MAE)
The level by which the *prediction* varied from the *actual*.

## Mean Squared Error (MSE)
Squares the individual errors to "amplify" larger errors.
- Useful for determining, along with the MAE, if the model makes many—but smaller—errors or fewer—but larger—errors.
- Because it squares the errors, it does not represent *variance*.


## Root Mean Squared Error (RMSE)
The square root of the MSE (to get back to variance).

## Coefficient of Determination ($R^2$)
Measures the proportion of variance in the validation results that can be explained by the model as opposed to some anomalous aspect of the validation data.
- It determines how *fit* the model is to the data.
- It is the sum of squared differences between predicted and actual labels with the sum of squared differences between the actual label values and the mean of actual label values:
- $R^2=1-\sum_{} {(y -\hat{y})^2} / \sum_{} {(y-\hat{y})^2}$
- The resulting value between 0 and 1 describes the proportion of the variance explained by the model.
- The closer the value is to $1$, the better the model fits the data.
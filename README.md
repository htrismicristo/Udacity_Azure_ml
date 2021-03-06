# Optimizing an ML Pipeline in Azure

## Overview
This project is part of the Udacity Azure ML Nanodegree.
In this project, we build and optimize an Azure ML pipeline using the Python SDK and a provided Scikit-learn model.
This model is then compared to an Azure AutoML run.

## Summary
This dataset contains data about bank customers. We aim to predict the y variable based on different customer characteristics. On the other hand, the best performing model was the VotingEnsemble found via AutoML with an accuracy of 0.9173.

## Scikit-learn Pipeline
A logistic regression model was used for doing classification. I used automated hyperparameter tuning with hyperdrive to find the best hyperparameters for the model. On one hand, I used Random Sampling because is faster than grid sampling and both yield almost the same accuracy. Besides, I used Bandit Policy since it terminates runs where the primary is not within the specified slack factor compared to the best performing run. By using this hyperdrive configuration, the best regularization strength was 0.28 and the recommended number of iterations to converge was 300. With this hyperparameters, the classification model gave an accuracy of 0.9101.

## AutoML
The VotingEnsemble model generated by AutoML was more accurate than the logistic regression model trained via hyperdrive. This model got an AUC of 0.948 and the most relevant customer features for the classification task were duration (0.647), nr.employed (0.392) and emp.var.rate (0.310).

## Pipeline comparison
The logistic regression model was trained using hyperdrive for choosing the best hyperparameter values. Then, those values were used to train the model and get the highest classification accuracy. Instead, the VotingEnsemble model was generated automatically based on simple configuration parameters like the kind of task, the primary metric and the number of cross validations.

## Future work
The logistic regression model might improve its results with a lower values for the regularization hyperparameter (--C) or a bigger training dataset. On the other hand, the VotingEnsemble model might be better with a larger number of cross validations. 

## Proof of cluster clean up
I deleted it within the code.
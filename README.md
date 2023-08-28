![H1N1 vaccine](https://github.com/Jko0425/phase-3-project/blob/main/Images/h1n1%20vaccine.webp)
# Predicting Flu Vaccination Rate
## Table of Contents
* [Overview](https://github.com/Jko0425/phase-3-project/blob/main/README.md#overview)
* [Business Problem](https://github.com/Jko0425/phase-3-project/blob/main/README.md#business-problem)
* [Data](https://github.com/Jko0425/phase-3-project/blob/main/README.md#data)
* [Models](https://github.com/Jko0425/phase-3-project/blob/main/README.md#models)
* [Evaluation of the model](https://github.com/Jko0425/phase-3-project/blob/main/README.md#evaluation-of-the-model)
* [Conclusion](https://github.com/Jko0425/phase-3-project/blob/main/README.md#conclusion)

## Overview
In recent events, vaccines have been a controversial topic. From governmental conspiracies to distrust in the health system, the efficiency of vaccines are not enough to get people to medical clinics. It is safe to say that regardless of the research behind vaccines, other variables like doubt and education may impact the patient's decision in receiving the vaccine. We will create several models that will take in all of these variables and predict the most accurate vaccination rate of each patient.

## Business Problem
Many pharmaceutical companies are responsible for producing much of our vaccines, including their very successful [COVID-19 vaccine](https://www.fiercepharma.com/pharma/pfizer-to-exceed-100b-revenue-2022-thanks-to-covid-19-drug-and-vaccine-analyst). Despite the success, [a good percentage of US citizens refused to take the vaccine](https://usafacts.org/visualizations/covid-vaccine-tracker-states). Pfizer can use these predictive models to calculate how successful the vaccine will potentially be. They may also observe the differences in vaccination rate of each feature and make further investigations on why differences in a specific feature exists.

## Data
The data is provided by [Drivendata](https://www.drivendata.org/competitions/66/flu-shot-learning/page/210/). They provide three datasets: training labels, training features, and the test set which is used to make our predictions. The labels contain two target variables: `h1n1_vaccine` and `seasonal_vaccine`, where both labels contain binary values where 0 = No and 1 = Yes. [We will be working with 36 features](https://www.drivendata.org/competitions/66/flu-shot-learning/page/211/#sub_values).

## Models
Three models are created in an attempted to find the most accurate. The parameters for each of the models are shown as follows:
| Model | Parameters |
| ----- | ---------- |
| Logistic Regression | solver='liblinear', fit_intercept=False, C=1e12 |
| KNN Algorithm | p=2, n_neighbors=39 (H1N1), n_neighbors=60 (seasonal) |
| Decision Tree (H1N1) | min_samples_leaf=161, min_samples_split=0.1, max_leaf_nodes=27, max_depth=4 |
| Decision Tree (seasonal) | min_samples_leaf=143, min_samples_split=0.1, max_leaf_nodes=41, max_depth=5 |

Of these three models, the logistic regression returned the most favorable results. The evaluation and metrics of the model are noted.

## Evaluation of the model
Out of the three models (logistic, nearest neighbor, decision tree) the logistic model had the greatest accuracy and lowest cost. We then calculate the performance of this model by observing calculating metrics. 
### Confusion Matrix:
It provides a plot that shows the density of each prediction. Starting at the top right and moving counterclockwise, the values tells us the number of false positives, true positives, false negatives, and true negatives.
![Confusion matrix h1n1](https://github.com/Jko0425/phase-3-project/blob/main/Images/Confusion%20matrix%20h1n1.png)

* __Precision:__ 0.68
* __Recall:__ 0.43
* __Accuracy:__ 0.84
* __F1:__ 0.53

![Confusion matrix seasonal](https://github.com/Jko0425/phase-3-project/blob/main/Images/Confusion%20matrix%20seasonal.png)

* __Precision:__ 0.77
* __Recall:__ 0.74
* __Accuracy:__ 0.78
* __F1:__ 0.76
### ROC curve:
Another way to measure the performance of the model by using two parameters: true positive rate and false positive rate. By measuring the area underneath the curve (AUC), we can see how well the model differentiates between the negative and positive class.
#### H1N1 ROC curve
![ROC h1n1](https://github.com/Jko0425/phase-3-project/blob/main/Images/ROC%20h1n1.png)
__AUC:__ 0.8292943967586459
#### Seasonal ROC curve
![ROC seasonal](https://github.com/Jko0425/phase-3-project/blob/main/Images/ROC%20seasonal.png)
__AUC:__ 0.8507245791998279

## Result of the model
By feeding in a sample of given variables, the model was able to predict the probability of vaccination for both the seasonal and H1N1 vaccine:
| Vaccine | Probability |
| ------- | ----------- |
| H1N1 | 0.21 |
| Seasonal | 0.46 |

## Conclusion
When observing the rate of vaccination, we saw how certain variables affected the rate. Pfizer can focus on these variables:
* __Target demographic__ If Pfizer does wish to push an H1N1 vaccine they can focus on people of specific ages and education as these two groups are more likely to be vaccinated.
* __Understanding why vaccines do poorly on certain groups__ On the other hand, the company can investigate why there is such a poor vaccination rate in a specific group. For example, why is there a difference in vaccination rate between races? There may be a social explanation, but a company should understand why these differences exist in order to maximize their profits.

If Pfizer follows the results of the model, they can focus on creating vaccines for the seasonal flu as the model returned higher probabilities of receiving the vaccine.

## About the author
Written and coded by: Joshua Ko
Email: joshuawko@gmail.com
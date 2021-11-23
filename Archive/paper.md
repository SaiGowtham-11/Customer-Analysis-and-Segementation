---
title: Discover Malicious Websites Using Data Mining Algorithms
date: November 22, 2021
author: Sai Gowtham, Srinivas Gutta, Manish Mapakshi, Pratibha Awasthi, San JosÃ©️ State University

header-includes: |
  \usepackage{booktabs}
  \usepackage{caption}
---

# Abstract


# Introduction

    Phishing is a deceptive practice in which an attacker attempts to obtain sensitive information from a victim. Emails, text messages, and websites are commonly used in these types of assaults. Phishing websites, which are on the rise these days, have the same appearance as real websites. Their backend, on the other hand, is geared to harvest sensitive information provided by the victim. The machine learning community, which has constructed models and performed classifications of phishing websites, has recently become interested in discovering and detecting phishing websites. This research includes two dataset versions with 58,645 and 88,647 websites categorized as real or fraudulent, respectively. These files contain a collection of legitimate and phishing website examples. Each website is identified by a collection of characteristics that indicate whether it is real or not. Thus, data can be used as a source of information in the machine learning process.

# Data Description
    The data in this presentation was gathered and compiled to develop and analyze several categorization algorithms for detecting phishing websites using URL characteristics, URL resolving metrics and external services. Six groups of attributes can be found in the prepared dataset:
- attributes based on the whole URL properties 
- attributes based on the domain properties 
- attributes based on the URL directory properties 
- attributes based on the URL file properties
- attributes based on the URL parameter properties
- attributes based on the URL resolving data and external metrics.
    As shown in Figure 1, the first group is based on the values of the characteristics on the entire URL string, but the values of the next four groups are based on specific sub-strings. The final set of attributes is based on URL resolve metrics as well as external services like Google's search index.

![Separation of the whole URL string into sub-strings](./images/Fig.1.SeparationofthewholeURLstringintosub-strings.jpg)

    The dataset has 111 features in total, except the target phishing attribute, which indicates if the instance is legitimate (value 0) or phishing (value 1).  We have two versions of the dataset, one with 58,645 occurrences with a more or less balanced balance between the target groups, with 30,647 instances categorized as phishing websites and 27,998 instances labeled as legitimate. The second dataset has 88,647 cases, with 30,647 instances tagged as phishing and 58,000 instances identified as valid, with the goal of simulating a real-world situation in which there are more legitimate websites present. We have used dataset_small for further analysis and model building as it has more balanced classes.


![The distribution between classes for both dataset variations.](./images/Fig. 2. The distribution between classes for both dataset variations.jpg)


# Methods
    Our data set consists of features like quantity of character's in URL, length of URL, parameters, and more, mainly numerical or categorical datatype. During the analysis, it was observed that the data set consists of '-1' as a value which the data authors have not described. Therefore, it generated two schools of belief in the group. 

1. The features mentioned in the data set do not make sense under negative values. For example, the length of the URL can never    be negative. Hence, the negative values should be considered as missing data.
2. A considerable data involves or includes -1. Removing such data will compromise the accuracy of the result, and hence the -1    should be considered.
Hence, this write-up will follow two ways of analyzing the data.

## Method 1
## Data Preprocessing
The following are the sequential steps which we followed for the data preprocessing:
1. Dropping the duplicate rows.
2. Dropping features that have single unique values through out the column.
3. Dropping the features which have atleast 80% of data as -1. Most of these features are attributes based on the URL            parameters.
4. Replacing the -1 values with NAN values.

![Missing Data](./images/fig.5.missing data.jpg)

5. We can infer from the above fig.5 that we still have missing values. To deal with these missing data we can use different      imputation techniques such as Mean/Median/Mode imputation or use imputer algorithms like KNNimputer(), MissForest().  We        have decided to approach this problem by using both the Mean mpuation and KNN imputation and later compare results.

## KNN Imputed Data Analysis:
1. The Null data is imputed using KNN imputer with n_neighbhors:3. The distance measure used is euclidean distance.
2. Stratified split of this data to train and test data with test data size as 25%.
3. Standardizing the data using Standardscaler().
4. Three classifiers namely Logistic Regression, RandomForestClassifier, and XGBoost classifier are implemented to analyze this    data.
5. We are initializing these 3 classifiers with default parameters. Hyperparameter tuning will be done in the next phase after    feature selection.

Below figures are the metrics obtained after training the models and scoring on test data.

![Logistic Regression performance metrics](./images/fig.6. metrics_lr.jpg)

![XGBoost performance metrics](./images/fig.7. xgboost metrics.jpg)

![RandomForest performance metrics](./images/fig.8. randomforest metrics.jpg)

### Feature Importance & Selection:
    Examining the model's coefficients is the simplest technique to analyze feature importances. It has some influence on the forecast if the assigned coefficient is a large (negative or positive) number. If the coefficient is zero, on the other hand, it has no bearing on the forecast.For Logistic Regression the feature importances is derived from their respective coefficients.

    RandomForest Classifier & XGBoost Classifier have built-in feature importance. The decrease in node impurity is weighted by the likelihood of accessing that node to compute feature significance. The number of samples that reach the node divided by the total number of samples yields the node probability. The more significant the feature, the higher the value.

Below are figures of feature importances using 3 models:
![feature importance logistic_regression](./images/Fig.9. feature_importance_logistic_regression.jpg)
![feature importance XGboost](./images/Fig.10. feature_importance_XGboost.jpg)
![feature importance randomforest](./images/Fig.11. feature_importance_randomforest.jpg)

Implementing Recursive Feature Elimination (RFECV) to obtain optimal features. This algorithm calculates the importance of each feature in a recursive manner, then discards the least important feature. It begins by determining the relevance of each column's feature. It then deletes the column with the lowest relevance score and repeats the process. 
Parameters:
`estimator_: RandomForestClassifier(); cv_: StratifiedKFold(3); Scoring_:’accuracy’`

![Cross-validation vs features selected RFECV](./images/Fig.12. RFECV.jpg)

From the above Fig, We can observe that the cross-validation accuracy score doesn't change after selecting 30 features; it flattens as the number of features selected increases. Training our models on these top 30 features should increase the performance of the model.

## Mean Imputed Data Analysis:

Correlation:
Later a heatmap is plotted to find the correlation between different features.
These correletation are printed.

Outliers: 
The outliers are detected using the z score. In this methodology, the threshold is kept to 3. 
Using IQR, the outliers are removed, and a new dataset is generated. 

Modeling: 
The accuracy is retrieved using three different models. They are: 
(1) Decision Tree:
Decision tree is a predictive modelling approaches used in data mining.  It is constructed through algorithmic approach that identifies differents methods of splitting a data set based on different conditions. 
The accuracy found through decision tree is 95.65%

(2) Random Forest:
When a large number of decision tree operate as an ensemble, they make up Random Forest. Each tree in the random forest produces a class prediction, and the class with the most votes becomes the prediction of our model. The accuracy found through Random Forest is 97.52% 

(3) KNN:
KNN is a machine learning algorithm based on Supervised Learning technique. It assumes similarity between new data and available data and put new data into category that seems most similar to available categories. 
The accuracy found was 97.29%

It is concluded that the Random forest detected the best accuracy. 




# Comparisons

# Example Analysis

# Conclusions


# References




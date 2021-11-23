---
title: Discover Malicious Websites Using Data Mining Algorithms (Team 2)
date: "November 22 2021"
author: Sai Gowtham, Srinivas Gutta, Manish Mapakshi, Pratibha Awasthi, San José State University


---

# Abstract

# Introduction
Phishing is a deceptive practice in which an attacker attempts to obtain sensitive information from a victim. Emails, text messages, and websites are commonly used in these types of assaults. Phishing websites, which are on the rise these days, have the same appearance as real websites. Their backend, on the other hand, is geared to harvest sensitive information provided by the victim. The machine learning community, which has constructed models and performed classifications of phishing websites, has recently become interested in discovering and detecting phishing websites. This research includes two dataset versions with 58,645 and 88,647 websites categorized as real or fraudulent, respectively. These files contain a collection of legitimate and phishing website examples. Each website is identified by a collection of characteristics that indicate whether it is real or not. Thus, data can be used as a source of information in the machine learning process.

# Methods
## Method 1
### Data Load & Manipulation
The data is initially checked for NA values. However, it is found that there have been no such null values. 
Then, unique values of data have been checked and printed. 

### EDA
The number of 0s and 1s:
The data is analyzed to find the value counts for '0' and '1'. It was found that there are 58000 for 0s and 30647 for 1s. 
These 0s and 1s values are plotted to provide clear visuals.

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

## Data Preprocessing:
The following are the sequential steps which we followed for the data preprocessing.
<ol>
<li>Dropping the duplicate rows.</li>
<li>Dropping features that have single unique values through out the column.</li>
<li>Dropping the features which have atleast 80% of data as -1.Most of these features are attributes based on the URL parameters.</li>
<li>Replacing -1 values with NAN values.</li>
<li>We can infer from the above figure that we still have missing values. To deal with these missing data we can use different imputation techniques such as Mean/Median/Mode imputation or use imputer algorithms like KNNimputer(), MissForest().  We have decided to approach this problem by using both the Mean impuation and KNN imputation and later compare results.</li>  

# Comparisons

# Example Analysis

# Conclusions


# References

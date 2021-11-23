---
title: Discover Malicious Websites Using Data Mining Algorithms (Team 2)
date: "November 22 2021"
author: Sai Gowtham, Srinivas Gutta, Manish Mapakshi, Pratibha Awasthi, San José State University


---

# Abstract

# Introduction
Phishing is a deceptive practice in which an attacker attempts to obtain sensitive information from a victim. Emails, text messages, and websites are commonly used in these types of assaults. Phishing websites, which are on the rise these days, have the same appearance as real websites. Their backend, on the other hand, is geared to harvest sensitive information provided by the victim. The machine learning community, which has constructed models and performed classifications of phishing websites, has recently become interested in discovering and detecting phishing websites. This research includes two dataset versions with 58,645 and 88,647 websites categorized as real or fraudulent, respectively. These files contain a collection of legitimate and phishing website examples. Each website is identified by a collection of characteristics that indicate whether it is real or not. Thus, data can be used as a source of information in the machine learning process.

# Methods
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

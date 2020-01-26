# Customer Churn Prediction with Spark
Sparkify is a fictitious digital music service similar to Spotify or Pandora. Millions of users stream their favorite songs through this service everyday. Every time a user interact with the service such as playing songs, logging in/out ect, it generates log data. 

![sparkify](https://github.com/gj0706/customer_churn_prediction_with_Spark/blob/master/img/sparkify.png)

The purpose of this project is to analyze these event data and predict which users are at risk to churn canceling their service. If we can accurately identify these users before they leare, the company can offer them discounts and incentives to them and potentially save business millions in revenue.


## Table of Contents
1. [Project Description](#desc)
2. [Installation](#installation)
3. [File Description](#files)
4. [Acknowledgements](#licensing)


## Project Description<a name="desc"></a>

The goal of this project is to build and train a binary classifier that can accurately identify users  who cancelled the Sparkify music streaming service, based on the patterns obtained from their interactions with the service. A good trained model could be used to identify users who are likely to churn in advance.

The dataset used in this project is the simulated Sparkify activity data provided by Udacity. The project is carried out by leveraging the Apache Spark distributed cluster-computing framework capabilities, through Python API for Spark, PySpark. The entire model development process (data understanding, feature engineering, model selection) is performed on a subset of 128.5MB (1/100) of the full Sparkify dataset, by using Spark in local mode. 

The project consists of the following steps:

1. **Data exploration:** manipulated a subset of a large and realistic dataset with Spark SQL and Spark Dataframes;
  - Data loading
  - Data overview
  - Data cleaning: handeling missing values and drop unecessary columns.
  - Define Churn: define churn as customer who confirmed cancellation.
  - Explore potential features related to customer churn. 

2. **Feature engineering:** create relevant features for machine learning;
  - Created 11 features with 9 numerical and 2 binary features.
    - Numerical: 'totalSong','totalLifetime','avgSongsPerSession','totalThumbsup','totalThumbsdown','totalAddFriend','totalAddList','totalListenLength','totalInteraction'
    - Binary: 'downgraded','paid'

3. **Modeling:** utilized the machine learning API with Spark ML to build and tune models.
  - Feature vectorization: transform feature columns to 1 vector per feature.
  - Model selection: chose 3 models: Logistic Regression, Random Forest and Gradient Boosted Tree.
  - Hyper parameter tuning: used grid search cross validation.
  - Evaluation.






## Installation <a name="installation"></a>

No particular installation needed. This project is built on Python 3.7.4 and jupyter notebook 6.0.1.


## File Description<a name="files"></a>

The notebook `Sparkify.ipynb` contains all the code necessary for understanding the whole process. 

## AcKnowledgements<a name="licensing"></a>

Thanks Udacity for providing all the project resources. ❤


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

1. **Data exploration:** using Spark SQL and Spark Dataframes;
  - Data loading
  - Data overview
  - Data cleaning: handeling missing values and drop unecessary columns.
  - Define Churn: define churn as customer who confirmed cancellation.
  - Explore potential features related to customer churn. 

2. **Feature engineering:** 

  - Created 11 features with 9 numerical and 2 binary features.
    - Numerical: 'totalSong','totalLifetime','avgSongsPerSession','totalThumbsup','totalThumbsdown','totalAddFriend','totalAddList','totalListenLength','totalInteraction'
    - Binary: 'downgraded','paid'

3. **Metrics**

- We choose **F1 score** as our metric for model evaluation. The reasons are:
  - Our goal in this project is to predict churned user as accurately as possible, so that the company can retain as many churned users as possible by offering incentives or discounts. Thus it would be crucial if we falsely predicted a user(false negative) who actually churned as not churned. We will lose customer in this case. Therefore, we want to get relatively high recall rate. On the other hand, although offering discounts to users who didn’t churn is not a bad idea, considering cost, we want to avoid giving too many discounts for no reason. So we also need to get a relatively good precision score. F1 score is one that balance the two best.
  - Another consideration is that in our dataset, the churned users is 52 out of 225, fairly small subset and imbalanced. In this case F1 score would best evaluate our models.


4. **Modeling:** 

  - Feature vectorization: used `VectorAssembler` and `StandardScaler` from `pyspark.ml.feature` module.
  - Model selection: used `LogisticRegression`, `RandomForestClassifier` and `GBTClassifier` from `pyspark.ml.classification` module.
  - Hyper parameter tuning: used `CrossValidator`, `ParamGridBuilder` from `pyspark.ml.tuning` module. 
  - Evaluation. Used `MulticlassClassificationEvaluator` from `pyspark.ml.evaluation` module. 
  
  - Detailed explanations on this project can be find on my [medium blog post](https://medium.com/@guojian0706/customer-churn-prediction-with-spark-334f243774ec) 

5. **Results**

![Results](https://github.com/gj0706/customer_churn_prediction_with_Spark/blob/master/img/results.png)

- The best model we got is Random Forest classifier.
- The best parameter combanation for Random Forest classi is: numTrees: 40, maxDepth: 4 after we performed grid search cross validation.
- The F1 score for the best model is 0.8226.


## Installation <a name="installation"></a>

No particular installation needed. This project is built on Python 3.7.4 and jupyter notebook 6.0.1.


## File Description<a name="files"></a>

The notebook `Sparkify.ipynb` contains all the code necessary for understanding the whole process. 

## AcKnowledgements<a name="licensing"></a>

Thanks Udacity for providing all the project resources. ❤


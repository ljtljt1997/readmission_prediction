# Readmission_prediction

**Dataset: Diabetes 130-US hospitals for years 1999-2008 Data Set**

### Overall Procedures:

#### (I) Data Preprocessing:

- Read & Copy & Check data

- (1) Drop columns, rows

  (2) Deal with missing data

  (3) Re-encoding admission type, discharge type, admission source etc.

  (4) Add useful columns, eg. Service_utilization, numberchange, nummed, level i _diag j etc.

  (5) Transform other variables like age, readmitted etc.

  ...

#### (II) Modelling

- Deal with skewness and kurtosis of numeric variables - perform log / log1p transform

- Drop duplicate observations based on patients

- Get dummies to categorical variables

- Machine learning methods:

  **Logistic Regression,**

  **Decision Tree (Using entropy and gini)**

  **Random Forest (Using entropy and gini)** 

- Imbalance learning - Deal with highly imbalanced data - Use SMOTE oversampling method here
  

...
### Overall Results:

1. In the model fitting part, I first apply these three methods on X_train, Y_train and test on X_dev, Y_dev, these four dataset are randomly splitted from the original cleaned set df_pd.

   The results are not good. For example, Logistic Regression. Even though the accuracy of prediction can achieve 91%, the precision and recall are as low as 0.

   |                        | Accuracy | Precision | Recall | F1_score |
   | ---------------------- | -------- | --------- | ------ | -------- |
   | Logistic Regrssion     | 0.91     | 0.00      | 0.00   | 0.00     |
   | Decision Tree(Entropy) | 0.86     | 0.12      | 0.10   | 0.11     |
   | Decision Tree(Gini)    | 0.86     | 0.13      | 0.09   | 0.10     |
   | Random Forest(Entropy) | 0.91     | 0.23      | 0.00   | 0.00     |
   | Random Forest(Gini)    | 0.91     | 0.27      | 0.00   | 0.00     |

2. The reason is this data is imbalanced. When fitting a model, it tends to make the accuracy higher. As a result, it would predict more 0s than 1s, because we have many times of 0s in the dataset. Thus, I used SMOTE oversampling method to resample the data to a balanced one.

   In this part, I only resampled the training data and test it on the original dev data set. The accuracy would be lower because of resampling. I compared Decision Tree(Entropy) and Random forest(Entropy).

   The former one didn't improve, however from the latter one the recall was not 0% anymore.

   |                        | Accuracy | Precision | Recall | F1_score |
   | ---------------------- | -------- | --------- | ------ | -------- |
   | Decision Tree(Entropy) | 0.85     | 0.1       | 0.08   | 0.09     |
   | Random Forest(Entropy) | 0.91     | 0.17      | 0.01   | 0.02     |

3. Imbalanced learning is necessary, because we don't just want a high accuracy and let the result to be more 0s. In order to compare these methods, this time I did SMOTE oversampling first on the whole data set, and then splitted it into train and dev set. We now can see very good prediction results, and the performance of all models.

   |                        | Accuracy | Precision | Recall | F1_score |
   | ---------------------- | -------- | --------- | ------ | -------- |
   | Logistic Regrssion     | 0.61     | 0.63      | 0.57   | 0.60     |
   | Decision Tree(Entropy) | 0.91     | 0.93      | 0.90   | 0.91     |
   | Decision Tree(Gini)    | 0.91     | 0.93      | 0.90   | 0.91     |
   | Random Forest(Entropy) | 0.95     | 0.99      | 0.90   | 0.94     |
   | Random Forest(Gini)    | 0.95     | 0.99      | 0.90   | 0.95     |

   Despite the results, we can see the performance Randome Forest > Decision Tree > Logistic Regression. Random Forest gave the best results in these three learning method no matter entropy or gini was used.


This visualization shows the values of five different metrics in these five methods:

   ![compare](/Users/ljt/Documents/Madison/DataChat/readmission_prediction/compare.png)







  

  

  




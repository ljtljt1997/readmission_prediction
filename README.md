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

  **Decesion Tree (Using entropy and gini)**

  **Random Forest (Using entropy and gini)** 

- Imbalance learning - Deal with highly imbalanced data - Use SMOTE oversampling method here

  

  

  

  

  




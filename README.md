# Module 17 Credit_Risk_Analysis
### by Terra Lasho 
## Overview of the Analysis: For this project, I have been asked to use several machine learning models to evaluate and predict credit risk.  For this, I have been giving a training data set from LendingClub. Using Python language I will use Python to: 1) oversample the data using RandomOverSampler and SMOTE based algorithms; 2) undersample the data using ClusterCentroids algorithm; 3) combine over and under-sampling approaches using the SMOTEENN algorithm; 4) compare BalancedRandomForestClassifier and EasyEnsembleClassifier, machine learning models that reduce bias and compare credit risk.  Using the information derived above, I can then evaluate the performance of these models in order to recommend which can be used to predict credit risk. 
-----------------------------------------------------------------------------------------------------------------------------------
## Results
------------------------------------------------------------------------------------------------------------------------------------
## Deliverable 1: Use Resampling Models to Predict Credit Risk
-	For Deliverable 1, I am tasked with using two oversampling algorithms, RandomOverSampler and SMOTE, and one undersampling algorithm, ClusterCentroids to re-sample the training dataset.
### Part 1: Split the data into training and testing. 
-	I first converted string values into numerical ones using ‘get_dummies()’ method, and created the target variables.  We defined loan status ‘current’ as low risk, and the remaining as high risk:

![](https://github.com/Beetleee/Credit_Risk_Analysis/blob/main/Resources/Plot1.png)

-	Using the loan status as an indication of whether the application was low or high risk, I next used ‘x.describe()’ to check how may applications (out of an initial ~100,000 from our training set) were considered ‘low risk’. The reduced dataset was comprised of 68,817 applicants.

![](https://github.com/Beetleee/Credit_Risk_Analysis/blob/main/Resources/Plot2.png)

-	I then checked the balance of the target values by using .value_counts() and found that 99% of them, 68,470 were low risk.

![](https://github.com/Beetleee/Credit_Risk_Analysis/blob/main/Resources/Plot3.png)

### Part 2: Resample the training data using 3 algorithms: RandomOverSampler(oversampler), SMOTE(oversampler), and ClusterCentroids(undersample).  For this, I will:
-	Use the Logistic Regression classifier (to make predictions and evaluate performance)
-	 Calculate the accuracy score of the model
-	Generate a confusion matrix
-	Print the classification report
### RandomOverSampler (random selection from minor class and adds to training set until both classifications are equal; the results classified 51,366 records each as high/low; the balanced accuracy score was 66%; the ‘high risk’ precision rate [pr] was only 1% with recall 71% while ‘low risk’ pr was 100% with a  recall 60%):

![](https://github.com/Beetleee/Credit_Risk_Analysis/blob/main/Resources/Plot4.png)

![](https://github.com/Beetleee/Credit_Risk_Analysis/blob/main/Resources/Plot5.png)

### SMOTE (synthetic minority oversampling technique -which increases the size of the minor class by creating new values based on neighbor effect instead of random selection; the results show a slight improvement in the balanced accuracy score to 66%, the ‘high risk’ pr was only 1% with a recall of 63%, ‘low risk’ pr was 100% and improved recall of 69%):

![](https://github.com/Beetleee/Credit_Risk_Analysis/blob/main/Resources/Plot6.png)

![](https://github.com/Beetleee/Credit_Risk_Analysis/blob/main/Resources/Plot7.png)

### ClusterCentroids (identifies clusters of major class to generate data points that are representative of the clusters; the model identified 246 applications as high risk and low risk; the balanced accuracy score was lower than the oversampling models at 54%; the ‘high risk’ pr was only 1% with 69% recall, ‘low risk’ was 100% with lower recall of 40%):

![](https://github.com/Beetleee/Credit_Risk_Analysis/blob/main/Resources/Plot8.png)

![](https://github.com/Beetleee/Credit_Risk_Analysis/blob/main/Resources/Plot9.png)
-------------------------------------------------------------------------------------------------------------------------------
## Deliverable 2: Use the SMOTEENN algorithm to Predict Credit Risk
### Resample the training data using the SMOTEENN algorithm. For this, I will:
-	Use the Logistic Regression classifier (to make predictions and evaluate performance)
-	 Calculate the accuracy score of the model
-	Generate a confusion matrix
-	Print the classification report
### SMOTEENN (synthetic minority oversampling technique + edited nearest neighbors = combination of both under and over sampling); the model identified 68,460 applications as high risk and 62,011 as low risk; the balanced accuracy score improved over the other models at 64.5%; the ‘high risk’ pr was only 1% with 72% recall[slightly better than the other models], ‘low risk’ was 100% with recall of 57%):

![](https://github.com/Beetleee/Credit_Risk_Analysis/blob/main/Resources/Plot10.png)

![](https://github.com/Beetleee/Credit_Risk_Analysis/blob/main/Resources/Plot11.png)

---------------------------------------------------------------------------------------------------------------------------------
## Deliverable 3: Use Ensemble Classifiers to Predict Credit Risk
Compare two new Machine Learning models that reduce bias to predict credit risk (BalancedRandomForestClassifier and EasyEnsembleClassifier).  For this, I will resample the training dataset using both algorithms, and:
-	View the total counts
-	Train the ensemble classifier
-	Calculate the balanced accuracy score
-	Generate a confusion matrix
-	Generate a classification report

### BalancedRandomForestClassifier (two trees equal in both size and to the minor class are built to represent one for the major class and one for the minor class; the balanced accuracy score for this increased to 78.8% over the other models; the ‘high risk’ pr increased to 4% with recall of 67%, and ‘low risk’ pr was 100% with recall of 91%; the top feature importance was “total_rec_prncy” at 7.9% of the total.

![](https://github.com/Beetleee/Credit_Risk_Analysis/blob/main/Resources/Plot12.png)

![](https://github.com/Beetleee/Credit_Risk_Analysis/blob/main/Resources/Plot13.png)

![](https://github.com/Beetleee/Credit_Risk_Analysis/blob/main/Resources/Plot14.5.png)

### EasyEnsembleClassifier (model based on individual decisions being combined to classify new examples;  the balanced accuracy score for this increased to 93% over the other models; the ‘high risk’ pr is still low, but increased to 7% with recall of 91% giving this model the best score yet, and ‘low risk’ pr was 100% with 94% precision
![](https://github.com/Beetleee/Credit_Risk_Analysis/blob/main/Resources/Plot14.png)

![](https://github.com/Beetleee/Credit_Risk_Analysis/blob/main/Resources/Plot15.png)
-----------------------------------------------------------------------------------------------------------------------------------
## Deliverable 4: Analysis

### Although all of the models had poor precision with predicting high risk credit scores, after reviewing the performance of all of the models, I found the EasyEnsembleClassifier had the best precision (7%), accuracy (93%), recall (91%) rates of all in the prediction of “high risk” applicants. If the crediting company needs a model and can handle the error rates from the statistical data I was able to generate from the usage of these models, then this model would be the one I would choose.

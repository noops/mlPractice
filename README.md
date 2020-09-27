# mlPractice - assessing credit risk



# Table of Contents 
  - [Overview](#overview)
  - [Resources](#resources)
  - [Data](#data)
  - [Logistic Regression](#logistic-regression)
  - [Ensemble Classification](#ensemble-classification)


## Overview
Credit risk is a challenge for machine learning algorithms and classification techniques due to good loans heavily outweighing bad loans. Financial data taken from Lending Club, a peer to peer lending service company, is used to train and evaluate models containing unbalanced classes. These models are evaluated using a balanced accuracy score, a confusion matrix, and a classification report generated via the imblearn library. 

## Resources
- visual studio code
- python
- scikit library
- imblearn library

## Data
- LoanStats_2019Q1.csv 

## Logistic Regression
Regression is primarily used to predict outcomes involing continuous variables
1. Naive Random Oversampling
    
    Here instances of the minority class are randomly selected and added to the training set until the minority and majority classes are balanced.

    Balanced Accuracy Score: 64%

    Average Precision: 0.99

    Average Recall (Sensitivity): 0.62



2. SMOTE oversampling

    Synthetic Minority Oversampling Technique or SMOTE uses a random instance from the minority class of the dataset. From here it draws upon the closest neighbors of the randomly chosen instance. Based on the value of these neighbors synthetic new values are created. This technique is vulnerable to datasets with lots of outliers.

    Balanced Accuracy Score: 65.2%

    Average Precision: 0.99

    Average Recall (Sensitivity): 0.62

3. Cluster Centroids Undersampling
   
    The cluster centroids algorithm identifies clusters of the majority class of the dataset, generates synthetic data points called centroids that are representative of the identified clusters. The majority class is then undersampled down to the size of the minority class using the synthetic data points.

    Balanced Accuracy Score: 54.4%

    Average Precision: 0.99

    Average Recall (Sensitivity): 0.42

4. Combination (Over and Under) Sampling
   
    SMOTE combined with an edited nearest neighbors algorithm. The minority class is oversampled via SMOTE. This resulting oversampled data is cleaned with an undersampling strategy. If the two nearest neighbors of a data point belong to two different classes, that point is dropped. 

    Balanced Accuracy Score: 65.5%

    Average Precision: 0.99

    Average Recall (Sensitivity): 0.56
5. Conclusion

   In my opinion none of these models are good for classifying high risk or low risk creditors. Recall, the ability of a classifier to find all positive samples, is our most important predictor. None of the models had a better average recall than 62%. For this reason I do not recommend using any of these models to evaluate high risk or low risk creditors.  

## Ensemble Classification
ensemble classification is the process of combining multiple models to help improve accuracy and robustness, as well as decrease variance of the model to improve overall performance
1. Balanced Random Forest Classifier
   
    instead of a single complex decision tree, random forests sample the data and build several smaller, simpler decision trees. They are robust against overfitting, outliers and nonlinear data. They can also be used to rank importance of input variables in a natural way. 

    Balanced Accuracy Score: 78.9%

    Average Precision: 0.99

    Average Recall (Sensitivity): 0.87

2. Easy Ensemble Adaptive Boosting Classifier
   
    The model is trained and evaluated. After evaluating errors another model is trained with extra weight given to errors from the previous model. This process is repeated until the error rate is minimized. Balancing is achieved by random under sampling. 

    Balanced Accuracy Score: 93.2%

    Average Precision: 0.99

    Average Recall (Sensitivity): 0.94

3. Conclusion
   
   Both of the ensemble classifiers produced high values for balanced accuracy score, average precision, and average recall. Both models return a high F1 score, the weighted average of the true positive rate, for low risk creditors. This suggests that the ensemble classifiers are good at identifying low risk creditors. The low F1 score for high risk creditors suggests that the ensemble classifiers used are not good for identifying high risk creditors. The adaptive boosting classifier produced the best overall results for identifying low risk creditors. 



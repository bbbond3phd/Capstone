# Capstone Overview

In the capstone project our goal is to use all the knowledge gained through this course and create several machine learning modles (k-nearest neighbors, logistic regression, decision trees, and support vector machines) to predict the outcome of an event and then compare the performance of the classifiers to determine which model should be selected as the best performing model.

## Business Understanding: CRISP-DM Step 1
A tour and travels company is offering travel insurance to their customers. The company wants to know which customers would be interested in buying coverage based on its database history. 
The objective is to compare model performance against historical purchasers for predicting if future clients will purchase coverage.

## Data Understanding: CRISP-DM Step 2  
Dataset description: 
Insurance was offered to some of the customers in 2019. The provided data is an extracted of the performance and sales of insurance packages during the same period.
The data provided contains almost 2000 rows of its previous customers.

Dataset: the data consists of 1,986 rows. The data file can be found at https://www.kaggle.com/datasets/tejashvi14/travel-insurance-prediction-data

Features:
1. Age- age of the customer
2. Employment Type- the sector in which the customer is employed
3. GraduateOrNot- whether the customer is a college graduate or not
4. AnnualIncome- yearly income of the customer (in Indian Rupees, rounded to the nearest 50K Rupee)
5. FamilyMembers- number of members in the customer's family
6. ChronicDisease- whether the customer suffers from any health ailments e.g., Diabetes, high BP, asthama, etc) 
7. FrequentFlyer- derived data based on customer's history of booking air tickets (minimum of four different instances in two years (2017-2019))
8. EverTravelledAbroad- has the customer ever travelled internationally
9. TravelInsurance- (target) did the customer purchase a travel insurance package during the introductory offering period (2019)

## Data Preparation: CRISP-DM Step 3
### Data preparation after our initial exploration
1. No missing data was found in the dataset
2. No outliers or malformed data was found
3. Percentage of rows with TravelInsurance = 1: 35.73%
4. Pairplot indicated no outliers were present in the data

## Modeling: CRISP-DM Step 4
Six total models were built.
1. kNN
2. Logistic Regression
3. Decision Tree
4. Support Vector Machine
5. Decision Tree using GridSearchCV
6. Support Vector Machine using GridSearchCV
   
For each of these models several evaluation metrics were created:
1. Accuracy
2. Recall
3. F1-score
4. Time to run the model
5. Confusion matrix

## Evaluation: CRISP-DM Step 5
Based on comparing evaluation metrics, it was clear that SVM model was the clear winner. It performed nearly identically as the SVM_GridSearchCV without the long run time.
    kNN: 
        -Strong performance with an accuracy of: 0.7621440536013401
        -Middle time taken to run: 0.10 seconds
        -Correct predictions: 455 (76.2%)
        -F1-Score: 0.7168427230046948
        -Recall: 0.7259343075132549
    Decision Tree: 
        -Moderate performance with an accuracy of: 0.7554438860971524
        -Quickest time to run: 0.03 seconds
        -Correct predictions: 451 (75.5%)
        -F1-Score: 0.7324546325172506
        -Recall: 0.7314957453051643
    Logistic Regression: 
        -Strong performance with an accuracy of: 0.7638190954773869
        -Very quick time to run: 0.04 seconds
        -Correct predictions: 456 (76.4%)
        -F1-Score: 0.7135950243102457
        -Recall: 0.7014194542253521
    SVM: 
        -Best performance with an accuracy of: 0.8023450586264657
        -Slowest time to run: 0.25 seconds
        -Correct predictions: 479 (80.2%)
        -F1-Score: 0.7638639349977205
        -Recall: 0.7480927230046948
    Tuned Models:
    Logistic Regression using GridSearchCV:
        -Strong performance with an accuracy of: 0.7621440536013401
        -Very quick time to run: 60.85 seconds
        -Correct predictions: 455 (76.2%)
        -F1-Score: 0.7059398934398935
        -Recall: 0.6938453638497653
    SVM using GridSearchCV:
        -Strong performance with an accuracy of: 0.8023450586264657
        -Very quick time to run: 50.09 seconds
        -Correct predictions: 479 (80.2%)
        -F1-Score: 0.7638639349977205
        -Recall: 0.7480927230046948

### Conclusion
The analysis shows that SVM classifier provide the best performance for predicting conversion. With proper tuning and potential feature engineering, this models can be further improved to achieve better predictive accuracy. The output metrics provided clear insights making offers of travel insurance more efficient and actionable for the business.

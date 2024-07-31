# Capstone Overview

In the capstone project our goal is to use all the knowledge gained through this course and create several machine learning models (k-nearest neighbors, logistic regression, decision trees, and support vector machines) to predict the outcome of an event and then compare the performance of the classifiers to determine which model should be selected as the best performing model.
The intended audience for this analysis is the marketing team within the travel company. As such, the write up should not be technical in nature and clearly provide insight and findings within the data and provide actionable next steps.

## Business Understanding: CRISP-DM Step 1
The luxury travel industry is an aspirational purchase for many people. That is because travel can be expensive. Travel can also be fraught with uncertainty. Often international travel is purchased many months, sometimes years, before departing on the trip. In effort to reduce some uncertainty and financial stress associated with a travelers purchase, tour and travel companies offer travel insurance to their customers.
Not only does travel insurance provide peace of mind for the traveler, it also represents an increasing revenue stream for the travel company. Understanding the positive business impact of selling such a profitable product, travel companies increasingly are interested in buying coverage based on its database history.

Given that background information, the objective of this capstone project is to accurately predict a target audience of prospective travel insurance purchasers using a dataset of historical purchasers.

## Data Understanding: CRISP-DM Step 2  
Dataset description: 
The dataset used in this analysis is from 2019, which is prior to the COVID pandemic. Specifically, the data is an extract of the 'performance and sales of insurance packages' during the same period.
The data provided contains almost 2,000 rows transactional data from previous customers.

The file can be found at, https://www.kaggle.com/datasets/tejashvi14/travel-insurance-prediction-data

Features comprising the dataset:
1. Age (int)- age of the customer
2. Employment Type (int)- the sector in which the customer is employed
3. GraduateOrNot (obj)- whether the customer is a college graduate or not
4. AnnualIncome (obj)- yearly income of the customer (in Indian Rupees, rounded to the nearest 50K Rupee)
5. FamilyMembers (int)- number of members in the customer's family
6. ChronicDisease- (int) whether the customer suffers from any health ailments (e.g., Diabetes, high BP, asthma, etc) 
7. FrequentFlyer (obj)- derived data based on customer's history of booking air tickets (minimum of four different instances in two years (2017-2019))
8. EverTravelledAbroad (obj)- has the customer ever travelled internationally
9. TravelInsurance (int, target)- did the customer purchase a travel insurance package during the introductory offering period (2019)

## Data Preparation: CRISP-DM Step 3
After an initial exploration of the data it was found to be a highly curated dataset. As a rule of thumb, any dataset with less than a 40% target observation rate is considered to be imbalanced, this dataset qualifies as imbalanced.
1. No missing data was found in the dataset
2. No outliers or malformed data was found
3. Percentage of rows with TravelInsurance = 1: 35.73%
4. Pairplot indicated no outliers were present in the data

![alt text](https://github.com/bbbond3phd/Capstone/blob/main/pairplot.png)
(Note: portion of full plot)

## Modeling: CRISP-DM Step 4
in total six total models were built for this analysis. All of the models selected are classification models used to predict whether or not future travelers will purchase insurance.

1. k-Nearest Neighbors (kNN):
   Classification: kNN is primarily used for classification tasks where it assigns the class of a new sample based on the majority class of its k nearest neighbors in the training data.

2. Logistic Regression:
   Classification: Logistic regression is a linear model used for binary and multi-class classification problems. It predicts the probability of a sample belonging to a specific class.

3. Decision Tree:
   Classification: Decision trees can be used for both classification and regression. When used for classification, they split the data based on feature values to classify samples into distinct categories.

4. Support Vector Machine (SVM):
   Classification: SVMs are used for classification by finding the optimal hyperplane that separates classes in a high-dimensional space. SVMs can handle binary and multi-class classification.

5. Decision Tree using GridSearchCV:
   Classification: GridSearchCV is a tool for hyperparameter tuning. When used with a decision tree classifier, it optimizes the hyperparameters of the decision tree to improve its classification performance.

6. Support Vector Machine using GridSearchCV:
   Classification: Similarly, GridSearchCV can be used with SVMs to find the best hyperparameters for classification tasks, optimizing the performance of the SVM classifier.
   
For each of these models several evaluation metrics were created:
1. Accuracy
2. Recall
3. F1-score
4. Time to run the model
5. Confusion matrix
   
Due to the imbalanced nature of the dataset we will not be reviewing accuracy of the model because if can be misleading for imbalanced datasets because it may be high even if the model is only predicting the majority class correctly. F1-Score will be the primary measure used to evaluate model performance because it  balances the trade-off between precision (the proportion of positive identifications that are actually correct) and recall, providing a single metric that accounts for both false positives and false negatives, making is very useful for imbalanced data.

## Evaluation: CRISP-DM Step 5
Based on comparing evaluation metrics, it was clear that SVM model was the winner. The F1-Score and the recall were both the greatest of the standard models. Using GridSearchCV for the SVM model only increased the runtime by 200x without any increase in measures.

Standard models:
1. kNN:   
   a. Middle time taken to run: 0.10 seconds;   
   b. Correct predictions: 455 (76.2%);   
   c. F1-Score: 0.7168427230046948;   
   d. Recall: 0.7259343075132549;   
2. Decision Tree:    
   a. Quickest time to run: 0.03 seconds;   
   b. Correct predictions: 451 (75.5%);   
   c. F1-Score: 0.7324546325172506;   
   d. Recall: 0.7314957453051643;   
3. Logistic Regression:    
   a. Very quick time to run: 0.04 seconds;   
   b. Correct predictions: 456 (76.4%);   
   c. F1-Score: 0.7135950243102457;   
   d. Recall: 0.7014194542253521;   
4. SVM:    
   a. Slowest time to run: 0.25 seconds;   
   b. Correct predictions: 479 (80.2%);   
   c. F1-Score: 0.7638639349977205;   
   d. Recall: 0.7480927230046948;   

Tuned models:   
5. Logistic Regression using GridSearchCV:   
        a. Strong performance with an accuracy of: 0.7621440536013401;   
        b. Very quick time to run: 60.85 seconds;   
        c. Correct predictions: 455 (76.2%);   
        d. F1-Score: 0.7059398934398935;   
        e. Recall: 0.6938453638497653;   
6. SVM using GridSearchCV:   
        a. Strong performance with an accuracy of: 0.8023450586264657;   
        b. Very quick time to run: 50.09 seconds;   
        c. Correct predictions: 479 (80.2%);   
        d. F1-Score: 0.7638639349977205;   
        e. Recall: 0.7480927230046948;   

![alt text](https://github.com/bbbond3phd/Capstone/blob/main/Recall.png)

![alt text](https://github.com/bbbond3phd/Capstone/blob/main/F1.png)

## Conclusion
The analysis shows that SVM classifier provide the best performance for predicting conversion. With proper tuning and potential feature engineering, this models can be further improved to achieve better predictive accuracy. The output metrics provided clear insights making offers of travel insurance more efficient and actionable for the business.

## Summary for business audience (marketing professionals)
### Topic: Providing travel customers the opportunity to protect their purchase
As we know, travel is an expensive purchase. Like most large purchases, having the ability to cover a potential loss is important for most buyers. To that end, Acme Travel offers insurance coverage for upcoming travel purchase with the company. Not only is insurance an important product for the customer, it is also a large contributor to Acme Travel’s revenue stream. To that end, Acme Travel has undertaken an effort to increase conversion of this product. Below is a list of frequently asked questions about the business’s approach towards identifying customers likely to purchase insurance.
 
FAQ:

**Why is insurance important?**   
   Purchased insurance offers a peace of mind surrounding the uncertainty associated with large purchase made many months in advance.

**Who should buy insurance?**   
   All customers purchasing a trip with Acme Travel should purchase insurance, but not all will chose to cover their expensive trip.

**How can Marketing identify likely customers?**   
   Acme Travel Data Science team built several machine learning models using historical transaction data to accurately predict customers that purchased data. The model that most correctly predicted customers having made an insurance purchase will be used in the future to generate an indicator for the Marketing team to use in effort to get more customers to purchase travel insurance.

**How will Marketing be informed about likely customers?**   
   Working with the IT team, the Data Science team has developed a real-time solution for bookings made through the customer relation management tool (CRM) that will show a key performance indicator (KPI) at the time of booking. The Data Science team will also provide a batch file to be used for targeting for those bookings made the previous day that did not purchase insurance at time of booking.

**How should Marketing use this data?**   
   Marketing can develop any number of strategies using this data. For example, within CRM, Marketing can develop sales scripts for the call agents to use while they are speaking to a customer at time of booking. Additionally, the predictions can be feed to the web team for use of offering during a booking made on-line. Lastly, the batch file can be used any number of ways; onboarding and segment targeting digitally, follow up email to customers, outbound calls from the sales team, etc.

**Can Marketing trust the data?**   
   Yes. The Data Science team trained the model using historical production transactional data. Meaning, the models use Acme Travel’s own data to predict likelihood based on our own customer’s purchase behavior.

**How long will the data be accurate?**   
   The Data Science team will monitor the production data of insurance purchases. If the team observes conversion dropping, the team will retrain the model to increase accuracy.

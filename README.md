# Comparing_Classifiers
Created for Practical assignment 3

### Executive summary
**Project overview and goals:** Goal of this project is to compare the performance of four classifiers , namely K Nearest Neighbor, Logistic Regression, Decision Trees, and Support Vector Machines. We will utilize a dataset related to marketing bank products over the telephone.

**Getting Started**
Our dataset comes from the UCI Machine Learning repository link. The data is from a Portugese banking institution and is a collection of the results of multiple marketing campaigns. We will make use of the article accompanying the dataset here for more information on the data and features.

**Business Problem**
The increasingly vast number of marketing campaigns over time has reduced its effect on the general public. Businesses now invest on directed campaigns with a strict and rigorous selection of contacts. Also, pressure for a reduction in cost and time requires a need for an improvement in efficiency: lesser contacts should be done, but an approximately number of successes (clients subscribing the deposit) should be kept. k The business goal is to find a model that can explain success of a contact, i.e if the client subscribes the deposit. Such model can increase campaign efficiency by identifying the main characteristics that affect success, helping in a better management of the available resources (e.g. human effort, phone calls, time) and selection of a high quality and affordable set of potential buying customers.estomers.

**Data Overview**
The data is related with direct marketing campaigns of a Portuguese banking institution. 17 Marketing campaigns were conducted. The marketing campaigns were based on phone calls. Often, more than one contact to the same client was required, in order to access if the product (bank term deposit) would be ('yes') or not ('no') subscribed.

During these phone campaigns, an attractive long-term deposit application, with good interest rates, was offered. For each contact, a large number of attributes was and if there was a success (the target variable). For the whole database considered, there were 6499 successes (8% success rate).

**Details of each feature is availabe in Jupyter file**

**measure of success**
Based on business requirement and imbalance of data ( in terms of number of 'yes' and 'no') I considered **ROC-AUC** as best measure when comparing the classifiers. 

**Exploratory data analysis:**
There are no null values in this data, but lot of unknowns in 'Poutcome' feature which tells if customer was previously contacted. Since there were significant number of people were contacted for the first time it made sense to plit the data into "First time customers" and "existing cutomers" as different features will have different impact in both scenarios.

**Preprocessing:**
- Data was split into "First time customers" ('Poutcome' = 'unknown') and "existing cutomers"(('Poutcome' != 'unknown')) . 
- For new customers 'Pdays' and 'Poutcome' was dropped .
- 'duration' feature was dropped for both the datasets.
- Categorical features were encoded. and data was split into train and test sets.
- New customer data set was too large for SVM there fore 10% data file was used for it.


**Analysis**
- For both the data sets best parameters  for K Nearest Neighbor, Logistic Regression, Decision Trees, and Support Vector Machines were identified. anmd then best parameters of all four models were compared against each other using ROC-AUC score. 
Existing customers Best parameters
-     KNN - Best k: 30
-     Logistic Regression - {'C': 0.01, 'penalty': 'l2', 'solver': 'lbfgs'}
-     Decision tree - {'criterion': 'entropy', 'max_depth': 5, 'min_samples_leaf': 10, 'min_samples_split': 2}
-     SVM - {'C': 1, 'gamma': 'auto', 'kernel': 'rbf'}
  Model Performance Summary:
                 Model   ROC AUC  
0                  KNN  0.821393  
1  Logistic Regression  0.817052  
2        Decision Tree  0.819775  
3                  SVM  0.799589

New customers Best parameters
-     KNN - Best k: 30
-     Logistic Regression - {'C': 0.01, 'penalty': 'l2', 'solver': 'lbfgs'}
-     Decision tree - {'criterion': 'gini', 'max_depth': 10, 'min_samples_leaf': 10, 'min_samples_split': 2}
-     SVM(smaller Data set) - {'C': 10, 'gamma': 'auto', 'kernel': 'rbf'}
Model Performance Summary:
                   Model   ROC AUC 
0                    KNN  0.678261  
1    Logistic Regression  0.676134  
2          Decision Tree  0.720967  
3  SVM (Smaller Dataset)  0.560122


#### Conclusion
Two seperate models where build . One for new customers amd other for Existing customers.

For new customers decision Tree seem to be performing the best with ROC-AUC of .72 . best parameters for Decision Tree (New Customers) - Best Parameters: {'criterion': 'gini', 'max_depth': 10, 'min_samples_leaf': 10, 'min_samples_split': 2} Top features - Month, Age, day, balance.

For existing Customers KNN, Decision Tree and Logistic Regression had almos same ROC-AUC of .82. But since we are using Decision tree for New csutomers we can recomend the same for existing customers. Best parameters for Decision Tree - Best Parameters: {'criterion': 'entropy', 'max_depth': 5, 'min_samples_leaf': 10, 'min_samples_split': 2} Top features - Poutcome, Housing, pdays

For new customers which month customer is contacted is most influencial factor.

For existing customer what was the outcome of previous contact is most influencial factor.

  

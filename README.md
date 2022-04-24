# Attrition Prevention Project - Team 11


## Dataset:
‘IBM HR Analytics Employee Attrition & Performance’ by Pavan Subhash on Kaggle.  

Link: https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset  

Problem Statement:  

Identify factors that affect Attrition, predict optimal conditions to make people stay, and devise recommendations.  
  
   
## Notebooks : <br>

1. **DataClean_EDA.ipynb** : cleaning the dataset and exploratory data analysis  

2. **Idealised_Data_Sets_.ipynb** : Creates recommended DataSets to run through Model  

3. **Model_up.ipynb** : Exploring Different Models and running ideal datasets  



## Data Preparation:

1. **Cleaning the data**  
  a. Drop irrelevant columns  
    b. Check to filter out unsuitable rows  
      c. Modify names to standard format  
  
2. **Feature Engineering**  
  a.JobSwitchRate  
    b.RelIncAtLev

## EDA Overview:  

1. Attrition Value Imbalance
2. Bi-Variate Exploration : HeatMap
3. Attrition and Categorical Values
4. Attrition and Numerical Values
5. JobSatisfaction and Attrition
6. MonthlyIncome
7. Age and Gender Statistics

## Mini EDA questions
1. Employee Stagnation
2. Exploring Job Environment
3. Evaluation in a Work Space
4. Potential New Hiring


## Preparing Data for Model:
1. dropping columns with low correlation
2. fix null values across variables
3. encode categorical variables
4. fit the data to the model and tune hyperparameters.  

## Models Used:
1. The **Decision Tree Classifier** from sklearn which splits dataset along features to predict the class.
2. **BalancedBaggingTreeClassifier**, which fits a base estimator on subsets of original data and aggregates predictions.
3. **XGBoost Classifier**: An ensemble method which combines many weaker tree-based models and optimizes an arbitrary loss function to make better predictions.

## Recommendation:
We pick 3 features — OverTime, BusinessTravel and RelIncAtLevel based on 2 criteria .  

(1) Importance of features in determining Attrition (found with XGBoost) and (2) Whether they can be changed by the employer, IBM.

## Verification Procedure:
1. Hypothesise a change in values for the three features
2. Make this change for Attrition==’Yes’ employees. That is, OverTime, BusinessTravel and RelIncAtLevel are altered but attrition value is left as it is.
3. Changed Values form a new dataset.
4. Pass whole of changed dataset (w/o Attrition) as ‘test’ through model

    **Assumption: the model is the closest possible predictor of attrition**  
 
5. Plot confusion matrix. Here, actual values are the original attrition values, whereas prediction represents what Attrition is now — with the recommended changes. 
6. False Negative value in the confusion matrix (1,0) is the number of employees ‘saved’ from leaving with the recommended changes

## Recommendations Tested:
1. Average/Mode values for people with Attrition No
2. Average RelIncAtLev for Attrition No, but OverTime and BusinessTravel left unaltered (these may be unnegotiable in some cases)
3. Increasing MonthlyIncome of Attrition Yes employees by 5%, thus calculating new RelIncAtLev
4. Increasing MonthlyIncome of Attrition Yes employees by 10%, thus calculating new RelIncAtLev

## Results - Key Recommendation from Model

A 5% income increase is most preferable for employer. 

The ideal value is average income of Attrition No employees at that level. 

Reduce OverTime and BusinessTravel or Hire more employees for even work distribution.

**Result - Data Insight — At Risk Employees**

Those with High Performance and Low Satisfaction
Mid-level Employees
Younger Employees 
Those in Overworked Job Roles


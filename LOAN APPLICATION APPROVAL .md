LOAN APPLICATION STATUS PREDICTION USING MACHINE LEARNING

In This dataset includes details of applicants who have applied for loan. The dataset includes details like credit history, loan amount, their income, dependents etc.
so, on this parameter base we have to predict the status of our applicant loan application.

Independent Variables:

- Loan_ID

- Gender

- Married

- Dependents

- Education

- Self_Employed

- ApplicantIncome

- CoapplicantIncome

- Loan_Amount

- Loan_Amount_Term

- Credit History

- Property_Area

Dependent Variable (Target Variable):

- Loan_Status

STEP 1:-
WE HAVE TO READ THE DATASET FILE WHICH IS IN .CSV 

![READING FILE](https://user-images.githubusercontent.com/79801052/115113279-2e4bb380-9fa7-11eb-8760-fc57d54765bd.jpg)



THE CHECKING THE DATASET I HAVE FOUND THAT IT HAS 614 ROWS AND 13 COLUMNS



After that i have  found that 

![null and dtypes](https://user-images.githubusercontent.com/79801052/115113361-88e50f80-9fa7-11eb-931d-77c359475a34.jpg)



and now filling the null values by this method 


![fiilna](https://user-images.githubusercontent.com/79801052/115113419-dd888a80-9fa7-11eb-924a-f7b2d0e8d007.jpg)



after that checking the correlation matrix by using the heatmap


![corr](https://user-images.githubusercontent.com/79801052/115113492-4e2fa700-9fa8-11eb-88c7-68d00dfd8b12.jpg)


in this heatmap i have found that there are some correlated variable i.e ApplicantIncome-LoanAmount and Credit_History-Loan_Status


and by checking the distplot and subplot of individual column
i have found that most of the plot left skewd and to make them right skewd i have use log transformation on each column individually



after this i have also convert categorical columns into numeric which are 👎


Gender,married, education,self_employed ,property_area

by using this 


![cat](https://user-images.githubusercontent.com/79801052/115113687-2ab92c00-9fa9-11eb-91bb-129161a279a8.jpg)




#dropping column which have no use
df1=df1.drop(['Loan_ID','ApplicantIncome','CoapplicantIncome',
'Coapplicant_log','LoanAmount','TotalIncome','TotalIncome_log','EMI','EMI_log','Balance_Income','Balance_Income_log'],axis=1)



now seprating the data for feature and label into x and y using this 


x=df1.drop(['Loan_Status'],axis=1)
y=df1['Loan_Status']






 FINDING THE BEST RANDOM STATE AND DIVIDE THE DATA IN TO  70:30 RATIO FOR TEST AND TRAIN

BY USING THE RANGE FUNCTION I HAVE FOUND THAT MY RANDOM STATE IS Max Accuracy SCORE is 0.8756756756756757 on Random State 389


AND NOW APPLYINNG THE DIFFRENT MACHINE LEARNING MODLES


1.LOGISTIC REGRESSION

THESE ARE MY SCORES 


LogisticRegression()
0.8756756756756757

              precision    recall  f1-score   support

           0       0.96      0.55      0.70        49
           1       0.86      0.99      0.92       136

    accuracy                           0.88       185
  
  
  
  
  
  
 2.DecisionTreeClassifier()
0.772972972972973

              precision    recall  f1-score   support

           0       0.56      0.69      0.62        49
           1       0.88      0.80      0.84       136

    accuracy                           0.77       185





3.RandomForestClassifier()
0.8540540540540541

              precision    recall  f1-score   support

           0       0.78      0.63      0.70        49
           1       0.88      0.93      0.90       136

    accuracy                           0.85       185
    
    
    
    
    
   
   
   
   AFTER THAT CROSS VALIDATION SCORES ARE ALSO COMES AFTER CV=5
    
   
Cross Validation Score for  LogisticRegression()  model is : 0.8061975209916034
 
Cross Validation Score for  GaussianNB()  model is : 0.8013194722111155
 
Cross Validation Score for  DecisionTreeClassifier()  model is : 0.7133679861388778
 
Cross Validation Score for  RandomForestClassifier()  model is : 0.79156337465014
   
   
   
   
   
IN THIS RANDOM FOREST CLASSIFIER IS HAVING THE HIGHEST SCORE WHICH IS 85.45

SO I HAVE ALSO TESTED FOR HYPERPARAMETER TUNNIG USING GRIDSEARCH CV

ON GETTING THE BEST PARAMETERS 


I HAVE GOT THESE 


RandomForestClassifier(random_state=389,max_features='auto',n_estimators=200,max_depth=4,criterion='gini')
0.8756756756756757

              precision    recall  f1-score   support

           0       0.96      0.55      0.70        49
           1       0.86      0.99      0.92       136

    accuracy                           0.88       185
  
  
  
  
 SO THE FINAL SCORE OF ACCURACY IS 87.56
 
 
 
 
 GITHUB LINK OF FULL IPYNB IS :--
 
 https://github.com/vinayak2910/Loan-application-status

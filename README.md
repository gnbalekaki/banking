# README: Practical Application Assignment 17.1: Comparing Classifiers
## Understanding the problem:
The Bank Marketing project involves data from direct marketing campaigns conducted by a Portuguese banking institution. These campaigns were primarily based on phone calls, and often required multiple contacts with the same client. The goal was to determine whether the client would subscribe to a bank term deposit, with the outcome being either 'yes' (subscribed) or 'no' (not subscribed).`

`To frame the task, throughout this practical application, we will apply CRISP-DM techniques as outlined in this report. We will begin by understanding the problem, followed by exploring the data through visualization plots. Next, we will preprocess the data, model it, evaluate the models, and conclude with key findings.

 ### Link to Jupyter notebook: 
 Refer to the link below: **https://github.com/gnbalekaki/banking**

## Understanding Model Features
We categorize and provide a description of each variable in the data under consideration.
### Input variables:
#### bank client data:
1. age (numeric)
2. job : type of job (categorical: 'admin.','blue-collar','entrepreneur','housemaid','management','retired','self-employed','services','student','technician','unemployed','unknown')
3. marital : marital status (categorical: 'divorced','married','single','unknown'; note: 'divorced' means divorced or widowed)
4. education (categorical: 'basic.4y','basic.6y','basic.9y','high.school','illiterate','professional.course','university.degree','unknown')
5. default: has credit in default? (categorical: 'no','yes','unknown')
6. housing: has housing loan? (categorical: 'no','yes','unknown')
7. loan: has personal loan? (categorical: 'no','yes','unknown') 
#### related with the last contact of the current campaign:
8. contact: contact communication type (categorical: 'cellular','telephone')
9. month: last contact month of year (categorical: 'jan', 'feb', 'mar', ..., 'nov', 'dec')
10. day_of_week: last contact day of the week (categorical: 'mon','tue','wed','thu','fri')
11. duration: last contact duration, in seconds (numeric). Important note: this attribute highly affects the output target (e.g., if duration=0 then y='no'). Yet, the duration is not known before a call is performed. Also, after the end of the call y is obviously known. Thus, this input should only be included for benchmark purposes and should be discarded if the intention is to have a realistic predictive model.
#### other attributes:
12. campaign: number of contacts performed during this campaign and for this client (numeric, includes last contact)
13. pdays: number of days that passed by after the client was last contacted from a previous campaign (numeric; 999 means client was not previously contacted)
14. previous: number of contacts performed before this campaign and for this client (numeric)
15. poutcome: outcome of the previous marketing campaign (categorical: 'failure','nonexistent','success')
#### social and economic context attributes
16. emp.var.rate: employment variation rate - quarterly indicator (numeric)
17. cons.price.idx: consumer price index - monthly indicator (numeric)
18. cons.conf.idx: consumer confidence index - monthly indicator (numeric)
19. euribor3m: euribor 3 month rate - daily indicator (numeric)
20. nr.employed: number of employees - quarterly indicator (numeric)
#### Output variable (desired target):
21. y - has the client subscribed a term deposit? (binary: 'yes','no')

## Data visualization:
During data exploration, we observed an imbalanced class, as computed and plotted using a bar plot (refer to the notebook)
* no-class: 88.30%
* yes-class: 11.70%

## Data modeling:
*We modeled the data using four different classifiers as shown below, all applied to the same dataset (split_train_test):

- models = {
        'Logistic Regression': LogisticRegression(),
        'Decision Tree': DecisionTreeClassifier(random_state=42),
        'K-Nearest Neighbors': KNeighborsClassifier(),
        'Support Vector Machine': SVC()
    }

## Model evaluation
Here, we measure the mean scores and fit times of four different classifiers, as shown below
- Logistic Regression:
  - Train Score: 89.15%
  - Test Score: 89.14%
  - Average Fit Time: 0.4392 seconds

- Decision Tree:
  - Train Score: 100.00%
  - Test Score: 87.27%
  - Average Fit Time: 0.3425 seconds

- K-Nearest Neighbors:
  - Train Score: 91.06%
  - Test Score: 88.17%
  - Average Fit Time: 0.0227 seconds

- Support Vector Machine:
  - Train Score: 88.41%
  - Test Score: 88.42%
  - Average Fit Time: 29.2099 seconds
    
Furthermore, we provide a classification report, including precision, recall, and F1 scores for each classifier, as in the notebook:
- Logistic Regression Final
  - Accuracy: 88.85%
  - prescision: 60.51%
  - recal: 21.91%
- Decision Tree 
  - Accuracy: 87.05%
  - prescision: 46.48%
  - recal: 48.40%
- K-Nearest Neighbors 
  - Accuracy: 87.55%
  - prescision: 47.26%
  - recal: 27.68%
- Support Vector Machine 
  - Accuracy: 87.95%
  - prescision: 53.85%
  - recal: 0.64%

 ## Findings for all classifiers:
- * Logistic Regression shows excellent generalization with a nearly identical train score (89.15%) and test score (89.14%), indicating that it performs well on both training and unseen data. The average fit time of 0.4392 seconds suggests it is relatively fast to train.

- * Decision Tree achieves a perfect train score (100%), but there is a significant drop in test score (87.27%), indicating overfitting. The model performs well on training data but struggles to generalize on unseen data. It has the fastest average fit time at 0.3425 seconds, making it efficient despite its overfitting issue.

- * K-Nearest Neighbors has a train score of 91.06% and a test score of 88.17%, showing a reasonable balance between training and testing performance. Its average fit time of 0.0227 seconds is notably fast, which is advantageous for larger datasets.

- * Support Vector Machine performs well with a train score of 88.41% and a test score of 88.42%, indicating good generalization and performance on unseen data. However, it has a significantly longer average fit time (29.2099 seconds), which may be a drawback for larger datasets.
 ## Conclusion: 
- From our analysis, the models shows that Logistic Regression achieved the highest accuracy at 88.85%, outperforming the other models. The Support Vector Machine came close with an accuracy of 87.95%, followed by K-Nearest Neighbors at 87.55%, and Decision Tree with the lowest accuracy of 87.05%. 

Overall, Logistic Regression and Support Vector Machine provide the best generalization with similar test scores, which also contributes to the highest F1 scores (94%) exhibited by both models. However, Logistic Regression is faster. Decision Tree suffers from overfitting, while K-Nearest Neighbors strikes a balance between accuracy and training speed.
## Contribution
>>by GN Balekaki<<



 
 

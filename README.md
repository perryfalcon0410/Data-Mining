# Data-Mining
Full report can be seen in the pdf file

## Motivation
### Neural Network Architecture Optimization

Hyper parameters tuning for neural network is challenging, especially in determine the architecture (number of layers, number of nodes for each layers)

## Dataset

The data is related to the direct marketing campaigns of a Portuguese banking institution. 

Target: Predict whether a customer will subscribe to the bank’s campaign (‘yes’) or not (‘no’).

The data folder contains two datasets:-

train.csv: 45,211 rows and 18 columns ordered by date (from May 2008 to November 2010)

test.csv: 4521 rows and 18 columns with 10% of the examples (4521), randomly selected from train.csv

1. age (numeric)
2. job : type of job
(categorical: "admin.","unknown","unemployed","management","housemaid","entrepreneur","student", "blue-collar","self-employed","retired","technician","services")
3. marital : marital status 
(categorical: "married","divorced","single";
note: "divorced" means divorced or widowed)
4. education
(categorical: "unknown","secondary","primary","tertiary")
5. default: has credit in default?
(binary: "yes","no")

6. balance: average yearly balance, in euros (numeric)
7. housing: has housing loan? (binary: "yes","no")
8. loan: has personal loan? (binary: "yes","no")

9. contact: contact communication type
(categorical: "unknown","telephone","cellular")
10. day: last contact day of the month (numeric)
11. month: last contact month of year (categorical: "jan", "feb", "mar", …, "nov", "dec")
12. duration: last contact duration, in seconds (numeric)
13. campaign: number of contacts performed during this campaign and for this client (numeric, includes last contact)
14. pdays: number of days that passed by after the client was last contacted from a previous campaign
(numeric, -1 means client was not previously contacted)
15. previous: number of contacts performed before this campaign and for this client (numeric)
16. poutcome: outcome of the previous marketing campaign
(categorical: "unknown","other","failure","success")

Output variable (desired target):

17. y - has the client subscribed a term deposit? (binary: "yes","no")

train.csv

![image](https://user-images.githubusercontent.com/93825495/228465290-7ac282ae-e574-4300-9f6b-d13b709333da.png)

## EDA
Note: The code is in Banking Data Mining.ipynb
### Convert Numerical to Categorical data
#### Age
![image](https://user-images.githubusercontent.com/93825495/228469213-bbab321a-fd10-4410-8a68-d8d737030889.png)

#### Customer's balance
![image](https://user-images.githubusercontent.com/93825495/228469354-06ece4a1-5ab0-4fba-80c5-f299b849cc3b.png)

#### contacts performed
![image](https://user-images.githubusercontent.com/93825495/228469827-11da580f-1269-40c4-9f38-10c0aca09c02.png)

#### pdays 
![image](https://user-images.githubusercontent.com/93825495/228470035-815db72b-bbd8-4b2f-aa33-0a8b199bc7a1.png)

#### Contacts performed before the campaign
![image](https://user-images.githubusercontent.com/93825495/228470097-589dae73-5631-47cd-9d25-416fc82e6682.png)

### Treating Missing data
![image](https://user-images.githubusercontent.com/93825495/228466177-804b35a7-9d34-4301-aea4-7c83b58eeb1d.png)

#### Job
The job will be matched with the education mode and the unknowns will be dropped.

If job is unknown and education is primary, we will assign with blue collar


If job is unknown and education is secondary, we will random the job


If job is unknown and education is tertiary, we will assign with management


#### Education
![image](https://user-images.githubusercontent.com/93825495/228467127-16ef34ce-4cb5-4208-a14b-732f6936520e.png)

If job is in this list ['blue-collar', 'technician', 'admin.' ,'student', 'education', 'retired', 'services' ,'unemployed'] we assign secondary.

If job is in this list ['management','entrepreneur','self-employed'] we will assign tertiary

Housemaid job will be assign with primary education

#### Contact
![image](https://user-images.githubusercontent.com/93825495/228467791-c050cf65-201a-4bcc-a772-d5fc6d354393.png)

We will assign unknown value with cellular since the number of cellular is much higher

#### poutcome
![image](https://user-images.githubusercontent.com/93825495/228468032-f2f2b4f5-6142-423f-8706-511aa6b40f3c.png)

Since most of the poutcome is 'unknown' any attempt to replace them will bring a lot of BIAS so we'll discard the column

### "y" column
![image](https://user-images.githubusercontent.com/93825495/228470365-c27093ea-6db4-4a0f-9ed8-334d7bfddc4e.png)

## Propose Solution
![image](https://user-images.githubusercontent.com/93825495/228472813-58204eab-5588-4cf2-9350-ea13b4ac84ab.png)

Note: Logistic Regression, SVM, Random Forest source code is found in banking data mining.ipynb. NN architecture can be found in neural-network-optimization-with-tabu-search.ipynb

## Evaluation

|               | Precision | F1 | Accuracy | Recall | 
| ------------- | ------------- | ------------- | ------------- | ------------- |
| Best NN Architecture  | 0.922  | 0.711  | 0.682 | 0.807 |
| Logistic Regression  | 0.838  | 0.534| 0.399  | 0.805  |
| SVM  | 0.829 | 0.527  | 0.386 | 0.83 |
| Random Forest  | 0.997  | 0.986 | 0.998 | 0.975 |

## Conclusion

For this dataset, after some preprocessing, the number of features is still really small for a neural network solution

→ Therefore, Random Forest out-perform Neural Network.

In fact, Random Forest is more commonly used in these kind of problems because its light-weight and can perform exceptionally.

However, Tabu Search for Neural Network Architecture Optimization have a big advantage in terms of scalability
⇒ If the problems are more complex, the number of features is huge ⇒ This method could potentially perform well.







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

### Convert Numerical to Categorical data
#### Age
![image](https://user-images.githubusercontent.com/93825495/228464782-543c2bec-34e9-4f7f-bed0-74cecf2dbaf7.png)

#### Customer's balance
![image](https://user-images.githubusercontent.com/93825495/228464970-17bc7342-6701-4f5c-9fab-090c1339f241.png)

#### contacts performed
![image](https://user-images.githubusercontent.com/93825495/228465057-0c757404-3f15-4f69-972a-cd5eb5ac3e80.png)

#### pdays 
![image](https://user-images.githubusercontent.com/93825495/228465565-1e45af76-f8bc-41ec-b3c3-acea14858e64.png)

#### Contacts performed before the campaign
![image](https://user-images.githubusercontent.com/93825495/228465712-84251533-3b16-4ba7-9fc6-8c5e9f24373e.png)

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
![image](https://user-images.githubusercontent.com/93825495/228468159-55364845-79dd-4213-aeb3-0960aef3d9c7.png)








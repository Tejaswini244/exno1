# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
```
import pandas as pd
exp=pd.read_csv("/content/SAMPLEIDS.csv")
exp.head()
```
![Screenshot 2025-03-07 151300](https://github.com/user-attachments/assets/d5fc6da8-36be-4a53-828c-6842ec3a1c00)
```
exp.head(5)
```
![Screenshot 2025-03-07 151814](https://github.com/user-attachments/assets/da3d30e3-bbc7-477d-a5f6-277f731b6566)
```
exp.tail(5)
```
![Screenshot 2025-03-07 152118](https://github.com/user-attachments/assets/7974d0ad-cc3a-43ae-83fb-9541ffec630a)
```
exp.isnull().sum()
```
![Screenshot 2025-03-07 152302](https://github.com/user-attachments/assets/4dd632a1-25bb-4ef1-ba9b-3be4734cbf3f)
```
exp.isnull().any()
```
![Screenshot 2025-03-07 152442](https://github.com/user-attachments/assets/617a9240-c3e3-4508-b59d-d9940ffdd318)
```
exp.dropna(axis=1)
```
![Screenshot 2025-03-07 152610](https://github.com/user-attachments/assets/edfba808-7871-4172-8102-60c799ed844d)
```
exp.fillna(50)
```   
![Screenshot 2025-03-07 152720](https://github.com/user-attachments/assets/6627c97b-29ef-410b-9425-a58b94018803)
```
exp.fillna(method='ffill')
```
![Screenshot 2025-03-07 153026](https://github.com/user-attachments/assets/80252f3d-5bdb-4f4e-a7ca-85b25d93aecf)

![Screenshot 2025-03-07 153047](https://github.com/user-attachments/assets/79b81ebe-26e0-4109-9a2d-84225e89d1a7)
```
exp.fillna(method='bfill')
```
![Screenshot 2025-03-07 153313](https://github.com/user-attachments/assets/7f9f90b6-70ff-4b44-ae45-43f2b7964107)
![Screenshot 2025-03-07 153331](https://github.com/user-attachments/assets/ea5e41ff-4877-4f79-b1a7-4fc9aa4d9146)
```
lab.fillna({'GENDER':'MALE','NAME':'PRAKASH','ADDRESS':'POONAMALEE','M1':'50','M2':'89','M3':'75','M4':'82','TOTAL':'896','AVG':'89.00000'})
```
![Screenshot 2025-03-07 153704](https://github.com/user-attachments/assets/38321599-a790-4b3b-9cbd-8fdaec9b9aba)

![Screenshot 2025-03-07 153730](https://github.com/user-attachments/assets/f0d7befc-c22f-4156-ba31-1119dfd3b329)
```
lab=pd.read_csv("/content/iris.csv")
lab
```
![Screenshot 2025-03-07 154021](https://github.com/user-attachments/assets/34cde2a4-deda-491d-8a15-50af4c5467c8)
```
lab.describe()
```
![Screenshot 2025-03-07 154123](https://github.com/user-attachments/assets/741980e1-9317-4c71-adc1-5128ee329d13)
```
import seaborn as sns
sns.boxplot(x='sepal_width',data=lab)
```
![Screenshot 2025-03-07 154235](https://github.com/user-attachments/assets/5954671a-39b5-434b-9cb0-bd8830772a2b)
```
q1=lab.sepal_width.quantile(0.25)
q3=lab.sepal_width.quantile(0.75)
iq=q3-q1
print(iq)
```
![Screenshot 2025-03-07 154325](https://github.com/user-attachments/assets/09c3f1ed-c98c-4bc8-8f69-5720a1e7dcca)
```
rid=lab[((lab.sepal_width<(q1-1.5*iq))|(lab.sepal_width>(q3+1.5*iq)))]
rid['sepal_width']
```
![Screenshot 2025-03-07 154417](https://github.com/user-attachments/assets/4b11a89b-7114-4e7a-9987-fcaff21eea89)
```
depo=lab[~((lab.sepal_width<(q1-1.5*iq))|(lab.sepal_width>(q3+1.5*iq)))]
depo
```
![Screenshot 2025-03-07 154536](https://github.com/user-attachments/assets/4817ffda-1838-49f3-a20b-e32a57afc858)
```
sns.boxplot(x='sepal_width',data=depo)
```
![Screenshot 2025-03-07 154536](https://github.com/user-attachments/assets/c2b10743-cffa-4b2b-a93a-b62152d63017)
```
import numpy as np
import scipy.stats as stats
z = np.abs(stats.zscore(lab.sepal_width))
z
```
![Screenshot 2025-03-07 154536](https://github.com/user-attachments/assets/a4d5e64b-12c9-47c3-94e2-f03e74300c76)
```
p=lab[z<2]
p
```
![Screenshot 2025-03-07 154536](https://github.com/user-attachments/assets/7d7308da-9724-45e0-87d4-b38f3aa8f3c9)

# Result
         Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.


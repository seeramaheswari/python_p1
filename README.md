# python_p1
## Analysing_Data_Using_Python
**Importing required libraries**
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```
**Reading csv file assigning it to *df1* variable**
>df1 = pd.read_csv(r"C:\Users\mahes\Desktop\python_projects\Salaries.csv.zip",low_memory=False)

**Lets see the values of the dataset**
>df1.head()

**Lets see the first 10 values**
>df1.head(10)

**Lets check last 10 rows in the dataset**
>df1.tail(10)

**Find the shape of our dataset(no of rows & no of columns)**
>df1.shape

**printing them in order**
```
print("Numbers of rows:",df1.shape[0])
print("Numbers of columns:",df1.shape[1])
```
**Describing our dataset**
>df1.describe()

**Getting information about our dataset like total no of rows ,columns,data type of each column  and memory requirement
using *info method***
>df1.info()
**Checking all the null values in the dataset using isnull**
>df1.isnull()
#### Lets check how many ***null values*** are there in each column using ***isnull()&sum() methods***
>df1.isnull().sum()

**Returning the column names**
>df1.columns

**Drop ID,Notes,Agency, and Status column**
>df1=df1.drop(['Id','Notes','Agency','Status'],axis=1)

**Checking the dataset after droping column**
>df1.head()

**Get overall statistics about the dataset**
>df1.describe(include='all')

**Find the occurance of the employeenames**
>df1['EmployeeName'].value_counts().head()

**Find the no of unique JobTitle**
>df1['JobTitle'].nunique()

**Total no of JobTitle that contain CAPTAIN**
>len(df1[df1['JobTitle'].str.contains('CAPTAIN')])

**Showing the JobTitle that contain CAPTAIN**
>df1[df1['JobTitle'].str.contains('CAPTAIN')]['JobTitle']

**Display all the employee names  from the fire department**
>df1[df1['JobTitle'].str.contains('FIRE DEPARTMENT')]['EmployeeName']

**Replace Not Provided in EmployeeName column to NAN**
```
df1['EmployeeName']
df1['EmployeeName'].str.contains('Not provided')
df1[['EmployeeName','JobTitle']]=df1[['EmployeeName','JobTitle']].replace('Not provided',np.nan)
df1
```
**Find the JobTitle of the ALBERT PARDINI**
```
df1.columns
df1[df1['EmployeeName']=='ALBERT PARDINI']['JobTitle']
```
**How much ALBERT PARDINI make include(Benefits)**
```
df1.columns
df1[df1['EmployeeName']=='ALBERT PARDINI']['TotalPayBenefits']
```
**Display the name of the person having highest BasePay**
```
df1.columns
df1['BasePay'] = pd.to_numeric(df1['BasePay'],errors='coerce')
df1[df1['BasePay'].max()==df1['BasePay']]
```
**Find Average BasePay of all employee per year**
```
df1.columns
df1['BasePay'] = pd.to_numeric(df1['BasePay'],errors='coerce')
df1.groupby('Year')['BasePay'].mean()
```
**Find Average BasePay of all employee per JobTitle**
```
df1.columns
df1.groupby('JobTitle')['BasePay'].mean()
```
**Find average BasePay of employee having JobTitle ACCOUNTANT**
>df1[df1['JobTitle']=='ACCOUNTANT']['BasePay'].mean()

**Find no of employee in each JobTitle**
```
df1.columns
df1['JobTitle'].value_counts()


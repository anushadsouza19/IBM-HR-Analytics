# IBM Employee Attrition Analysis
## Summary
IBM, a global leader in technology and innovation, operates across 174 countries with business verticals spanning hardware, software, and IT services. Like many service-driven organizations, employee attrition is a major concern, losing skilled professionals means losing valuable knowledge and experience.

This project dives into the factors influencing employee attrition, aiming to uncover patterns and insights that can help predict or reduce it.

🧭 Project Stages:
This analysis follows a practical, structured workflow:

### 🔹Data Preparation
We use the IBM HR Analytics Employee Attrition & Performance dataset from Kaggle, which contains information on employee demographics, job roles, compensation, satisfaction levels, and more.

### 🔹Data Processing

#### Installing the necessary packages needed for cleaning and analysis.

```bash
#Installing the packages
import pandas as pd
import numpy as np

#Data Viz
import matplotlib.pyplot as plt
from matplotlib import style
import seaborn as sns
```
#### Loading the dataset
```bash
dataset = pd.read_csv('D:\Data analytics\Projects\Python proj\IBM Attrition Data.csv')
```
#### Exploring the dataframe
```bash
dataset.head() 
  ```
### 🔹Analyze & Visualize
#### a) Explore data of employees who left the company

```bash
plt.figure(figsize=(6,4))
dataset['Attrition'].value_counts().plot(kind='bar', color='orange')
plt.title("Overall Attrition Rate")
plt.xlabel("Attrition Status")
plt.ylabel("Number of Employees")
plt.show()
```
![1](https://github.com/user-attachments/assets/134749bb-7c07-4c9a-b06b-2ef3969a9215)

#### b) How Age Relates to Employee Attrition?

```bash
plt.figure(figsize=(10,6))
sns.histplot(data=dataset, x='Age', hue='Attrition', bins=30, multiple='dodge')
plt.title("Age Distribution by Attrition (Side-by-Side)")
plt.xlabel("Age")
plt.ylabel("Number of Employees")
plt.show()

```
![2](https://github.com/user-attachments/assets/6e8ec7f5-51cb-4d01-a06e-3cb5ff6815fc)

#### c) Which Age Groups Are Leaving the Most?
```bash

dataset['AgeGroup'] = pd.cut(dataset['Age'], bins=[18,25,30,35,40,45,50,60])
attrition_by_age = dataset.groupby('AgeGroup')['Attrition'].value_counts(normalize=True).unstack() * 100

attrition_by_age['Yes'].plot(kind='bar', figsize=(10,6), color='tomato')
plt.title("Attrition Percentage by Age Group")
plt.xlabel("Age Group")
plt.ylabel("Attrition Rate (%)")
plt.show()
```
![3](https://github.com/user-attachments/assets/f733e6c2-9010-4f93-9e85-c9ad447fcf64)

#### d) Attrition Rates Across Departments

```bash
plt.figure(figsize=(7,5))
sns.countplot(data=dataset, x='Department', hue='Attrition')
plt.title("Attrition Across Departments")
#plt.xticks(rotation=145)
plt.ylabel("Number of Employees")
plt.show()
```
![4](https://github.com/user-attachments/assets/2206e6ec-ebfd-4447-8233-e90a160535d6)

#### e) Education Field and Its Impact on Attrition

```bash
plt.figure(figsize=(8,5))
sns.countplot(data=dataset, x='Education_Field', hue='Attrition',  palette={'Yes': 'tomato', 'No': 'skyblue'})
plt.title("Attrition by Education Field")
plt.xticks(rotation=45)
plt.show()
```
![5](https://github.com/user-attachments/assets/42b4ea2d-5dcd-4c70-b67e-dde1532b6000)

#### f) Does Environment Satisfaction Affect Attrition?

```bash
plt.figure(figsize=(7,5))
sns.countplot(data=dataset, x='Environment_Satisfaction', hue='Attrition',  palette={'Yes': 'grey', 'No': 'orange'})
plt.title("Attrition vs Environment Satisfaction")
plt.xlabel("Environment Satisfaction (1-4)")
plt.show()
```
![6](https://github.com/user-attachments/assets/85a1b784-e177-4fb5-a75e-04b69f55c1e9)

#### g) Job Satisfaction Levels Among Employees Who Left

```bash
plt.figure(figsize=(7,5))
sns.countplot(data=dataset, x='Job_Satisfaction', hue='Attrition', palette='Set2')
plt.title("Attrition by Job Satisfaction Level")
plt.xlabel("Job Satisfaction (1-4)")
plt.show()
```
![7](https://github.com/user-attachments/assets/998c5bab-8357-453d-b690-931676db97fb)

#### h) Attrition Patterns Based on Marital Status

```bash
plt.figure(figsize=(7,5))
sns.countplot(data=dataset, x='Marital_Status', hue='Attrition', palette='Set1')
plt.title("Attrition by Marital Status")
plt.show()
```
![8](https://github.com/user-attachments/assets/f70492e0-131a-45e5-8cca-8941c9f3b428)

#### i) Is Salary a Factor in Employee Turnover?

```bash
plt.figure(figsize=(8,5))
sns.boxplot(data=dataset, x='Attrition', y='Monthly_Income')
plt.title("Attrition by Monthly Income")
plt.show()
```
![9](https://github.com/user-attachments/assets/90c4f8bc-35a4-4f7a-9578-89e52e5a71fd)

#### j) Do Employees with More Job History Leave More Often?

```bash
plt.figure(figsize=(8,5))
sns.boxplot(data=dataset, x='Attrition', y='No_Companies_Worked', palette='Set3')
plt.title("Attrition vs Number of Companies Worked")
plt.show()
```
![10](https://github.com/user-attachments/assets/bee28fdf-340d-4c61-9868-e9f43cd61f2a)

#### k) Work-Life Balance and Its Link to Attrition

```bash
plt.figure(figsize=(7,5))
sns.countplot(data=dataset, x='Work_Life_Balance', hue='Attrition', palette='Set2')
plt.title("Attrition by Work-Life Balance Rating")
plt.xlabel("Work-Life Balance (1 = worst, 4 = best)")
plt.show()
```
![11](https://github.com/user-attachments/assets/23e717b9-fe48-4557-b333-bca47f075f87)

#### l) Does Tenure at the Company Influence Attrition?

```bash
plt.figure(figsize=(8,5))
sns.boxplot(data=dataset, x='Attrition', y='Years_At_Company', palette='Set1')
plt.title("Attrition vs Years at Company")
plt.show()
```
![12](https://github.com/user-attachments/assets/f1bbd7f2-c129-4c34-94ed-0d2bfa7d46d2)

  

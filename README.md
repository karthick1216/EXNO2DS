# EXNO2DS-Exploratory Data Analysis
# AIM:
      To perform Exploratory Data Analysis on the given data set.
      
# EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT
## Developed by : Karthick . S
## Register no : 212224230114
~~~
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
df=pd.read_csv("/content/titanic_dataset.csv")
df
~~~
![Screenshot 2025-03-27 112754](https://github.com/user-attachments/assets/c5c0fa1f-be09-4821-ac1e-43722b99a4b2)
~~~
df.info()
~~~
![Screenshot 2025-03-27 113023](https://github.com/user-attachments/assets/c3b34149-0076-4d87-90e2-ce8feeb7d97f)
~~~
df.shape
~~~
![Screenshot 2025-03-27 113116](https://github.com/user-attachments/assets/2b5fa65c-0f0f-4969-914d-c31f19188a98)
~~~
df.set_index("PassengerId",inplace=True)
df.describe()
~~~
![Screenshot 2025-03-27 113215](https://github.com/user-attachments/assets/e016cebf-d4d6-4d00-a77c-87912ffd563a)
~~~
df.shape
~~~
![Screenshot 2025-03-27 113327](https://github.com/user-attachments/assets/bc3ed049-7144-478b-ba23-139e031f6a7e)
~~~
df.nunique()
~~~
![Screenshot 2025-03-27 113459](https://github.com/user-attachments/assets/66940af2-da88-40e2-afde-df5a72d513e8)
~~~
df["Survived"].value_counts()
~~~
![Screenshot 2025-03-27 113547](https://github.com/user-attachments/assets/4d79f307-cc3c-4b5c-86b4-62d37aafef28)
~~~
per=(df["Survived"].value_counts()/df.shape[0]*100).round(2)
per
~~~
![Screenshot 2025-03-27 113636](https://github.com/user-attachments/assets/729a1ce7-099f-42dc-b123-f0143e47b625)
~~~
sns.countplot(data=df,x="Survived")
~~~
![Screenshot 2025-03-27 113726](https://github.com/user-attachments/assets/0203a26f-ed65-407d-b274-cf1c1f3c8333)
~~~
df
~~~
![Screenshot 2025-03-27 113818](https://github.com/user-attachments/assets/78b87b4e-5a03-46b9-b4c6-bc02a2a42fd2)
~~~
df.Pclass.unique()
~~~
![Screenshot 2025-03-27 113911](https://github.com/user-attachments/assets/4388190e-4bd2-46bf-97e9-dc6e95ac5735)
~~~
df.rename(columns={'Sex':'Gender'},inplace=True)
df
~~~
![Screenshot 2025-03-27 114029](https://github.com/user-attachments/assets/c86b0ff1-e9ef-4180-be17-9d93901fe9c8)
~~~
#bivariate analysis:
sns.catplot(x="Gender",col="Survived",kind="count",data=df,height=5,aspect=.7)
~~~
![Screenshot 2025-03-27 114121](https://github.com/user-attachments/assets/6af24605-d0c9-4359-bf8c-5ccf1feab0e3)
~~~
sns.catplot(x="Survived",hue="Gender",data=df,kind="count")
~~~
![Screenshot 2025-03-27 114215](https://github.com/user-attachments/assets/fd6826cc-70a0-4cd2-bbe2-910aef7fede3)
~~~
df.boxplot(column="Age",by="Survived")
~~~
![Screenshot 2025-03-27 114259](https://github.com/user-attachments/assets/eb8ba514-255e-4e01-a888-75528e1e0fb7)
~~~
sns.scatterplot(x=df["Age"],y=df["Fare"])
~~~
![Screenshot 2025-03-27 114343](https://github.com/user-attachments/assets/5f18e16d-b75e-4a6e-9138-5903056386dc)
~~~
sns.jointplot(x="Age",y="Fare",data=df)
~~~
![Screenshot 2025-03-27 114445](https://github.com/user-attachments/assets/ae1684f9-5dd0-4aa2-b5d9-f817e2086818)
~~~
#multivariate analysis
fig,ax1=plt.subplots(figsize=(8,5))
plt=sns.boxplot(ax=ax1,x='Pclass',y='Age',hue='Gender',data=df)
~~~
![Screenshot 2025-03-27 114536](https://github.com/user-attachments/assets/f182a88c-5c72-4dae-800a-557b7f80c8c0)
~~~
sns.catplot(data=df,col="Survived",x="Gender",hue="Pclass",kind="count")
~~~
![Screenshot 2025-03-27 114626](https://github.com/user-attachments/assets/d8e43242-537d-4378-8de5-f4b016e32654)
~~~
#co-relation
corr=df.select_dtypes(include=np.number).corr() # Select only numerical columns for correlation
sns.heatmap(corr,annot=True)
~~~
![Screenshot 2025-03-27 114732](https://github.com/user-attachments/assets/f45e2df7-0817-4e14-b73e-00424424c181)
~~~
sns.pairplot(df)
~~~
![Screenshot 2025-03-27 114836](https://github.com/user-attachments/assets/fbcde38c-f521-46ff-9599-1b7876bfcf2b)
![Screenshot 2025-03-27 114902](https://github.com/user-attachments/assets/ae13073a-5058-4333-8fa6-2b5a7c8f0a77)
## RESULT
        We have performed Exploratory Data Analysison the given data set successfully.

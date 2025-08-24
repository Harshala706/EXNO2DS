# EXNO2DS
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
```
import pandas as pd
df=pd.read_csv("/content/titanic_dataset (1).csv")
df
```

<img width="1598" height="534" alt="Screenshot 2025-08-24 212149" src="https://github.com/user-attachments/assets/95cf8108-6fb1-4c48-96f9-03c40101c6a6" />

```
df.shape
```

<img width="1723" height="50" alt="Screenshot 2025-08-24 212216" src="https://github.com/user-attachments/assets/27163428-bb25-4479-abcc-7bc7ed1e4054" />

```
df.set_index("PassengerId",inplace=True)
df
```

<img width="1681" height="571" alt="Screenshot 2025-08-24 212230" src="https://github.com/user-attachments/assets/9754bd8e-64a0-440b-96b0-f1d862fd5108" />

```
df.nunique()
```

<img width="1243" height="533" alt="Screenshot 2025-08-24 212245" src="https://github.com/user-attachments/assets/37241e99-e199-470c-b6ea-0aa558b85822" />

```
df['Survived'].value_counts()
```

<img width="900" height="227" alt="Screenshot 2025-08-24 212252" src="https://github.com/user-attachments/assets/52845cd5-904e-4ae4-88c0-558ee046fe34" />

```
df.Pclass.unique()
```

<img width="770" height="52" alt="Screenshot 2025-08-24 212259" src="https://github.com/user-attachments/assets/405c025f-a838-48ad-923a-72ef237a1da4" />

```
df.Survived.unique()
```

<img width="1090" height="62" alt="Screenshot 2025-08-24 212306" src="https://github.com/user-attachments/assets/07dcb4dd-22b4-4925-8dbf-010015058715" />

```
df.rename(columns={"Sex":"Gender"},inplace=True)
df
```

<img width="1697" height="554" alt="Screenshot 2025-08-24 212322" src="https://github.com/user-attachments/assets/c3a01c5b-10a2-4e6f-b87f-e37cd1add50f" />

```
import seaborn as sns
sns.countplot(data=df)
```

<img width="1224" height="558" alt="Screenshot 2025-08-24 212334" src="https://github.com/user-attachments/assets/7ac45399-0b57-45cf-8de3-624e53935930" />

```
sns.countplot(x="Survived",hue="Gender",data=df)
```

<img width="1203" height="579" alt="Screenshot 2025-08-24 212350" src="https://github.com/user-attachments/assets/fad13f2a-218c-4582-8e7e-0f620d3d06dd" />

```
sns.catplot(x="Survived",hue="Gender",data=df)
```

<img width="1186" height="658" alt="Screenshot 2025-08-24 212404" src="https://github.com/user-attachments/assets/bfd560fc-4601-4dcc-855a-5ae2e7889081" />

```
sns.catplot(x="Survived",hue="Gender",data=df,kind="violin")
```

<img width="1174" height="667" alt="Screenshot 2025-08-24 212418" src="https://github.com/user-attachments/assets/3d0810da-50f0-49d9-a99c-0eedc10abf6d" />

```
sns.boxplot(data=df)
```

<img width="972" height="560" alt="Screenshot 2025-08-24 212436" src="https://github.com/user-attachments/assets/404ad59b-06b4-4355-96cf-d969e741ee71" />

```
df.boxplot(column="Survived",by="Gender")
```

<img width="1081" height="622" alt="Screenshot 2025-08-24 212448" src="https://github.com/user-attachments/assets/cacc3b25-325a-4b8a-be36-30dd85453f1f" />

```
sns.scatterplot(data=df)
```

<img width="1072" height="578" alt="Screenshot 2025-08-24 212456" src="https://github.com/user-attachments/assets/bfa34358-9fb7-4cd4-859b-115190126305" />

```
sns.scatterplot(x=df['Age'],y=df['Fare'])
```
<img width="1054" height="580" alt="Screenshot 2025-08-24 212504" src="https://github.com/user-attachments/assets/6e7bc8ff-7d43-46f1-8312-b3f7af2ae0ff" />

```
sns.jointplot(x='Age',y='Fare',data=df,kind='kde')
```

<img width="1009" height="778" alt="Screenshot 2025-08-24 212513" src="https://github.com/user-attachments/assets/29277180-11da-4b7d-a0a5-367bbdb99cbb" />

```
sns.jointplot(x='Age',y='Fare',data=df,kind='hist')
```

<img width="1090" height="783" alt="Screenshot 2025-08-24 212524" src="https://github.com/user-attachments/assets/2729f52d-c61a-41b6-9271-7a423ec38594" />

```
sns.pairplot(data=df)
```

<img width="1444" height="838" alt="Screenshot 2025-08-24 212617" src="https://github.com/user-attachments/assets/250feb8f-5310-4a4d-8b11-98d9981b0c2b" />


<img width="1451" height="584" alt="Screenshot 2025-08-24 212631" src="https://github.com/user-attachments/assets/e624f4a6-d6fa-4084-a409-ac145ba6d845" />


```
corr1=df.select_dtypes(include=['number']).corr()
sns.heatmap(corr1,annot=True)
```

<img width="997" height="522" alt="Screenshot 2025-08-24 212646" src="https://github.com/user-attachments/assets/63b7cef4-2621-4f41-a771-fbcdbfdbcc5a" />

```
sns.catplot(x='Gender',col='Survived',data=df,kind='count')
```

<img width="1348" height="606" alt="Screenshot 2025-08-24 212701" src="https://github.com/user-attachments/assets/2bd0c407-13ad-4a90-b49d-1a87a068aef3" />

```
sns.catplot(x='Gender',hue='Survived',data=df,kind='count')
```

<img width="1048" height="600" alt="Screenshot 2025-08-24 212713" src="https://github.com/user-attachments/assets/e0ef52be-3801-4c59-8e7d-a4ab92948f84" />


# RESULT
        Thus , the Exploratory Data Analysis on the given data set was performed successfully.

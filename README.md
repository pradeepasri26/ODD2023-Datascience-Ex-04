## EX-04-MULTIVARIATE-ANALYSIS
## AIM:
To perform Multivariate EDA on the given data set.

## EXPLANATION:
Exploratory data analysis is used to understand the messages within a dataset. This technique involves many iterative processes to ensure that the cleaned data is further sorted to better understand the useful meaning.The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

## ALGORITHM:
Step1:Import the built libraries required to perform EDA and outlier removal.

Step2:Read the given csv file.

Step3:Convert the file into a dataframe and get information of the data.

Step4:Return the objects containing counts of unique values using (value_counts()).

Step5:Plot the counts in the form of Histogram or Bar Graph.

Step6:Use seaborn the bar graph comparison of data can be viewed.

Step7:Find the pairwise correlation of all columns in the dataframe.corr()

Step8:Save the final data set into the file.

## PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

dt = pd.read_csv('/content/titanic_dataset.csv')

dt

dt.info()

dt.set_index("PassengerId",inplace=True)

dt.shape

dt.describe()

dt.nunique()

dt["Survived"].value_counts()

per = (dt["Survived"].value_counts()/dt.shape[0]*100).round(2)

per

sns.countplot(data=dt,x="Survived")

dt

dt.Pclass.unique()

dt.rename(columns = {'Sex':'Gender'}, inplace = True)
dt

sns.catplot(x="Gender",col="Survived",kind="count",data=dt,height=5, aspect=.7)

sns.catplot(x='Survived',hue = "Gender",data = dt,kind = "count")

fig, ax1 = plt.subplots(figsize=(8,5))
graph = sns.countplot(ax=ax1,data=dt,x="Survived",hue="Pclass",palette="rainbow")
graph.set_xticklabels(graph.get_xticklabels())
for p in graph.patches:
  height = p.get_height()
  graph.text(p.get_x()+p.get_width()/2, height + 20.8,height,ha="left")

dt.boxplot(column="Age",by="Survived")

sns.scatterplot(x = dt["Age"],y = dt["Fare"])

fig, ax1 = plt.subplots(figsize = (8,5))
pt = sns.boxplot(ax = ax1,x = 'Pclass',y = 'Age', hue='Gender',data=dt)

sns.catplot(data=dt,col="Survived",x="Gender",hue ="Pclass",kind = "count")

g = sns.catplot(data=dt,col="Survived",x="Gender",hue ="Pclass",kind = "count",legend=True)
g.fig.set_size_inches(8,5)
g.fig.subplots_adjust(top=0.81,right=0.86)
ax = g.facet_axis(0,0)
for p in ax.patches:
  ax.text(p.get_x()- 0.01,p.get_height() * 1.02,'{0:.1f}'.format(p.get_height()),color='red',rotation='horizontal',size='small')

## Co-relation
corr = dt.corr()
sns.heatmap(corr,annot=True)

sns.pairplot(dt)
```
## OUTPUT:
![image](https://github.com/pradeepasri26/ODD2023-Datascience-Ex-04/assets/131433142/e85ea7a2-3f40-4bd7-b0f5-4143217dbf25)

![image](https://github.com/pradeepasri26/ODD2023-Datascience-Ex-04/assets/131433142/61477b8b-cb47-483c-b346-c80cfd0b2146)

![image](https://github.com/pradeepasri26/ODD2023-Datascience-Ex-04/assets/131433142/6165f526-d63e-4211-9286-05e8f5d77cf8)

![image](https://github.com/pradeepasri26/ODD2023-Datascience-Ex-04/assets/131433142/d17a8eb0-79b8-4609-93d8-521f1e37ba54)

![image](https://github.com/pradeepasri26/ODD2023-Datascience-Ex-04/assets/131433142/acca521c-b026-4ccc-9c98-d12e610eecde)

![image](https://github.com/pradeepasri26/ODD2023-Datascience-Ex-04/assets/131433142/a187203a-d9dc-4f1e-a3fa-5a7ea3d05b73)

![image](https://github.com/prad\eepasri26/ODD2023-Datascience-Ex-04/assets/131433142/666b9149-1412-4c61-90ac-4bf8de4ffe9c)

![image](https://github.com/pradeepasri26/ODD2023-Datascience-Ex-04/assets/131433142/e199a21a-aed8-42c0-9a45-1160563d4358)

![image](https://github.com/pradeepasri26/ODD2023-Datascience-Ex-04/assets/131433142/c2def247-7868-44d7-9fd3-19b2c5a4db78)

![image](https://github.com/pradeepasri26/ODD2023-Datascience-Ex-04/assets/131433142/88b43f5c-8493-43c1-95ad-12580986dbea)

![image](https://github.com/pradeepasri26/ODD2023-Datascience-Ex-04/assets/131433142/a8121947-20cc-406a-bda2-0dac1f39425e)

![image](https://github.com/pradeepasri26/ODD2023-Datascience-Ex-04/assets/131433142/5ceb7df3-8b61-44e2-a652-d95d1e092d39)

![image](https://github.com/pradeepasri26/ODD2023-Datascience-Ex-04/assets/131433142/ed53ffd6-77e2-45e2-8250-b33ffcbd20a0)

![image](https://github.com/pradeepasri26/ODD2023-Datascience-Ex-04/assets/131433142/926b8c25-501e-4a0d-89af-2ac82d628a74)

![image](https://github.com/pradeepasri26/ODD2023-Datascience-Ex-04/assets/131433142/ace6ceaa-81db-47ef-acba-98bf4bdbdb64)

![image](https://github.com/pradeepasri26/ODD2023-Datascience-Ex-04/assets/131433142/67a60846-98a6-499b-baf9-4670dbdfed5e)

![image](https://github.com/pradeepasri26/ODD2023-Datascience-Ex-04/assets/131433142/03a1aa72-6764-4e36-bea5-ddf6277e4396)

![image](https://github.com/pradeepasri26/ODD2023-Datascience-Ex-04/assets/131433142/adf84faf-bac7-47f3-8345-120c59e36b32)

![image](https://github.com/pradeepasri26/ODD2023-Datascience-Ex-04/assets/131433142/c61f8557-241f-43df-b0f9-a65820010747)

![image](https://github.com/pradeepasri26/ODD2023-Datascience-Ex-04/assets/131433142/d69f36d7-07f5-4a11-ad8d-6642944e3cef)

![image](https://github.com/pradeepasri26/ODD2023-Datascience-Ex-04/assets/131433142/9381a638-7c6c-42ac-a085-b6d801c86bb5)

## RESULT:
Thus the program to perform EDA on the given data set is successfully executed.
























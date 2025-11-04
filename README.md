# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1.Import dataset and print head,info of the dataset

2.check for null values

3.Import kmeans and fit it to the dataset

4.Plot the graph using elbow method

5.Print the predicted array

6.Plot the customer segments


## Program and Output:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Lokeshwaran S
RegisterNumber: 212224240080 
*/
```

```
from google.colab import drive
drive.mount('/content/drive')
import pandas as pd
import matplotlib.pyplot as plt
data=pd.read_csv("drive/MyDrive/ML/Mall_Customers.csv")
data.head()
```

<img width="708" height="249" alt="image" src="https://github.com/user-attachments/assets/480ee3a7-4253-4523-acc4-126bd045f754" />

```
data.info()
```
<img width="508" height="281" alt="image" src="https://github.com/user-attachments/assets/cffcdec7-b83c-4035-9241-f41419d570d0" />

```
data.isnull().sum()
```

<img width="290" height="289" alt="image" src="https://github.com/user-attachments/assets/c5a363eb-f7a8-4740-bae4-2a0cc3a8e585" />

```
from sklearn.cluster import KMeans
wcss=[]
for i in range(1,11):
  kmeans=KMeans(n_clusters=i,init="k-means++")
  kmeans.fit(data.iloc[:,3:])
  wcss.append(kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("No_of_Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")
```

<img width="791" height="596" alt="image" src="https://github.com/user-attachments/assets/1cc71fa7-49a1-46b2-a213-0b45114ddcba" />

```
km = KMeans(n_clusters = 5)
km.fit(data.iloc[:, 3:])
y_pred = km.predict(data.iloc[:, 3:])
y_pred
```

<img width="729" height="234" alt="image" src="https://github.com/user-attachments/assets/c1f2daa8-6d04-447f-bc3f-6f513b0a5451" />

```
data["cluster"] = y_pred
df0=data[data["cluster"]==0]
df1=data[data["cluster"]==1]
df2=data[data["cluster"]==2]
df3=data[data["cluster"]==3]
df4=data[data["cluster"]==4]

plt.scatter(df0["Annual Income (k$)"], df0["Spending Score (1-100)"], c = "red", label = "cluster0")
plt.scatter(df1["Annual Income (k$)"], df1["Spending Score (1-100)"], c = "black", label = "cluster1")
plt.scatter(df2["Annual Income (k$)"], df2["Spending Score (1-100)"], c = "blue", label = "cluster2")
plt.scatter(df3["Annual Income (k$)"], df3["Spending Score (1-100)"], c = "green", label = "cluster3")
plt.scatter(df4["Annual Income (k$)"], df4["Spending Score (1-100)"], c = "magenta", label = "cluster4")
plt.legend()
plt.title("Customer Segments")
```

<img width="719" height="563" alt="image" src="https://github.com/user-attachments/assets/c49bfc0c-14c1-4068-931c-8246ec20c7bd" />







## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.

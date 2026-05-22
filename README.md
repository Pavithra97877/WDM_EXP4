### EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns
### DATE: 
### AIM: To implement Cluster and Visitor Segmentation for Navigation patterns in Python.
### Description:
<div align= "justify">Cluster visitor segmentation refers to the process of grouping or categorizing visitors to a website, 
  application, or physical location into distinct clusters or segments based on various characteristics or behaviors they exhibit. 
  This segmentation allows businesses or organizations to better understand their audience and tailor their strategies, marketing efforts, 
  or services to meet the specific needs and preferences of each cluster.</div>
  
### Procedure:
1) Read the CSV file: Use pd.read_csv to load the CSV file into a pandas DataFrame.
2) Define Age Groups by creating a dictionary containing age group conditions using Boolean conditions.
3) Segment Visitors by iterating through the dictionary and filter the visitors into respective age groups.
4) Visualize the result using matplotlib.

### Program1:
import pandas as pd
df=pd.read_csv('/content/clustervisitor.csv')
print(df)
cluster={"Young":(df['Age']<=30),"Middle":((df['Age']>30) & (df['Age']<=50)),"Old":(df['Age']>50)}
count=[]
for group,condition in cluster.items():
  visitors=df[condition]
  count.append(len(visitors))
  print(f"The visitors on {group} are :")
  print(visitors)
  print("count=",len(visitors))
import matplotlib.pyplot as plt
plt.figure(figsize=(8,6))
plt.bar(['Young','Middle','Old'],count,color="skyblue")
plt.xlabel('Age Groups')
plt.ylabel('Number of Visitors')
plt.title("Visitor Distribution Across Age Groups")
plt.show()

### Output:
<img width="462" height="692" alt="546543619-842cf8d5-7ea6-4681-98ad-380ef69db608" src="https://github.com/user-attachments/assets/0aaacdd5-b9c5-42fc-988c-c7a96c69a23f" />

<img width="781" height="558" alt="546543682-c020d268-e7e8-4dbe-aba7-f2bdb6331395" src="https://github.com/user-attachments/assets/95d934e8-b300-4333-904b-d70f93ac7cf4" />

# Program2:
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans
df1=df['Age']
df2=df['Income']
df3=pd.concat([df1,df2],axis=1)
s=StandardScaler()
newdf=s.fit_transform(df3)
k=KMeans(n_clusters=3,random_state=42)
df3['cluster']=k.fit_predict(newdf)
df3
plt.figure(figsize=(8,6))
plt.scatter(x=df3['Age'],y=df3['Income'],c=df3['cluster'])
plt.xlabel('Age')
plt.ylabel('Income')
plt.title('Visitor Distribution in Different Clusters')
plt.show()

### Output:
<img width="202" height="625" alt="546546259-4340bd53-6688-485b-9b6e-9b6a9f12c162" src="https://github.com/user-attachments/assets/ede25e72-c399-455f-b6c1-aaaf12128398" />

<img width="862" height="629" alt="546546406-a530cbf2-879e-4642-93c8-7c794ed4896e" src="https://github.com/user-attachments/assets/d9dcce11-51b6-4b8e-8c7f-f98085f64eda" />

### Result:
The implementation of Cluster and Visitor Segmentation for Navigation patterns in Python has been executed successfully.

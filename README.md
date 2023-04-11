# EX-05-Feature-Generation


## AIM
To read the given data and perform Feature Generation process and save the data to a file. 

# Explanation
Feature Generation (also known as feature construction, feature extraction or feature engineering) is the process of transforming features into new features that better relate to the target.
 

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature Generation techniques to all the feature of the data set
### STEP 4
Save the data to the file


# CODE

```
import pandas as pd
df=pd.read_csv("data.csv")
df

#feature generation
import category_encoders as ce
be=ce.BinaryEncoder()
ndf=be.fit_transform(df["bin_1"])
df["bin_1"] = be.fit_transform(df["bin_1"])
ndf

ndf2=be.fit_transform(df["bin_2"])
df["bin_2"] = be.fit_transform(df["bin_2"])
ndf2

df1=df.copy()
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder,OneHotEncoder
import category_encoders as ce
be=ce.BinaryEncoder()
ohe=OneHotEncoder(sparse=False)
le=LabelEncoder()
oe=OrdinalEncoder()


df1["City"] = ohe.fit_transform(df1[["City"]])

temp=['Cold','Warm','Hot','Very Hot']
oe1=OrdinalEncoder(categories=[temp])
df1['Ord_1'] = oe1.fit_transform(df1[["Ord_1"]])

edu=['High School','Diploma','Bachelors','Masters','PhD']
oe2=OrdinalEncoder(categories=[edu])
df1['Ord_2']= oe2.fit_transform(df1[["Ord_2"]])
df1

#feature scaling
from sklearn.preprocessing import MinMaxScaler
sc=MinMaxScaler()
df2=pd.DataFrame(sc.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df2

from sklearn.preprocessing import StandardScaler
sc1=StandardScaler()
df3=pd.DataFrame(sc1.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df3

from sklearn.preprocessing import MaxAbsScaler
sc2=MaxAbsScaler()
df4=pd.DataFrame(sc2.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df4

from sklearn.preprocessing import RobustScaler
sc3=RobustScaler()
df5=pd.DataFrame(sc3.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df5


Encoading.draw:


import pandas as pd
df=pd.read_csv("Encoding Data.csv")
df

#feature generation
import category_encoders as ce
be=ce.BinaryEncoder()
ndf=be.fit_transform(df["bin_1"])
df["bin_1"] = be.fit_transform(df["bin_1"])
ndf

ndf2=be.fit_transform(df["bin_2"])
df["bin_2"] = be.fit_transform(df["bin_2"])
ndf2

df1=df.copy()
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
le=LabelEncoder()
oe=OrdinalEncoder()

df1["nom_0"] = oe.fit_transform(df1[["nom_0"]])
temp=['Cold','Warm','Hot']
oe2=OrdinalEncoder(categories=[temp])
df1['ord_2'] = oe2.fit_transform(df1[['ord_2']])

df1

#feature scaling
from sklearn.preprocessing import MinMaxScaler
sc=MinMaxScaler()
df0=pd.DataFrame(sc.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
df0

from sklearn.preprocessing import StandardScaler
sc1=StandardScaler()
df2=pd.DataFrame(sc1.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
df2

from sklearn.preprocessing import MaxAbsScaler
sc2=MaxAbsScaler()
df3=pd.DataFrame(sc2.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
df3

from sklearn.preprocessing import RobustScaler
sc3=RobustScaler()
df4=pd.DataFrame(sc3.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
df4


Titanic.csv:

import pandas as pd
df=pd.read_csv("titanic_dataset.csv")
df

#removing unwanted data
df.drop("Name",axis=1,inplace=True)
df.drop("Ticket",axis=1,inplace=True)
df.drop("Cabin",axis=1,inplace=True)

#data cleaning
df.isnull().sum()

df["Age"]=df["Age"].fillna(df["Age"].median())
df["Embarked"]=df["Embarked"].fillna(df["Embarked"].mode()[0])

df.isnull().sum()

df

#feature encoding

from category_encoders import BinaryEncoder
be=BinaryEncoder()
df["Sex"]=be.fit_transform(df[["Sex"]])
ndf=be.fit_transform(df["Sex"])
ndf

df1=df.copy()
from sklearn.preprocessing import LabelEncoder, OrdinalEncoder
embark=['S','C','Q']
e1=OrdinalEncoder(categories=[embark])
df1['Embarked'] = e1.fit_transform(df[['Embarked']])
df1

#feature scaling
from sklearn.preprocessing import MinMaxScaler
sc=MinMaxScaler()
df2=pd.DataFrame(sc.fit_transform(df1),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
df2

from sklearn.preprocessing import StandardScaler
sc1=StandardScaler()
df3=pd.DataFrame(sc1.fit_transform(df1),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
df3

from sklearn.preprocessing import MaxAbsScaler
sc2=MaxAbsScaler()
df4=pd.DataFrame(sc2.fit_transform(df1),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
df4

from sklearn.preprocessing import RobustScaler
sc3=RobustScaler()
df5=pd.DataFrame(sc3.fit_transform(df1),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
df5
```

# OUPUT

![image](https://user-images.githubusercontent.com/119122478/231107215-6a18a3f3-b0ab-484c-9970-6711560085e9.png)

![image](https://user-images.githubusercontent.com/119122478/231107285-51241e64-58be-40c9-a971-8fbad6451140.png)

![image](https://user-images.githubusercontent.com/119122478/231107381-74191ab8-076d-4180-bfb7-124f59c8bc2c.png)

![image](https://user-images.githubusercontent.com/119122478/231107577-1da07b81-16c0-473f-974d-c0c14af07898.png)

![image](https://user-images.githubusercontent.com/119122478/231107911-ee1ca2a2-fb56-43c1-bfa6-3cd4e2fd1d3e.png)


![image](https://user-images.githubusercontent.com/119122478/231108040-ab2a58e2-1a28-44a1-a786-b42fac07661a.png)

 ![image](https://user-images.githubusercontent.com/119122478/231108493-60c45084-066a-4e67-95e3-f6b334984167.png)
 
 ![image](https://user-images.githubusercontent.com/119122478/231108581-8b574793-d530-436e-aded-54faf752a844.png)

![image](https://user-images.githubusercontent.com/119122478/231108698-4104b3af-2d68-4bc6-bba7-e67ac1be8929.png)

![image](https://user-images.githubusercontent.com/119122478/231108791-7677fea6-539f-4dd7-ac9d-4baca39c564f.png)

![image](https://user-images.githubusercontent.com/119122478/231109014-0448a52b-f9a7-4759-8dc7-be72b5cb6155.png)

![image](https://user-images.githubusercontent.com/119122478/231109210-2d9cdb68-3ee6-4332-bca6-30a98c40d632.png)

![image](https://user-images.githubusercontent.com/119122478/231109304-fe652c12-a312-43ce-bf5e-330e5a275664.png)

![image](https://user-images.githubusercontent.com/119122478/231109356-ce09ed73-3ab0-4025-bb57-17021305af9b.png)

![image](https://user-images.githubusercontent.com/119122478/231109427-ddb711cc-1905-4f31-8ed6-2161e7839dcb.png)

![image](https://user-images.githubusercontent.com/119122478/231109483-438bb6bd-3fe5-4bca-81c7-5e856a61fe36.png)

![image](https://user-images.githubusercontent.com/119122478/231109551-48b55226-0f33-4ecf-8ae6-a40d712d6320.png)

 ![image](https://user-images.githubusercontent.com/119122478/231109679-c7fb6cc7-4e67-4b08-b70f-29e02ee5cd34.png)
 
 ![image](https://user-images.githubusercontent.com/119122478/231109823-f8e07d03-f184-4609-a9b4-9779051fa8e5.png)
 
 ![image](https://user-images.githubusercontent.com/119122478/231109969-cc4226b9-7109-4e55-8bb3-cf7f98375044.png)

![image](https://user-images.githubusercontent.com/119122478/231110084-1266d721-5e07-496d-a7a5-bd8925b3f83f.png)

![image](https://user-images.githubusercontent.com/119122478/231110212-3c752b1d-08e5-497a-b7ef-b364cd399a56.png)

![image](https://user-images.githubusercontent.com/119122478/231110516-32f3245f-ce71-46a2-9fb2-89a973e3fe6f.png)

# RESULT:

Feature Generation process and Feature Scaling process is applied to the given data frames sucessfully.



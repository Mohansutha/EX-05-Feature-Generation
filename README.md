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

Program developed by: Mohanraj S
Register number : 212221230065

## DATA.CSV:

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

## ENCODING.CSV:

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

## TITANIC.CSV:

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









## OUPUT

## DATA.CSV:

![1](https://user-images.githubusercontent.com/94828335/167990801-67229376-0755-4867-96dd-988da072e253.png)

![2](https://user-images.githubusercontent.com/94828335/167990825-7f9faba8-724a-4f5d-ad6d-4f1df71e6fdf.png)

![3](https://user-images.githubusercontent.com/94828335/167990856-18529176-51ab-4717-8832-2552e7b62c8c.png)

![4](https://user-images.githubusercontent.com/94828335/167990896-fb4f4dd9-ea48-429c-8fc1-004592b318c9.png)

![o5](https://user-images.githubusercontent.com/94828335/167990924-8299aaee-9e1a-4999-9e3b-ca5ba89e218b.png)

![o6](https://user-images.githubusercontent.com/94828335/167990964-87e5b974-aa9a-490b-872a-09c67cf111b2.png)

![o7](https://user-images.githubusercontent.com/94828335/167990983-feee4e3e-40a2-4009-a254-221fdc3ca20e.png)

![o8](https://user-images.githubusercontent.com/94828335/167991006-febe61c6-b2c8-418b-b4b3-06eac168d8ea.png)

## ENCODING.CSV:

![o9](https://user-images.githubusercontent.com/94828335/167991120-02fd8295-97bb-41f6-84c6-3d9487382de3.png)

![o10](https://user-images.githubusercontent.com/94828335/167991140-6b7cb5f3-d0d5-45bc-a5d5-e065490f14fe.png)

![o11](https://user-images.githubusercontent.com/94828335/167991168-83cc67b0-47c9-413c-89b6-f9eca50e3b4c.png)

![o12](https://user-images.githubusercontent.com/94828335/167991197-4a6a25b7-23c7-4948-b442-301d5e93d359.png)

![o13](https://user-images.githubusercontent.com/94828335/167991225-9f7568aa-1f2d-4e09-99a5-e075c071c533.png)

![o14](https://user-images.githubusercontent.com/94828335/167991261-349e38fa-17b6-4723-87f9-b4564364d357.png)

![o15](https://user-images.githubusercontent.com/94828335/167991282-2bfdd8e6-f943-4b79-9b9e-0eb5b46ddf38.png)

![o16](https://user-images.githubusercontent.com/94828335/167991303-38bebd1c-8741-4114-b8ae-489a9462b073.png)

## TITANIC.CSV:

![o17](https://user-images.githubusercontent.com/94828335/167992946-860069d6-452f-4b03-936f-60d086c09974.png)

![o18](https://user-images.githubusercontent.com/94828335/167992969-70a2d765-1cf5-40be-8233-553370bc6e21.png)

![o19](https://user-images.githubusercontent.com/94828335/167992999-aadd544a-87d9-4fe9-a6b1-9bce44721a42.png)

![o20](https://user-images.githubusercontent.com/94828335/167993023-96542361-88f6-4af3-a158-67e081d4f81d.png)

![o21](https://user-images.githubusercontent.com/94828335/167993037-11dd775f-853c-40c1-9ab2-b01e419632ff.png)

![o22](https://user-images.githubusercontent.com/94828335/167993063-dd7c2db9-525d-4256-baa4-790d74a9f3ff.png)

![o23](https://user-images.githubusercontent.com/94828335/167993086-4d94c6d4-71f4-46a5-92b7-5daa31af5d4f.png)

![o24](https://user-images.githubusercontent.com/94828335/167993106-e2ac5067-ef30-4e23-980b-a094dfbdd1e6.png)

![o25](https://user-images.githubusercontent.com/94828335/167993127-48ce258f-e033-4518-81d0-7d59544ade8b.png)

![o26](https://user-images.githubusercontent.com/94828335/167993155-a0d1252c-e12e-4711-894f-254b5b21d93f.png)

![o27](https://user-images.githubusercontent.com/94828335/167993185-887c4d30-005a-4ceb-b019-03880bcf30a3.png)

##RESULT:

Feature Generation process and Feature Scaling process is applied to the given data frames sucessfully.


















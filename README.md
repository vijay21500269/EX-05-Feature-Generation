# EX-05-Feature-Generation


## AIM
To read the given data and perform Feature Generation process and save the data to a file. 

# Explanation
Feature Generation (also known as feature construction, feature extraction or feature engineering) is the process of transforming features into new features that better relate to the target.
It includes two process:
1.Feature Encoding
2.Feature Scaling
## FEATURE ENCODING:
# 1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data
# 2.Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
# 3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
# 4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.
## FEATURE SCALING:
# 1. Standard Scaler
It is also called Z-score normalization. It calculates the z-score of each value and replaces the value with the calculated Z-score. The features are then rescaled with x̄ =0 and σ=1
# 2. MinMaxScaler
It is also referred to as Normalization. The features are scaled between 0 and 1. Here, the mean value remains same as in Standardization, that is, 0.
# 3. Maximum absolute scaling
Maximum absolute scaling scales the data to its maximum value; that is, it divides every observation by the maximum value of the variable.The result of the preceding transformation is a distribution in which the values vary approximately within the range of -1 to 1.
# 4. RobustScaler
RobustScaler transforms the feature vector by subtracting the median and then dividing by the interquartile range (75% value — 25% value).

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature Generation techniques to all the feature of the data set
### STEP 4
Save the data to the file


# 1.FEATURE GENERATION FOR Data.csv
# CODE FOR FEATURE ENCODING AND FEATURE SCALING:
~~~
import pandas as pd
df=pd.read_csv("data.csv")
df
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
temp=["Cold","Warm","Hot","Very Hot"]
enc=OrdinalEncoder(categories=[temp])
df["Ord_1"]=enc.fit_transform(df[["Ord_1"]])
df
education=["High School","Diploma","Bachelors","Masters","PhD"]
ed=OrdinalEncoder(categories=[education])
df["Ord_2"]=ed.fit_transform(df[["Ord_2"]])
df
pip install category_encoders
from category_encoders import BinaryEncoder
be=BinaryEncoder()
be.fit_transform(df["bin_1"])
df["bin_1"]=be.fit_transform(df[["bin_1"]])
df
be1=BinaryEncoder()
be1.fit_transform(df["bin_2"])
df["bin_2"]=be1.fit_transform(df[["bin_2"]])
df
from sklearn.preprocessing import OneHotEncoder
ohe=OneHotEncoder(sparse=False)
ohe.fit_transform(df[["City"]])
from category_encoders import TargetEncoder
te=TargetEncoder()
te.fit_transform(X=df['Ord_1'],y=df["Target"])
le=LabelEncoder()
df["City"]=le.fit_transform(df[["City"]])
df

from sklearn.preprocessing import StandardScaler
sc=StandardScaler()
df1=pd.DataFrame(sc.fit_transform(df),columns=['id','bin_1','bin_2','City','Ord_1','Ord_2','Target'])
df1

from sklearn.preprocessing import MaxAbsScaler
mas=MaxAbsScaler()
df2=pd.DataFrame(mas.fit_transform(df),columns=['id','bin_1','bin_2','City','Ord_1','Ord_2','Target'])
df2

from sklearn.preprocessing import MinMaxScaler
mms=MinMaxScaler()
df3=pd.DataFrame(mms.fit_transform(df),columns=['id','bin_1','bin_2','City','Ord_1','Ord_2','Target'])
df3

from sklearn.preprocessing import RobustScaler
rs=RobustScaler()
df4=pd.DataFrame(rs.fit_transform(df),columns=['id','bin_1','bin_2','City','Ord_1','Ord_2','Target'])
df4
~~~


# OUPUT:
## Given DataFrame
![img](https://github.com/vijay21500269/EX-05-Feature-Generation/blob/main/ds.1.png)
## Feature encoding using Ordinal Encoder
![img](https://github.com/vijay21500269/EX-05-Feature-Generation/blob/main/ds.2.png)
![img](https://github.com/vijay21500269/EX-05-Feature-Generation/blob/main/ds.3.png)
# Feature encoding using Binary Encoder
![img](https://github.com/vijay21500269/EX-05-Feature-Generation/blob/main/ds.4.png)
![img](https://github.com/vijay21500269/EX-05-Feature-Generation/blob/main/ds.5.png)
![img](https://github.com/vijay21500269/EX-05-Feature-Generation/blob/main/ds.6.png)
![img](https://github.com/vijay21500269/EX-05-Feature-Generation/blob/main/ds.7.png)
# Feature encoding using One Hot Encoder
![img](https://github.com/vijay21500269/EX-05-Feature-Generation/blob/main/ds.8.png)
# Feature encoding using Target Encoder
![img](https://github.com/vijay21500269/EX-05-Feature-Generation/blob/main/ds.9.png)
# Feature encoding using Label Encoder
![img](https://github.com/vijay21500269/EX-05-Feature-Generation/blob/main/ds.10.png)
# Feature scaling using Standard Scaler
![img](https://github.com/vijay21500269/EX-05-Feature-Generation/blob/main/ds.11.png)
# Feature scaling using MaxAbs Scaler
![img](https://github.com/vijay21500269/EX-05-Feature-Generation/blob/main/ds.12.png)
# Feature scaling using MinMax Scaler
![img](https://github.com/vijay21500269/EX-05-Feature-Generation/blob/main/ds.13.png)
# Feature scaling using Robust Scaler
![img](https://github.com/vijay21500269/EX-05-Feature-Generation/blob/main/ds.14.png)
# 2.FEATURE GENERATION FOR Encoding.csv
# CODE FOR FEATURE ENCODING AND FEATURE SCALING:
~~~
import pandas as pd
df=pd.read_csv("Encoding Data.csv")
df
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
temp=["Cold","Warm","Hot"]
enc=OrdinalEncoder(categories=[temp])
df["ord_2"]=enc.fit_transform(df[["ord_2"]])
df
from category_encoders import BinaryEncoder
be=BinaryEncoder()
df['bin_1']=be.fit_transform(df[['bin_1']])
df
be1=BinaryEncoder()
df['bin_2']=be1.fit_transform(df[['bin_2']])
df
from sklearn.preprocessing import OneHotEncoder
ohe=OneHotEncoder(sparse=False)
ohe.fit_transform(df[["nom_0"]])
le=LabelEncoder()
df["nom_0"]=le.fit_transform(df[["nom_0"]])
df

from sklearn.preprocessing import StandardScaler
sc=StandardScaler()
df1=pd.DataFrame(sc.fit_transform(df),columns=['id','bin_1','bin_2','nom_0','Ord_2'])
df1

from sklearn.preprocessing import MinMaxScaler
mms=MinMaxScaler()
df2=pd.DataFrame(mms.fit_transform(df),columns=['id','bin_1','bin_2','nom_0','Ord_2'])
df2

from sklearn.preprocessing import MaxAbsScaler mas=MaxAbsScaler()
df3=pd.DataFrame(mas.fit_transform(df),columns=['id','bin_1','bin_2','nom_0','Ord_2'])
df3

from sklearn.preprocessing import RobustScaler
rs=RobustScaler()
df4=pd.DataFrame(rs.fit_transform(df),columns=['id','bin_1','bin_2','nom_0','Ord_2'])
df4
~~~
# OUTPUT:
## Given DataFrame
![img](https://github.com/vijay21500269/EX-05-Feature-Generation/blob/main/ds.15.png)
## Feature encoding using Ordinal Encoder
![img](https://github.com/vijay21500269/EX-05-Feature-Generation/blob/main/ds.16.png)
## Feature encoding using Binary Encoder
![img](https://github.com/vijay21500269/EX-05-Feature-Generation/blob/main/ds.17.png)
![img](https://github.com/vijay21500269/EX-05-Feature-Generation/blob/main/ds.18.png)
## Feature encoding using One Hot Encoder
![img](https://github.com/vijay21500269/EX-05-Feature-Generation/blob/main/ds.19.png)
## Feature encoding using Label Encoder
![img](https://github.com/vijay21500269/EX-05-Feature-Generation/blob/main/ds.20.png)
![img](https://github.com/vijay21500269/EX-05-Feature-Generation/blob/main/ds.21.png)
## Feature scaling using Standard Scaler
![img](https://github.com/vijay21500269/EX-05-Feature-Generation/blob/main/ds.22.png)
## Feature scaling using MinMax Scaler
![img](https://github.com/vijay21500269/EX-05-Feature-Generation/blob/main/ds.23.png)
## Feature scaling using MaxAbs Scaler
![img](https://github.com/vijay21500269/EX-05-Feature-Generation/blob/main/ds.24.png)
## Feature scaling using Robust Scaler
![img](https://github.com/vijay21500269/EX-05-Feature-Generation/blob/main/ds.25.png)
# 3.FEATURE GENERATION FOR titanic_dataset.csv
# CODE FOR FEATURE ENCODING AND FEATURE SCALING:
~~~
import pandas as pd
df=pd.read_csv("titanic_dataset.csv")
df
df.isnull().sum()
df["Age"]=df["Age"].fillna(df["Age"].median())
df["Embarked"]=df["Embarked"].fillna(df["Embarked"].mode()[0])
df
df.drop("Cabin",axis=1,inplace=True)
df.drop("Ticket",axis=1,inplace=True)
df.drop("Name",axis=1,inplace=True)
df.isnull().sum()
df
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
embark=["C","S","Q"]
emb=OrdinalEncoder(categories=[embark])
df["Embarked"]=emb.fit_transform(df[["Embarked"]])
df
from category_encoders import BinaryEncoder
be=BinaryEncoder()
df["Sex"]=be.fit_transform(df[["Sex"]])
df

from sklearn.preprocessing import StandardScaler
ss=StandardScaler()
df1=pd.DataFrame(ss.fit_transform(df),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked','PClass'])
df1

from sklearn.preprocessing import MinMaxScaler
mms=MinMaxScaler()
df2=pd.DataFrame(mms.fit_transform(df),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked','PClass'])
df2

from sklearn.preprocessing import MaxAbsScaler
mas=MaxAbsScaler()
df3=pd.DataFrame(mas.fit_transform(df),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked','PClass'])
df3

from sklearn.preprocessing import RobustScaler
rs = RobustScaler()
df4=pd.DataFrame(rs.fit_transform(df),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked','PClass'])
df4
~~~
# OUTPUT:
## Given DataFrame
![img](https://github.com/vijay21500269/EX-05-Feature-Generation/blob/main/ds.26.png)
## Resolving null value data
![img](https://github.com/vijay21500269/EX-05-Feature-Generation/blob/main/ds.27.png)
![img](https://github.com/vijay21500269/EX-05-Feature-Generation/blob/main/ds.28.png)
## Dropping unnecessary columns
![img](https://github.com/vijay21500269/EX-05-Feature-Generation/blob/main/ds.29.png)
## Feature encoding using Ordinal Encoder
![img](https://github.com/vijay21500269/EX-05-Feature-Generation/blob/main/ds.30.png)
## Feature encoding using Binary Encoder
![img](https://github.com/vijay21500269/EX-05-Feature-Generation/blob/main/ds.31.png)
## Feature scaling using Standard Scaler
![img](https://github.com/vijay21500269/EX-05-Feature-Generation/blob/main/ds.32.png)
## Feature scaling using MinMax Scaler
![img](https://github.com/vijay21500269/EX-05-Feature-Generation/blob/main/ds.33.png)
## Feature scaling using MaxAbs Scaler
![img](https://github.com/vijay21500269/EX-05-Feature-Generation/blob/main/ds.34.png)
## Feature scaling using Robust Scaler
![img](https://github.com/vijay21500269/EX-05-Feature-Generation/blob/main/ds.35.png)
# RESULT:
Feature Encoding process and Feature Scaling process is applied to the given data frame sucessfully.
















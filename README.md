# Ex02-OUTLIER DETECTION :
## AIM :
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them

## EXPLANATION :

An Outlier is an observation in a given dataset that lies far from the rest of the observations. That means an outlier is vastly larger or smaller than the remaining values in the set. An outlier is an observation of a data point that lies an abnormal distance from other values in a given population. (odd man out). Outliers badly affect mean and standard deviation of the dataset. These may statistically give erroneous results.

## ALGORITHM :

### Step 1 : 
Read the given Data.
### Step 2 : 
Get the information about the data.
### Step 3 : 
Detect the Outliers using IQR method and Z score.
### Step 4 : 
Remove the outliers.
### Step 5 : 
Plot the datas using Box Plot.

## PROGRAM :

### NAME : MAMTHA I
### REG NO : 212222230076

### bhp.csv :

```

import pandas as pd
import seaborn as sns
import numpy as np
from scipy import stats
from google.colab import files
uploaded=files.upload()
df=pd.read_csv('bhp.csv')
df.info()
print(df.describe())

df.head()

# BEFORE REMOVING OUTLIER :
sns.boxplot(y='price_per_sqft',data=df)

# PERFORMING IQR METHOD :
q1=df['price_per_sqft'].quantile(0.25)
q3=df['price_per_sqft'].quantile(0.75)
IQR=q3-q1
low=q1-1.5*IQR
high=q3+1.5*IQR
new=df[((df['price_per_sqft']>=low)&(df['price_per_sqft']<=high))]

# AFTER REMOVING OUTLIER USING (IQR) METHOD :
sns.boxplot(y='price_per_sqft',data=new)

# PERFORMING ZSCORE METHOD :
z=np.abs(stats.zscore(df['price_per_sqft']))
new2=df[(z<3)]

# AFTER REMOVING OUTLIER USING ZSCORE METHOD :
sns.boxplot(y="price_per_sqft",data=new2)

```
### height_weight.csv :

```
# HEIGHT_WEIGHT.CSV :
import pandas as pd
import seaborn as sns
from google.colab import files
uploaded=files.upload()
df=pd.read_csv('/content/height_weight.csv')
df.info()
df.describe()

# BEFORE REMOVING OUTLIER :
sns.boxplot(y='height',data=df)

# PERFORMING IQR METHOD ON HEIGHT :
height_q1=df['height'].quantile(0.25)
height_q3=df['height'].quantile(0.75)
height_IQR=height_q3-height_q1
height_low=height_q1-1.5*height_IQR
height_high=height_q3+1.5*height_IQR
height_new=df[((df['height']>=height_low)&(df['height']<=height_high))]

# AFTER REMOVING OUTLIER IN HEIGHT :
sns.boxplot(y='height',data=height_new)

# BEFORE REMOVING OUTLIER in WEIGHT :
sns.boxplot(y='weight',data=df)

# PERFORMING IQR METHOD ON HEIGHTS :
weight_q1 = df['weight'].quantile(0.25)
weight_q3 = df['weight'].quantile(0.75)
weight_IQR = weight_q3 - weight_q1
weight_low = weight_q1 - 1.5 * weight_IQR
weight_high = weight_q3 + 1.5 * weight_IQR
weight_new=df[((df['weight']>=weight_low)&(df['weight']<=weight_high))]

# AFTER REMOVING OUTLIER in WEIGHT :
sns.boxplot(y='weight',data=weight_new)

```
## OUTPUT : 

### bhp.csv :

![Screenshot 2023-09-12 221915](https://github.com/Mamthaiyappaprabu/ODD2023---Datascience---Ex-02/assets/119393563/8858d759-c9db-457c-89a8-40ad740b6a2b)

![Screenshot 2023-09-12 221925](https://github.com/Mamthaiyappaprabu/ODD2023---Datascience---Ex-02/assets/119393563/8b99b195-511b-48c9-9343-2af55ae1f4ff)

![Screenshot 2023-09-12 221943](https://github.com/Mamthaiyappaprabu/ODD2023---Datascience---Ex-02/assets/119393563/60533bff-45bc-405f-bfa7-583f3498b5d3)


![Screenshot 2023-09-12 221954](https://github.com/Mamthaiyappaprabu/ODD2023---Datascience---Ex-02/assets/119393563/3faf9a02-a46c-4d2b-b813-6c8c7ebbe3ee)

![Screenshot 2023-09-12 222004](https://github.com/Mamthaiyappaprabu/ODD2023---Datascience---Ex-02/assets/119393563/1d8f27ce-9ca1-4409-a6bb-822d188d438e)




### weight_height.csv :





![Screenshot 2023-09-12 222507](https://github.com/Mamthaiyappaprabu/ODD2023---Datascience---Ex-02/assets/119393563/24e3bc28-459e-463a-b808-ca0b6fc72bf9)

![Screenshot 2023-09-12 222515](https://github.com/Mamthaiyappaprabu/ODD2023---Datascience---Ex-02/assets/119393563/f865d1f4-7469-4a3d-8de5-d7b443a53cf3)


![Screenshot 2023-09-12 222524](https://github.com/Mamthaiyappaprabu/ODD2023---Datascience---Ex-02/assets/119393563/d9703187-8108-484e-8496-68a9e02bddf2)



![Screenshot 2023-09-12 222533](https://github.com/Mamthaiyappaprabu/ODD2023---Datascience---Ex-02/assets/119393563/6b3eb09f-86dd-499c-ab14-b081a6f27df6)



![Screenshot 2023-09-12 222544](https://github.com/Mamthaiyappaprabu/ODD2023---Datascience---Ex-02/assets/119393563/a1396465-262c-4444-870e-c70db14372a4)


## RESULT :

Hence the given set of data is read and the outliers are removed using the IQR method and Zscore method.







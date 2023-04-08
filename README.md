# Ex02-Outlier

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them
    
    # EXPLANATION
    
    An Outlier is an observation in a given dataset that lies far from the rest of the observations. That means an outlier is vastly larger or smaller than the remaining values in the set. An outlier is an observation of a data point that lies an abnormal distance from other values in a given population. (odd man out).Outliers badly affect mean and standard deviation of the dataset. These may statistically give erroneous results.Most machine learning algorithms do not work well in the presence of outlier. So it is desirable to detect and remove outliers.Outliers are highly useful in anomaly detection like fraud detection where the fraud transactions are very different from normal transactions.
    
    # ALGORITHM
    
    STEP 1
Read the given Data

STEP 2
Get the information about the data

STEP 3
Detect the Outliers using IQR method and Z score

STEP 4
Remove the outliers

STEP 5
Plot the datas using Box Plot
    
 # CODE
 
 #  (1) & (2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe.
 
 import pandas as pd import numpy as np import seaborn as sns

df = pd.read_csv("/content/drive/MyDrive/Colab Notebooks/Semester 3/19AI403 - Data Science/bhp.csv") df

df.head()

df.describe()

df.info()

df.isnull().sum()

df.shape

sns.boxplot(x="price_per_sqft",data=df) q1 = df['price_per_sqft'].quantile(0.25) q3 = df['price_Aper_sqft'].quantile(0.75) print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1 ul = q3+1.5IQR ll = q1-1.5IQR

df1 =df[((df['price_per_sqft']>=ll)&(df['price_per_sqft']<=ul))] df1

df1.shape

sns.boxplot(x="price_per_sqft",data=df1)`

(3) Examine price_per_sqft column and use zscore of 3 to remove outliers. from scipy import stats
z = np.abs(stats.zscore(df['price_per_sqft'])) df2 = df[(z<3)] df2

print(df2.shape) sns.boxplot(x="price_per_sqft",data=df2)

(4)(i) For the data set height_weight.csv detect weight outliers using IQR method df3 = pd.read_csv("/content/drive/MyDrive/Colab Notebooks/Semester 3/19AI403 - Data Science/height_weight.csv") df3

df3.head()

df3.info()

df3.describe()

df3.isnull().sum()

df3.shape sns.boxplot(x="weight",data=df3)

q1 = df3['weight'].quantile(0.25) q3 = df3['weight'].quantile(0.75) print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1 ul = q3+1.5IQR ll = q1-1.5IQR

df4 =df3[((df3['weight']>=ll)&(df3['weight']<=ul))] df4

df4.shape

<img width="276" alt="2 10" src="https://user-images.githubusercontent.com/93427345/191421710-aad50409-e824-4ad5-8c87-665de18fdbbb.png">
sns.boxplot(x="weight",data=df4) (4)(ii) For the data set height_weight.csv detect height outliers using IQR method sns.boxplot(x="height",data=df3)

q1 = df3['height'].quantile(0.25) q3 = df3['height'].quantile(0.75) print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1 ul = q3+1.5IQR ll = q1-1.5IQR

df5 =df3[((df3['height']>=ll)&(df3['height']<=ul))] df5

df5.shape

sns.boxplot(x="height",data=df5)

# OUTPUT

# (1)(2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe

# DATASET

![Screenshot 2023-04-08 091506](https://user-images.githubusercontent.com/120567837/230701811-8add8219-4dd7-4975-b829-eb8df55ad76b.png)

# DATA HEAD
 
 ![Screenshot 2023-04-08 091718](https://user-images.githubusercontent.com/120567837/230701878-b602ff0e-6d39-4f7f-836d-e26897d33742.png)
 # DATASET INFO
 
 ![Screenshot 2023-04-08 094532](https://user-images.githubusercontent.com/120567837/230702788-5af9e29b-7b47-4f96-9af1-6fc4954829df.png)

 # DATASET DESCRIBE
 
 ![Screenshot 2023-04-08 092443](https://user-images.githubusercontent.com/120567837/230702673-865a89c2-ad02-4799-afd5-2399fa7de9b1.png)

# NULL VALUES

![Screenshot 2023-04-08 095217](https://user-images.githubusercontent.com/120567837/230702970-86add89a-d198-40a1-88a5-0f6faa2537eb.png)

# DATASET SHAPE

![Screenshot 2023-04-08 095535](https://user-images.githubusercontent.com/120567837/230703034-54c6301f-bb88-4e9c-a7a7-14792a3a32c9.png)

# Box plot of price_per_sqft column with outliers

![Screenshot 2023-04-08 095628](https://user-images.githubusercontent.com/120567837/230703064-315b1a2a-d17f-4f7f-abf4-b7016c6d5a82.png)

# price_per_sqft - Dataset after removing outliers

![Screenshot 2023-04-08 095910](https://user-images.githubusercontent.com/120567837/230703137-0e11313c-87f9-4e1a-8813-6d237e8514ff.png)

# price_per_sqft - Shape of Dataset after removing outliers

![Screenshot 2023-04-08 100204](https://user-images.githubusercontent.com/120567837/230703212-8c2ed226-72f5-467d-b98f-6d2f5d5951f6.png)

# Box Plot of price_per_sqft column without outliers

![Screenshot 2023-04-08 100300](https://user-images.githubusercontent.com/120567837/230703236-4477a52b-444c-41e6-aa98-0cb31a356c28.png)

# Examine price_per_sqft column and use zscore of 3 to remove outliers. Dataset after removal of outlier using z score

![Screenshot 2023-04-08 100407](https://user-images.githubusercontent.com/120567837/230703264-5fc4f4cc-c3f4-47ab-b1b7-1ccbd44404b7.png)

# Shape of Dataset after removal of outlier using z score
![Screenshot 2023-04-08 100531](https://user-images.githubusercontent.com/120567837/230703309-7a1948ab-3cda-4fa8-a14e-c092fbc95f21.png)

# price_per_sqft column after removing outliers

![Screenshot 2023-04-08 100637](https://user-images.githubusercontent.com/120567837/230703357-4bc5777c-7326-41fa-a5b4-7ef9f5440d58.png)

# (4) For the data set height_weight.csv detect weight and height outliers using IQR method Dataset

![Screenshot 2023-04-08 100750](https://user-images.githubusercontent.com/120567837/230703385-c2b3b3fe-1be0-48ca-8b41-f8540b3388ec.png)

# Datahead

![Screenshot 2023-04-08 100904](https://user-images.githubusercontent.com/120567837/230703413-eafd9339-670a-496d-b36b-5788e8cf6d24.png)

# Dataset info

![Screenshot 2023-04-08 101112](https://user-images.githubusercontent.com/120567837/230703467-81e0b5a8-814f-4d75-86ea-2f89779cb6d0.png)

# Dataset describe

![Screenshot 2023-04-08 101242](https://user-images.githubusercontent.com/120567837/230703506-6676eb25-9826-42d7-b1b5-5586a790db78.png)

# Null values

![Screenshot 2023-04-08 101404](https://user-images.githubusercontent.com/120567837/230703561-7ff72986-2e8d-4e2d-8f40-53edb9eee061.png)

# Dataset Shape

![Screenshot 2023-04-08 101515](https://user-images.githubusercontent.com/120567837/230703589-0fcb7168-4d40-454d-ab55-ac6806b8e15e.png)

# Weight - With outlier

![Screenshot 2023-04-08 101607](https://user-images.githubusercontent.com/120567837/230703618-cff54014-c98a-41eb-8367-4cd175ad51e2.png)

# Weight - Dataset after removing Outliers using IQR method

![Screenshot 2023-04-08 101754](https://user-images.githubusercontent.com/120567837/230703669-d739ba70-0a73-47c9-995d-af8e0a3fa479.png)

# Weight - Shape of Dataset after removing Outliers using IQR method

![Screenshot 2023-04-08 101853](https://user-images.githubusercontent.com/120567837/230703697-5af139f5-1bbf-4f9f-badb-4c7d83dcb52a.png)

# Weight - Without Outliers using IQR method

![Screenshot 2023-04-08 102014](https://user-images.githubusercontent.com/120567837/230703737-2ac3d9de-dd6f-4e9c-b1f4-d79f6a7c3f53.png)

# Height - With outliers

![Screenshot 2023-04-08 102122](https://user-images.githubusercontent.com/120567837/230703776-a4caa39e-86b6-45e0-a865-83dc069a23d4.png)

# Height - Dataset after removing Outliers using IQR method

![Screenshot 2023-04-08 102232](https://user-images.githubusercontent.com/120567837/230703809-b9b5eb9d-39fb-4b98-b893-2dddc2abafdc.png)

# Height - Shape of Dataset after removing Outliers using IQR method

![Screenshot 2023-04-08 102344](https://user-images.githubusercontent.com/120567837/230703831-50407ca8-bcd3-40cf-bf1b-2597760177f2.png)

# Height - Without Outliers using IQR method

![Screenshot 2023-04-08 102502](https://user-images.githubusercontent.com/120567837/230703858-b07e7a40-d4d3-45e6-ba6c-4e2f6e5ac17b.png)

# RESULT
The given datasets are read and outliers are detected and are removed using IQR and z-score methods.

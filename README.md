# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
```
REGISTER NUMBER:212223040216
NAME:SURIYA RAJ K
```
```import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
df=pd.read_csv('drive/MyDrive/heights.csv')
print(df)

       name  height
0     mohan     5.9
1     maria     5.2
2     sakib     5.1
3       tao     5.5
4     virat     4.9
5    khusbu     5.4
6    dmitry     6.2
7    selena     6.5
8      john     7.1
9     imran    14.5
10     jose     6.1
11  deepika     5.6
12   yoseph     1.2
13    binod     5.5

```
```
pd.DataFrame(df)

	name	height
0	mohan	5.9
1	maria	5.2
2	sakib	5.1
3	tao	5.5
4	virat	4.9
5	khusbu	5.4
6	dmitry	6.2
7	selena	6.5
8	john	7.1
9	imran	14.5
10	jose	6.1
11	deepika	5.6
12	yoseph	1.2
13	binod	5.5
```
```
sns.boxplot(df)
```

![download](https://github.com/user-attachments/assets/0d7429a6-d9cd-49ab-91ec-ca9bf3f732a6)


```
sns.scatterplot(df)
```

![download](https://github.com/user-attachments/assets/bea4d1bf-a145-457e-8045-0f59063d0cf3)

```
Q1=df['height'].quantile(0.25)
Q3=df['height'].quantile(0.75)
IQR=Q3-Q1
print(IQR)

0.9249999999999998

lower_bound=Q1-1.5*IQR
upper_bound=Q3+1.5*IQR
print("lower bound:",lower_bound)
print("upper bound:",upper_bound)

lower bound: 3.8625000000000003
upper bound: 7.5625
```
```
 outliers = df[(df['height'] < lower_bound) | (df['height'] > upper_bound)]
 print(outliers)

     name  height
9    imran    14.5
12  yoseph     1.2

 print("Q1 = ", Q1)
 print("Q3 = ",Q3)
 print("IQR = ", IQR)
 print("Lower bound = ", lower_bound)
 print("Upper bound = ", upper_bound)
 print( outliers)

Q1 =  5.25
Q3 =  6.175
IQR =  0.9249999999999998
Lower bound =  3.8625000000000003
Upper bound =  7.5625
      name  height
9    imran    14.5
12  yoseph     1.2
```
```

new=df[(df['height'] > lower_bound) & (df['height'] < upper_bound)]
 print(new)

     name  height
0     mohan     5.9
1     maria     5.2
2     sakib     5.1
3       tao     5.5
4     virat     4.9
5    khusbu     5.4
6    dmitry     6.2
7    selena     6.5
8      john     7.1
10     jose     6.1
11  deepika     5.6
13    binod     5.5
```
```
sns.boxplot(new)
```

![download](https://github.com/user-attachments/assets/aeeb4c0f-d6b1-448e-8478-d3733e5b603d)


```
sns.scatterplot(new)
```

![image](https://github.com/user-attachments/assets/638b0fe8-dabd-4ae1-b0f4-b792a44e03e2)





# Result
 The given data has been used to perform data cleaning and saved the cleaned data to a file.
          

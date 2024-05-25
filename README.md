# Covid-19-Data-Analysis

```python

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import warnings
warnings.filterwarnings ('ignore')


#Data pre-pocesssing
#load the data using pandas read function
#print the dataset information
#print the statistics about the data using describe function 
#visualize the correlation map to understand the correlation with the columns.
#check for null values, and if the data contains any, remove them.
#additionally, inspect for duplicate values and remove them if present.

#load the dataset and print the top 5 rows
import pandas as pd
​
data = pd.read_csv(r"C:\Users\user\Documents\DATA ANALYTICS\COVID DATA -SEUN.csv")
data.head()
States Affected	No. of Cases (Lab Confirmed)	No. of Cases (on admission)	No. Discharged	No. of Deaths
0	Lagos	104,118	975	102,372	771
1	FCT	29,492	38	29,205	249
2	Rivers	18,093	48	17,890	155
3	Kaduna	11,603	4	11,510	89
4	Oyo	10,334	2	10,130	202

#about the dataset
​
data.info()
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 37 entries, 0 to 36
Data columns (total 5 columns):
 #   Column                        Non-Null Count  Dtype 
---  ------                        --------------  ----- 
 0   States Affected               37 non-null     object
 1   No. of Cases (Lab Confirmed)  37 non-null     object
 2   No. of Cases (on admission)   37 non-null     int64 
 3   No. Discharged                37 non-null     object
 4   No. of Deaths                 37 non-null     int64 
dtypes: int64(2), object(3)
memory usage: 1.6+ KB


#understanding the statistics in the dataset
data.describe().style.background_gradient(cmap='tab20c')
 	No. of Cases (on admission)	No. of Deaths
count	37.000000	37.000000
mean	94.594595	85.270270
std	199.791900	134.897008
min	-1.000000	2.000000
25%	2.000000	25.000000
50%	10.000000	38.000000
75%	67.000000	89.000000
max	975.000000	771.000000
#checking the correlaton matrix
plt.figure(figsize=(10,4))
sns.heatmap(data.corr(),annot=True,cmap='winter_r',fmt='.2f',linewidths=1)
plt.title('correlation map')
plt.show()

#data cleaning process
#checking the null values in the datasets
data.isna().sum()/len(data)*100
States Affected                 0.0
No. of Cases (Lab Confirmed)    0.0
No. of Cases (on admission)     0.0
No. Discharged                  0.0
No. of Deaths                   0.0
dtype: float64


#checking the percentage of the null values in the dataset
null_values=data.isna().sum()
total_shells=np.product(data.shape)
total_missing_values=null_values.sum()
percentage_missing_values=(total_missing_values/total_shells)*100
print(f'the dataset contains {percentage_missing_values} of values')
the dataset contains 0.0 of values

#checking the duplicate values in the dataset
duplicate=data.duplicated().sum()
print(f'there is {duplicate} values in the dataset')
​
there is 0 values in the dataset

# Check column names and data types
print(data.dtypes) 
States Affected                 object
No. of Cases (Lab Confirmed)    object
No. of Cases (on admission)      int64
No. Discharged                  object
No. of Deaths                    int64
dtype: object
#lets find number of the states affected in the dataset using the bar chart
​
data['States Affected'].value_counts().nlargest(10).plot(kind='bar', color=['#A9E2F3'])
​
plt.title('Top 10 states in the dataset')
plt.xlabel('states')
plt.xticks(rotation=90)
plt.ylabel('count of values')
plt.show()
```

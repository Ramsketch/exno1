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
# Import required libraries 
import pandas as pd 
import numpy as np 
from scipy import stats 
import seaborn as sns 
```

```
 
# Step 1: Read the Data 
# Replace 'your_data.csv' with your actual CSV file 
df = pd.read_csv('Data_set.csv')

```
```
 
# Step 3: Remove null values and display the sum of null values in each row 
df_null=df.isnull() 
df_null 
df_null_sum=df.isnull().sum() 
df_null_sum 
```
<img width="277" height="182" alt="image" src="https://github.com/user-attachments/assets/6b844922-48ab-448a-be8e-384e24bca633" />

```
   # Fill Null Values with Constant Value "O" 
df_nafill_0=df.fillna(0) 
df_nafill_0

```
<img width="994" height="367" alt="image" src="https://github.com/user-attachments/assets/2bcfc789-33a0-4437-b699-eb258d2b3c2e" />

```
# Fill Null Values with ffill Method 
df_ffill=df.ffill() 
df_ffill

```
<img width="977" height="329" alt="image" src="https://github.com/user-attachments/assets/01bbb1a1-c1c3-4283-8c0c-07d7b8485607" />

```
# Fill Null Values with bfill Method 
df_bfill=df.bfill() 
df_bfill

```
<img width="998" height="359" alt="image" src="https://github.com/user-attachments/assets/9dd3b9f9-3c7c-4529-bded-91fef011222a" />

```
# Calculate the mean value of a column and fill it with null values. 
df_mean1=df['num_episodes'].fillna(df['num_episodes'].mean()) 
df_mean1

```
<img width="374" height="216" alt="image" src="https://github.com/user-attachments/assets/57b24e9f-72e3-4303-8e09-d94d0742fd20" />

```
# Drop Null Values 
df_dropna=df.isnull().dropna() 
df_dropna

```
<img width="830" height="351" alt="image" src="https://github.com/user-attachments/assets/05da9da4-6d7d-4f83-90e5-7dc470f47a47" />

```
# Step 4: Save the clean data to a new file
df.to_csv('Loan_data.csv', index=False)

```
```
# Step 5: Remove Outliers using IQR Method 
ir=pd.read_csv('iris.csv') 
ir 
# Use Boxplot function to detect outlier 
sns.boxplot(ir) 
# Use Scatterplot function to detect outlier 
sns.scatterplot(ir) 
q1=ir.sepal_width.quantile(0.25) 
q3=ir.sepal_width.quantile(0.75) 
iqr=q3-q1 
print(iqr) 
rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))] 
rid['sepal_width']
delid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))] 
delid

```
<img width="430" height="349" alt="image" src="https://github.com/user-attachments/assets/683a2b43-7b7d-460c-b81e-056ca5bb00e3" />
<img width="558" height="422" alt="image" src="https://github.com/user-attachments/assets/adec7e72-853b-49c4-a8e5-7b5bfc177c0f" />

```
# Step 6: Remove Outliers using Z-score Method 
data=[1,12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,72,75,78,81,
84,87,90,93] 
df=pd.DataFrame(data) 
mean=np.mean(data) 
mean 
std=np.std(data) 
std 
z=np.abs(stats.zscore(df)) 
z 
threshold=3 
outliers = df[abs(df) > 3] 
print("Outliers:") 
print(outliers) 
# Remove outliers 
df_cleaned = df[(z <= threshold)] 
df_cleaned

```
<img width="174" height="545" alt="image" src="https://github.com/user-attachments/assets/2749952b-66a3-4dcc-b10c-9dfac2217cd1" />
<img width="143" height="610" alt="image" src="https://github.com/user-attachments/assets/7c1cca0c-4bc3-4096-bbc9-92e87662bb11" />


# Interpretation

1. The given dataset was loaded and its information was analyzed using Pandas.

2. Missing values were identified and handled using constant value, forward fill, backward fill, mean and dropna() methods.

3. The cleaned data was saved into a CSV file.

4. Outliers were detected using Boxplot and Scatterplot visualizations.

5. The IQR method was used to identify and remove outliers from the Iris dataset.

6. The Z-score method was applied with a threshold value of 3 to detect and remove outliers.

7. Thus, different data cleaning techniques were performed to improve data quality.


# Result

The given data has been cleaned successfully using data cleaning process.

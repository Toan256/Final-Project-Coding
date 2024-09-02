# Final Project Codes using Pandas
## Step 1: Import Pandas

import pandas as pd

## Step 2: Upload the cleaned Google Sheets File into Pandas

salary_GS='1v_P_q5EWeNMHFTpal7MgBTVpdouhhXRARNxMOcmCiWU'

df = pd.read_excel('https://docs.google.com/spreadsheets/d/' + salary_GS +'/export?format=xlsx',sheet_name='Trang tính1')

## Step 3: Conduct Statistcal Summary for numerical columns

print(df.describe())

## Step 4: Exploratory Data Analysis

**- View the first few rows of the data**

print(df.head())

**- View the last few rows of the data**

print(df.tail())

**- Get an overview of the DataFrame, including column names, data types, and non-null values**

print(df.info())

**- Check for any missing values in the dataset**

print(df.isnull().sum())

## Step 5: Checking Data distribution

**- Install additional required libraries**

import matplotlib.pyplot as plt

import seaborn as sns

**- Histogram for numerical columns**

df.hist(figsize=(10, 10), bins=20)

plt.show()

## Step 6: Correlation Analysis

**- Correlation matrix**

corr_matrix = df.corr()

corr_matrix

**- Displaying the correlation matrix using a heatmap**

plt.figure(figsize=(10, 8))

sns.heatmap(corr_matrix, annot=True, cmap='coolwarm', linewidths=0.5)

plt.show()

## Step 7: Linear Regression Model
**- Install additional required libraries**

import statsmodels.api as sm

**- Linear Regression**

X = df[['Age', 'Gender','Education Level','Years of Experience','level','field']]

y = df['Salary']

**- Add a constant to the predictor variable set to represent the intercept**

X = sm.add_constant(X)

**- Fit the model**

model = sm.OLS(y, X).fit()

**- View the model summary**

print(model.summary())

## Step 8: Autocorrelation Test

**- Install Durbin-Watson test** 

from statsmodels.stats.stattools import durbin_watson

**- Perform Durbin-Watson test**

dw_statistic = durbin_watson(model.resid)

print(f"Durbin-Watson statistic: {dw_statistic}")

## Step 9: Rerun General Least Square

**- Import GLS**

from statsmodels.regression.linear_model import GLS

**- Fit the GLS model**

gls_model = GLS(y, X).fit()

**- View the model summary**

print(gls_model.summary())

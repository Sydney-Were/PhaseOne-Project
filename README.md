
# AVIATIONDATA ANALYSIS

Our company is expanding in to new industries to diversify its portfolio. I will thereby translate my findings into actionable insights that the head of the new aviation division can use to help decide which aircraft to purchase.

In this project, I will focus on data cleaning, imputation, analysis, and visualization to derive valuable insights for a business stakeholder.

## The dataset

https://www.kaggle.com/datasets/khsamaha/aviation-accident-database-synopses
## Language used 
Python.

# The libraries used
## IMPORTING ALL NECESSARY LIBRARIES.
1. import pandas as pd
2. import numpy as np 
3. import matplotlib.pyplot as plt
4. import seaborn as sns
# To ignore warnings
1. import warnings
2. %matplotlib inline

# loading the data
df = pd.read_csv("AviationData.csv",encoding = 'Windows-1252')

# sanity checks
- df.shape
- df.tail()
- df.columns
- df.describe()
- df.describe(include="object")
- df.info()
- df.isna().sum()
- df.isna().sum()/len(df)*100

# Cleaning 
- cleaned_df = df.drop(columns=columns_dropped)
- cleaned_df.head()
- cleaned_df.duplicated()
- duplicate_count = cleaned_df.duplicated().sum()
 
# analysis
def aircraft_category(value):
    if pd.isna(value) or value.strip() == "":
        return "Unknown"
    return value.strip().title()

for column in cleaned_df.columns:
    if cleaned_df[column].dtype == 'object':
        #Categorical value filled with the most frequent value(mode)
        cleaned_df[column] = cleaned_df[column].fillna(cleaned_df[column].mode()[0])
    else:
        #Numerical value filled with median
        cleaned_df[column] = cleaned_df[column].fillna(cleaned_df[column].median())


- cleaned_df['Make'] = cleaned_df['Make'].str.upper()

# visualization
event_counts = cleaned_df.groupby('Make')['Event.Id'].nunique().sort_values(ascending=False)
plt.figure(figsize=(12,6))
top_makes.plot(kind='bar', color='skyblue')

plt.title('Number of Events per Aircraft Make')
plt.xlabel('Aircraft Make')
plt.ylabel('Number of Events')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()

# Presentation pdf
presentation pdf can be accessed through this link(https://docs.google.com/presentation/d/1TECMOduZlYuVE7jGFL1-mTtRlU6WAsm0/edit?usp=drive_link&ouid=114562565227732877556&rtpof=true&sd=true)

# More representations on tableau
https://public.tableau.com/app/profile/sydney.were/viz/Aviationvisualization/Story1?publish=yes

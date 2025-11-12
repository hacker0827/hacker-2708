import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
from scipy.stats import skew

df=pd.read_csv("D:\Devl\slip14 DB.csv")
print(df.head())
print(df.tail())
print(df.info())
print(df.describe())

print("\nCentral Tendency of Age Distribution : ")
print("Mean : ",df['age'].mean())
print("Median ; ",df['age'].median())
print("Mode : ",df['age'].mode())

sc=skew(df['age'])
print(sc)

kt=df['age'].kurtosis()
print(kt)

plt.figure(figsize=(8,6))
sns.boxplot(df['age'])
plt.title("Outliers / Patterns in Age Distribution before Handling ")
plt.show()

Q1 = df['age'].quantile(0.25)
Q3 = df['age'].quantile(0.75)
IQR = Q3 - Q1

lower=Q1 - 1.5 * IQR
upper = Q3 + 1.5 * IQR

df['age']=df['age'].clip(lower,upper)

plt.figure(figsize=(8,6))
sns.boxplot(df['age'])
plt.title("Outliers / Patterns in Age Distribution after Handling ")
plt.show()

avg_age_region = df.groupby(df['native-country'])['age'].mean()
plt.figure(figsize=(9,7))
avg_age_region.plot(kind="bar", color="pink")
plt.title("Age distribution across different Regions")
plt.xlabel("Region / Groups")
plt.ylabel("Age")
plt.show()

plt.figure(figsize=(8,6))
sns.histplot(df['age'], bins=10, color="yellow")
plt.title("Age Distribution")
plt.xlabel("Age")
plt.ylabel("Count")
plt.show()

plt.figure(figsize=(9,6))
sns.scatterplot(x="age", y="marital-status", data=df, color="green")
plt.title("Age Distribution accordign to Marital Status")
plt.xlabel("AGE")
plt.ylabel("Marital Status")
plt.show()


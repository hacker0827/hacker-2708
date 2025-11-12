import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df=pd.read_csv("D:\Devl\Titanic DB slip12.csv")
print(df.head(10))
print("Column Name and data types :")
print(df.dtypes)

print("\nMissing Values ")
print(df.isnull().sum())

print("\nColumns with most missing data")
print(df.isnull().sum().sort_values(ascending=False).head())

bins=[0,12,18,35,50,80]
labels=["Child","Teen","Young Adult","Adult","Senior"]
df['AgeGroup']=pd.cut(df['Age'], bins=bins, labels=labels)

avg_age=df.groupby('AgeGroup')['Survived'].mean()
plt.figure(figsize=(8,6))
avg_age.plot(kind="bar", color="pink")
plt.title("Survival rate across different age groups")
plt.xlabel("Survival rate")
plt.ylabel("Age Group")
plt.show()

avg_pclass=df.groupby('Pclass')['Survived'].mean()
plt.figure(figsize=(7,6))
avg_pclass.plot(kind="bar", color="yellow")
plt.title("Pclass survivals : ")
plt.show()

plt.figure(figsize=(9,6))
sns.heatmap(df.corr(numeric_only=True), annot=True, cmap="coolwarm")
print("Correlation Heatmap")
plt.show()
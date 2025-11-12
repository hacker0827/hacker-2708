import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df=sns.load_dataset("titanic")

print("-------HEAD-------")
print(df.head())

print("\n-------TAIL-------")
print(df.tail())

print("\nSHAPE : ",df.shape)
print("\nColumn Names : ")
print(df.columns)

print("\n------DESCRIBE------")
print(df.describe())

print("\nMissing values present in each column : ")
print(df.isnull().sum())

df["age"].fillna(df["age"].mean() , inplace=True)
df["deck"]=df["deck"].astype(object)
df["deck"].fillna("Unknown" , inplace=True)

print("\nMissing Values After Handling : ")
print(df.isnull().sum())

plt.boxplot(df['fare'])
plt.title("Boxplot Before Handling Outliers : ")
plt.ylabel("FARE")
plt.show()

Q1 = df['fare'].quantile(0.25)
Q3 = df['fare'].quantile(0.75)
IQR = Q3-Q1

lower_limit = Q1-1.5*IQR
upper_limit = Q3 + 1.5 *IQR

df['fare']=df['fare'].clip(lower_limit, upper_limit)

plt.boxplot(df['fare'])
plt.title("Bosplot After Handling Outliers : ")
plt.ylabel("FARE")
plt.show()

print("\nData Cleaned Successfully\n")


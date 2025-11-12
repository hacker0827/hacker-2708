import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df=pd.read_csv("D:\Devl\slip11 DB.csv")

print("SUMMARY")
print(df.describe())

print("Missing Values ")
print(df.isnull().sum())
df.fillna(df.median(numeric_only=True), inplace=True)

plt.hist(df['price'], bins=10, edgecolor="black")
plt.title("Distribution Of House Prices")
plt.xlabel("Prices")
plt.ylabel("Counts")
plt.show()

plt.figure(figsize=(10,8))
sns.regplot(x='sqft_living', y='price', data=df, line_kws={'color':'red'})
plt.title("Relationship b/w Square fit Living and Price ")
plt.show()

avg_house_price = df.groupby("zipcode")['price'].mean()
plt.figure(figsize=(12,6))
avg_house_price.plot(kind='bar', color='lightgreen')
plt.title("Zipcode and avg house price")
plt.show()

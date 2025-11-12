import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df = sns.load_dataset("tips")

plt.figure(figsize=(8,6))
sns.histplot(df['total_bill'], bins=20, kde=True, color="skyblue")
plt.title("Total Bill using histogram")
plt.show()

plt.figure(figsize=(7,5))
sns.kdeplot(df['tip'], fill=True, color="orange")
plt.title("Tips using Kernel Density Estimate Plot")
plt.show()

plt.figure(figsize=(9,7))
sns.scatterplot(x="total_bill", y="tip", data=df, color="Yellow")
plt.title("Total Bill and tip using Scatterplot")
plt.show()

plt.figure(figsize=(8,8))
sns.boxplot(x="total_bill",y="day", data=df)
plt.title("Total Bill Across each Day")
plt.xlabel("Total Bill")
plt.ylabel("Day")
plt.show()

plt.figure(figsize=(9,5))
sns.heatmap(df.corr(numeric_only=True),annot=True, cmap="coolwarm")
plt.title("Correlation matrix for numeric variables in the dataset")
plt.show()
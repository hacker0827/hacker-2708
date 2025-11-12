import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df=pd.read_csv("D:\Devl\Student DB slip10.csv")
print("------HEAD------")
print(df.head())

print("------TAIL------")
print(df.tail())

print("------INFO------")
print(df.info())

print("------DESCRIBE------")
print(df.describe())

print("------SHAPE------")
print(df.shape)

print("------COLUMN NAME------")
print(df.columns)

print("------MISSING VALUES------")
print(df.isnull().sum())

plt.figure(figsize=(8,6))
sns.histplot(df['GradeID'], kde=True, color="skyblue")
sns.histplot(df['SectionID'], kde=True, color="green")
sns.histplot(df['Topic'], kde=True, color="pink")
plt.title("Distribution Of Grades")
plt.xlabel("SCORES")
plt.ylabel("No. of Students")
plt.legend()
#plt.show()

plt.figure(figsize=(6,5))
sns.heatmap(df.corr(numeric_only=True), annot=True, cmap='viridis')
plt.title("Correlations Between Subjects ")
plt.show()

plt.figure(figsize=(7,5))
sns.countplot(x="StudentAbsenceDays", hue="Class", data=df)
plt.title("\nImpact of attendance on Performance")
plt.xlabel("Absence Days")
plt.ylabel("Count")
plt.show()
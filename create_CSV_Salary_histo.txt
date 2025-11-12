import pandas as pd
import matplotlib.pyplot as plt

df=pd.read_csv("D:\Devl\slip7.csv")

print("-----MISSING VALUES IN DATASET-----")
print(df.isnull().sum())
df["Salary"].fillna(df["Salary"].mean(),inplace=True)

print("\n-------SALARY STATISTICS-------\n")
print(df['Salary'].describe())
plt.hist(df['Salary'], bins=5, edgecolor = 'Black')
plt.title("\nSALARY STATISTICS\n")
plt.xlabel("SALARY")
plt.ylabel("Frequency")
plt.show()

avg_dept_sal = df.groupby('Dept')['Salary'].mean()
print("\nAverage Salary in each Department : ")
print(avg_dept_sal)

highest_avg = avg_dept_sal.idxmax()
print("\nHIGHEST AVERAGE SALARY OF ALL DEPARTMENTS : ",highest_avg)
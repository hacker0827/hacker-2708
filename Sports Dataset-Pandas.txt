import pandas as pd
df=pd.read_csv("D:\Devl\cbb.csv")
print("\nTask 1]")
print("1st 5 records in dataframe : ")
print(df.head())
print("last 5 records in dataframe : ")
print(df.tail())

print("\nTask 2]")
print("No. of Records in the dataset(Rows,Columns) : ",df.shape)

print("\nTask 3]")
print("\nNo. of Missing values in each column : ")
print(df.isnull().sum())

print("\nTask 4]")
print("Maximum value present in Each column : ", df.max(numeric_only=True))

print("\nTask 5]")
for col in df.columns:
  print(f"\nColumn : {col} ")
  print(df[col].unique())

print("\nTask 6]")
print("Number of Unique Values in each Column : ",df.nunique())

print("\nTask 7]")
for col in df.columns:
  print(f"\nColumn : {col} ")
  print(df[col].value_counts())
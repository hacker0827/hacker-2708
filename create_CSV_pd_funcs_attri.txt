import pandas as pd
df=pd.read_csv("D:\Devl\slip6.csv")

print("\n-----HEAD-----")
print(df.head())

print("\n-----TAIL-----")
print(df.tail())

print("-----INFO-----")
print(df.info())

print("-----DESCRIBE-----")
print(df.describe())

print("-----ATTRIBUTES------")
print("\nDATA TYPES : ",df.dtypes)
print("\nShape : ",df.shape)

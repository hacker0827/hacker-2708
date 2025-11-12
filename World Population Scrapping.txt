import pandas as pd
import requests

url = "https://en.wikipedia.org/wiki/World_population"
headers={"User-Agent":"Mozilla/5.0(Windows NT 10.0; Win64 ; x64)"}      #to look like a real browser
response = requests.get(url, headers=headers)
tables = pd.read_html(response.text)

print("\nNumber of Tables : ",len(tables))

print("*********************TABLES FOUND*********************")
for table in tables:
    print(table.head())
    print("\n")

table1 = tables[0]
print("\nTables Info : ")
print(table1.info())

print("\nTable Description : ")
print(table1.describe())

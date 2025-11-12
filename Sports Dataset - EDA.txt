import pandas as pd

url = "https://raw.githubusercontent.com/selva86/datasets/master/NCAABasketballGames1985_2016.csv"
df = pd.read_csv(url)


print("\nFirst 5 Records from the table")
print(df.head())

print("Object Columns in Dataset : ")
for column in df.columns:
    if df[column].dtype=='object':
        print(column)

win150=df[df['WScore']>150]
print("Winning teams that scored more than 150 points ")
print(win150[['Season','Wteam','LTeam','WScore','LScore']])

winLose = df[df['WScore']>150 & df['LScore']<100]
print("Winning teams that scored more than 150 points and when the losing teams scored below 100")
print(winLose[['Season','WTeam','LTeam','WScore','LScore']])

games_played = df.groupby('Season').size()
print("\nGames Played in each Season : ")
print(games_played)

avg_win_score = df.groupby("WTeam")['WScore'].mean().sort_values(ascending=False)
print("\nAverage Winning Score for each Team : ")
print(avg_win_score)

if 'WLoc' in df.columns:
    print("Games Won by location : ")
    print(df['WLoc'].value_counts())
else:
    print("\nNo 'WLoc' column found!!!")

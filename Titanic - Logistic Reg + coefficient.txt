import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score, roc_auc_score
from sklearn.linear_model import LogisticRegression

df=sns.load_dataset("titanic")
print(df.head())

print("\nMissing Values ")
print(df.isnull().sum())

#preprocessed data
df=df[['survived', 'pclass','age','sex','fare']]
df['age'] = df['age'].fillna(df['age'].mean())
df['sex'] = df['sex'].map({'male':0, 'female': 1})
df.dropna(inplace=True)

print("\nMissing Values After processing : ")
print(df.isnull().sum())

X = df[['pclass','sex','age','fare']]
y = df['survived']

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=0)

model = LogisticRegression()
model.fit(X_train,y_train)
y_pred = model.predict(X_test)

print("\nAccuracy Score : ",accuracy_score(y_test,y_pred))
print("\nPrecision Score : ",precision_score(y_test,y_pred))
print("\nRecall Score : ",recall_score(y_test,y_pred))
print("\nF1 Score : ",f1_score(y_test,y_pred))
print("\nROC AUC Score : ",roc_auc_score(y_test,y_pred))

coef = pd.Series(model.coef_[0], index=X.columns)
coef.plot(kind="bar", color="blue")
plt.title("Coefficients of Trained Model ")
plt.show()

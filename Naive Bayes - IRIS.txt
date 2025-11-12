import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split
from sklearn.naive_bayes import GaussianNB
from sklearn.metrics import accuracy_score, confusion_matrix

iris=load_iris()
X = iris.data
Y = iris.target

X_train, X_test, y_train, y_test = train_test_split(X, Y, test_size=0.2, random_state=0)

model= GaussianNB()
model.fit(X_train, y_train)
y_pred=model.predict(X_test)

print("\nAccuracy Score : ",accuracy_score(y_test, y_pred))
print("\nConfusion Matrix : ",confusion_matrix(y_test, y_pred))

plt.figure(figsize=(7,5))
sns.heatmap(confusion_matrix(y_test,y_pred), annot=True, cmap="coolwarm")
plt.title("Predicted & Actual Values (Confusion Matrix) : ")
plt.xlabel("Predicted")
plt.ylabel("Actual")
plt.show()
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.datasets import load_wine
from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score, confusion_matrix
from sklearn.naive_bayes import GaussianNB
from sklearn.preprocessing import StandardScaler
from sklearn.model_selection import train_test_split

wine = load_wine()
X = wine.data
Y = wine.target

scaler = StandardScaler()
x_scaled = scaler.fit_transform(X)

X_train, X_test, y_train, y_test = train_test_split(x_scaled, Y, test_size=0.2, random_state=0)

model = GaussianNB()
model.fit(X_train, y_train)
y_pred =  model.predict(X_test)

print("\nAccuracy Score : ", accuracy_score(y_test, y_pred))
print("Precision Score : ", precision_score(y_test, y_pred, average='macro'))
print("Recall Score : ",recall_score(y_test, y_pred, average='macro'))
print("F1 Score : ",f1_score(y_test, y_pred, average='macro'))

plt.figure(figsize=(9,6))
sns.heatmap(confusion_matrix(y_test,y_pred), annot=True, cmap = "coolwarm")
plt.title("Confusion Matrix : Gaussian Naive Bayes on Wine Dataset")
plt.xlabel("Predicted")
plt.ylabel("Actual")
plt.show()
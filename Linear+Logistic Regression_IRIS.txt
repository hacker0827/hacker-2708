import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.linear_model import LinearRegression, LogisticRegression
from sklearn.metrics import accuracy_score, mean_squared_error, confusion_matrix
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split

iris=load_iris()
X = iris.data
Y = iris.target

X_train,X_test,y_train,y_test = train_test_split(X, Y, test_size=0.2, random_state = 0)

Li_model = LinearRegression()
Li_model.fit(X_train, y_train)
pred_y = Li_model.predict(X_test)

print("\nLinear Regression result : ")
print("Mean Squared Error : ",mean_squared_error(y_test,pred_y))

plt.figure(figsize=(8,6))
sns.scatterplot(x=y_test, y=pred_y, color="pink")
plt.title("\nLinear Regression : Predicted VS Actual ")
plt.ylabel("Predicted")
plt.xlabel("Actual")
plt.show()

Lo_model = LogisticRegression(max_iter=200)
Lo_model.fit(X_train,y_train)
y_pred=Lo_model.predict(X_test)

print("\nLogistic Regression Result : ")
print("Accuracy Score : ", accuracy_score(y_test,y_pred))

plt.figure(figsize=(8,7))
sns.heatmap(confusion_matrix(y_test,y_pred), annot=True, cmap="coolwarm")
plt.title("Logistic Regression : Actual VS Predicted")
plt.xlabel("Actual")
plt.ylabel("Predicted")
plt.show()


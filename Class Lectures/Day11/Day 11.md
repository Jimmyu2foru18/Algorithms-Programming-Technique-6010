# K-Nearest Neighbors: Regression & Classification

---

## 1. Dataset Preparation: Tips Dataset

Supervised learning focuses on building models that map input features ($X$) to a target output ($Y$). In Day 11, we work with the **tips dataset** from Seaborn.

### One-Hot Encoding

Categorical columns (`sex`, `smoker`, `day`, `time`) are converted to dummy variables using `pd.get_dummies`:

```python
df_encoding = pd.get_dummies(tips, columns=['sex', 'smoker', 'day', 'time'], drop_first=True, dtype=int)
```

### Feature Correlation Heatmap

A heatmap visualizes the correlation between all features to identify which ones most strongly predict the tip amount:

```python
corr = df_encoding.corr()
sns.heatmap(corr, annot=True, fmt='.2f')
```

---

## 2. Linear Regression on Tips

A simple linear regression predicts tip amount from total bill:

```python
x = df_encoding['total_bill'].values.reshape(-1, 1)
y = df_encoding['tip'].values.reshape(-1, 1)

linear_model = LinearRegression().fit(xtrain, ytrain)
linear_model.score(xtest, ytest)
```

### Scenario: 3 People Ordering Burgers

Predict the tip for a table of 3 with a total bill of $36.00, encoded features passed to the trained model:

```python
burger_price = 12.0
total_bill = burger_price * 3
row = {
    "total_bill": total_bill,
    "size": 3,
    "sex_Female": 1,
    "smoker_No": 1,
    "day_Fri": 0,
    "day_Sat": 0,
    "day_Sun": 0,
    "time_Dinner": 1,
}
X_new = np.array([[row[c] for c in ["total_bill","size","sex_Female","smoker_No","day_Fri","day_Sat","day_Sun","time_Dinner"]]])
pred_tip = linear_model.predict(X_new)
print("Predicted tip:", round(float(pred_tip[0][0]), 2))
```

---

## 3. KNN Regression

K-Nearest Neighbors regression predicts tip using the same features:

```python
from sklearn.neighbors import KNeighborsRegressor

knn_model = KNeighborsRegressor(n_neighbors=5).fit(xtrain, ytrain)
knn_model.score(xtest, ytest)

knn_pred = knn_model.predict(X_new)
print("KNN predicted tip:", round(float(knn_pred[0][0]), 2))
```

Actual vs predicted tip values are plotted to visualize regression performance:

```python
plt.scatter(ytest, knn_model.predict(xtest), alpha=0.6)
plt.plot([ytest.min(), ytest.max()], [ytest.min(), ytest.max()], 'r--')
```

---

## 4. KNN Classification: Iris Dataset

The iris dataset is used to classify flower species using KNN.

### Encoding Species Labels

Species names are encoded as numeric labels:

```python
from sklearn.preprocessing import LabelEncoder
le = LabelEncoder()
iris["species_encoded"] = le.fit_transform(iris["species"])

X_iris = iris[["sepal_length", "sepal_width", "petal_length", "petal_width"]].values
y_iris = iris["species_encoded"].values.reshape(-1, 1)

xtrain_i, xtest_i, ytrain_i, ytest_i = train_test_split(X_iris, y_iris, test_size=0.2, random_state=42)
```

### KNN Classifier & Evaluation

```python
from sklearn.neighbors import KNeighborsClassifier
from sklearn.metrics import accuracy_score, confusion_matrix

knn_clf = KNeighborsClassifier(n_neighbors=5).fit(xtrain_i, ytrain_i)
acc = accuracy_score(ytest_i, knn_clf.predict(xtest_i))
print("KNN accuracy:", round(acc, 4))

cm = confusion_matrix(ytest_i, knn_clf.predict(xtest_i))
print("\nConfusion Matrix:\n", cm)
```

### Predicting a New Flower

A new flower (5.1, 3.5, 1.4, 0.2) is classified:

```python
new_flower = np.array([[5.1, 3.5, 1.4, 0.2]])
pred_species = knn_clf.predict(new_flower)
print("Predicted species:", le.inverse_transform(pred_species)[0])
```

---

## 5. Distance & Nearest Neighbors

### Euclidean Distance

Distance from each test sample to the new flower is computed row by row:

```python
from scipy.spatial.distance import euclidean

distances = np.array([euclidean(x, new_flower[0]) for x in xtest_i])
```

### Finding Nearest Neighbors

`np.argsort` ranks test samples by distance to identify the 5 nearest neighbors:

```python
nearest_idx = np.argsort(distances)[:5]
print("Indices of 5 nearest neighbors:", nearest_idx)
```

### Actual vs Predicted & Accuracy

A DataFrame compares actual and predicted species for the test set, with mismatches counted:

```python
actual = le.inverse_transform(ytest_i.flatten())
predicted = le.inverse_transform(knn_clf.predict(xtest_i).flatten())

results = pd.DataFrame({"Actual": actual, "Predicted": predicted})
mismatch = results["Actual"] != results["Predicted"]
print("Total mismatches:", mismatch.sum(), "out of", len(results))

acc_score = accuracy_score(ytest_i, knn_clf.predict(xtest_i))
print("Accuracy score:", round(acc_score, 4))
```

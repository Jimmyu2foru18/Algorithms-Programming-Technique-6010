# NumPy Arrays, Matrices & KNN Distance

---

## 1. Setup & Iris Dataset

Day 12 begins by loading the iris dataset, splitting into training and testing sets, and exploring the feature space:

```python
import seaborn as sns
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np

irisDF = sns.load_dataset("iris")

X = irisDF[['sepal_length', 'sepal_width', 'petal_length', 'petal_width']]
Y = irisDF['species']

Xtrain, Xtest, ytrain, ytest = train_test_split(X, Y, test_size=0.20, random_state=42)
```

- **Target ($Y$):** Species
- **Features ($X$):** sepal_length, sepal_width, petal_length, petal_width

To display all rows and columns without truncation:

```python
pd.set_option("display.max_rows", None)
pd.set_option("display.max_columns", None)
print(X)
```

---

## 2. Manual Euclidean Distance: KNN Examples

Two query points (`q1`, `q2`) are compared against two training points (`t1`, `t2`) using the Euclidean distance formula:

```python
q1 = np.array([5.6, 3.0, 4.5, 1.5])
q2 = np.array([6.7, 3.0, 5.2, 2.3])
t1 = np.array([7.0, 3.2, 4.7, 1.4])
t2 = np.array([6.4, 3.2, 4.5, 1.5])
```

For each query → training pair, the code prints the differences, squared differences, sum of squares, and final distance:

| Query → Train | Sum of Squares | Distance |
|--------------|---------------|----------|
| q1 → t1 | 2.05 | 1.43 |
| q1 → t2 | 0.68 | 0.83 |
| q2 → t1 | 1.19 | 1.09 |
| q2 → t2 | 1.26 | 1.12 |

**Result:** Since q1 is closest to t2 and q2 is closest to t1, KNN classification is likely **virginica**.

---

## 3. Example Toy Data

### Arrays

```python
arr1 = np.array([1, 2, 3, 4])
arr2 = np.array([5, 6, 7, 8])
```

### Matrix

```python
matrix = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
```

### Euclidean Distance

```python
distance = np.sqrt(np.sum((arr1 - arr2) ** 2))
```

### Sum

```python
total_sum = np.sum(matrix)
```

### Row-wise Sum

```python
row_sums = np.sum(matrix, axis=1)
```

Loop version:

```python
for i, row in enumerate(matrix):
    print(f"Row {i}: sum = {np.sum(row)}")
```

### For Loop

```python
for i in range(5):
    print(i)
```

### List Comprehension

```python
list_comp = [x ** 2 for x in range(10)]
```

---

## 4. Broadcasting

Broadcasting allows NumPy to perform operations between arrays of different shapes:

| Operation | Code | Effect |
|-----------|------|--------|
| Scalar + array | `arr1 + 10` | Adds 10 to every element |
| 1D array + matrix | `matrix + np.array([100, 200, 300])` | Adds per-column across every row |
| Column vector + matrix | `matrix + np.array([[10], [20], [30]])` | Adds per-row across every column |
| Matrix × scalar | `matrix * 2` | Multiplies every element by 2 |

---

## 5. Finding Nearest Neighbors with Xtest

### Using `argpartition` (faster than full sort)

Partitions distances so the k smallest are at the front, then sorts just those k:

```python
query = Xtest.values[0]

dists = np.sqrt(np.sum((Xtest.values - query) ** 2, axis=1))

k = 3
nearest_idx = np.argpartition(dists, k)[:k]
nearest_idx = nearest_idx[np.argsort(dists[nearest_idx])]

print("Nearest neighbor indices:", nearest_idx)
print("Distances:", dists[nearest_idx])
print("Labels:", ytest.values[nearest_idx])
```

### Manual for-loop distance

Computes distance to each test row one at a time:

```python
query = Xtest.values[0]

for i, row in enumerate(Xtest.values):
    diff = row - query
    sq = diff ** 2
    s = np.sum(sq)
    d = np.sqrt(s)
    print(f"Row {i}: diffs={diff}, sq={sq}, sum={round(s,2)}, dist={round(d,2)}")
```

### Using `argsort`

Ranks all test rows by distance:

```python
dists = np.sqrt(np.sum((Xtest.values - query) ** 2, axis=1))
sorted_idx = np.argsort(dists)
```

Top 5 nearest:

```python
k = 5
for i in sorted_idx[:k]:
    print(f"  Index {i}: dist={round(dists[i], 2)}, label={ytest.values[i]}")
```

### Print all rows without truncation

```python
print("All rows sorted by distance (no truncation):")
print(f"{'Rank':<5} {'Index':<8} {'Distance':<10} {'Label':<12} {'Features'}")
print("-" * 70)
for rank, i in enumerate(sorted_idx):
    print(f"{rank:<5} {i:<8} {round(dists[i], 2):<10} {ytest.values[i]:<12} {Xtest.values[i]}")
```

### Index lookup

`argsort` returns positions within Xtest (0–29). To get original iris dataset indices:

```python
original_idx = Xtest.index[sorted_idx]
print(original_idx)  # e.g., [71, 104, 12, ...]
```

Get features and label of the nearest neighbor:

```python
i = sorted_idx[0]
features = Xtest.values[i]
label = ytest.values[i]
print("Features:", features)
print("Label:", label)
```

---

## 6. Row-wise Sums for Xtrain & Xtest

```python
# Xtrain row sums (120 rows)
xtrain_row_sums = np.sum(Xtrain.values, axis=1)
print("Xtrain row sums (first 10):", xtrain_row_sums[:10])

# Xtest row sums (30 rows)
xtest_row_sums = np.sum(Xtest.values, axis=1)
print("Xtest row sums:", xtest_row_sums)
```

---

## 7. Partitioning Xtrain into Groups of 3

Xtrain is partitioned into groups of 3 rows, and each partition's features are summed:

```python
partition_size = 3
n_partitions = len(Xtrain) // partition_size

partitioned = Xtrain.values[:n_partitions * partition_size].reshape(n_partitions, partition_size, -1)
partition_sums = np.sum(partitioned, axis=1)
```

### Finding the partition for a specific index

The 71st value (index 70) falls into partition `70 // 3 = 23`:

```python
target_idx = 70
partition_num = target_idx // partition_size
print(f"Index {target_idx} is in partition {partition_num}")
print(f"Partition {partition_num} sum:", partition_sums[partition_num])
print(f"Partition {partition_num} rows:", partitioned[partition_num])
```

View partition 3 specifically:

```python
print("Partition 3 rows:", partitioned[3])
print("Partition 3 sum:", partition_sums[3])
```

### Partition 0: features and labels

```python
partition_0_rows = [0, 1, 2]
for i in partition_0_rows:
    print(f"  Row {i}: features={Xtrain.values[i]}, label={ytrain.values[i]}")
```

### Locating versicolor in ytrain

```python
first_versicolor = np.where(ytrain.values == 'versicolor')[0][0]
print(f"First versicolor at index: {first_versicolor}")
print(f"Partition: {first_versicolor // 3}")
print(f"Features: {Xtrain.values[first_versicolor]}")
print(f"Label: {ytrain.values[first_versicolor]}")
```

---

## 8. Summary

| Concept | Code | Purpose |
|---------|------|---------|
| Arrays | `np.array([...])` | 1-D data storage |
| Matrix | `np.array([[...]])` | 2-D data storage |
| Distance | `np.sqrt(np.sum((a-b)**2))` | Euclidean distance |
| Sum | `np.sum(matrix)` | Total or row-wise (axis=1) |
| Loop | `for i in range(n)` | Iteration |
| List Comprehension | `[x**2 for x in range(n)]` | Concise list creation |
| Broadcasting | `matrix + vector` | Operations across different shapes |
| argpartition | `np.argpartition(dists, k)` | Fast top-k nearest indices |
| argsort | `np.argsort(dists)` | Full ranking of distances |
| Row-wise sum | `np.sum(arr, axis=1)` | Sum each row separately |
| Partitioning | `.reshape(n, 3, -1)` | Group rows into fixed-size blocks |

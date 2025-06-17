#Matrix #InPlaceModification
similar question [[1886. Determine Whether Matrix Can Be Obtained By Rotation]]

You are given an `n x n` 2D `matrix` representing an image, rotate the image by **90** degrees (clockwise).

You have to rotate the image [**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm), which means you have to modify the input 2D matrix directly. **DO NOT** allocate another 2D matrix and do the rotation.

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/08/28/mat1.jpg)

```**Input:** matrix = [[1,2,3],[4,5,6],[7,8,9]]
**Output:** [[7,4,1],[8,5,2],[9,6,3]]
```

**Example 2:**

![](https://assets.leetcode.com/uploads/2020/08/28/mat2.jpg)

```**Input:** matrix = [[5,1,9,11],[2,4,8,10],[13,3,6,7],[15,14,12,16]]
**Output:** [[15,13,2,5],[14,3,4,1],[12,6,8,9],[16,7,10,11]]
```

**Constraints:**

- `n == matrix.length == matrix[i].length`
- `1 <= n <= 20`
- `-1000 <= matrix[i][j] <= 1000`

---
---
# Solution


track position of eah element before and after 90 degree rotation 
-
That's the spirit, Nav — **brute to optimal with solid intuition** is how true mastery is built. Let's tackle **LeetCode 48 – Rotate Image** step-by-step.

---

## 🔴 Problem:

You are given an `n x n` 2D matrix (square matrix) representing an image.  
**Rotate the image by 90 degrees (clockwise).**  
**Do it _in-place_** — modify the input matrix directly.

---

## 🧠 Step 1: Brute Force (with Extra Space)

### 🔧 Idea:

Use an extra `n x n` matrix.
Simple idea but its forbidden
--
For each element at `(i, j)` in the original matrix, place it at `(j, n - 1 - i)` in the rotated matrix.

### ✅ Intuition:

You're rotating the matrix **layer by layer**, shifting rows to columns — turning the **top row into the rightmost column**, and so on.

### 🧪 Example:

```
Original:
1 2 3
4 5 6
7 8 9

After Rotation:
7 4 1
8 5 2
9 6 3
```

### 🚀 Code (Java):

```java
public void rotate(int[][] matrix) {
    int n = matrix.length;
    int[][] copy = new int[n][n];

    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            copy[j][n - 1 - i] = matrix[i][j];
        }
    }

    // Copy back to original matrix
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            matrix[i][j] = copy[i][j];
        }
    }
}
```

### 📊 Time: O(n²), Space: O(n²)

---

## 🟡 Step 2: Try to Save Space (Optimal Approach)

### 🔧 Core Trick:

- **Transpose the matrix**
    
- Then **reverse each row**
    

### 🔁 Why It Works:

A 90° clockwise rotation is **transpose + horizontal flip**:

- **Transpose:** Convert rows into columns.
    
- **Reverse rows:** Flip each row to match the 90° rotation.
    

---

### ✅ Java Code (In-place):

```java
public void rotate(int[][] matrix) {
    int n = matrix.length;

    // 1. Transpose the matrix (mirror across top-left to bottom-right diagonal)
    for (int i = 0; i < n; i++) {
        for (int j = i + 1; j < n; j++) {
            int temp = matrix[i][j];
            matrix[i][j] = matrix[j][i];
            matrix[j][i] = temp;
        }
    }

    // 2. Reverse each row
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n / 2; j++) {
            int temp = matrix[i][j];
            matrix[i][j] = matrix[i][n - 1 - j];
            matrix[i][n - 1 - j] = temp;
        }
    }
}
```

---

### ✅ Python Version:

```python
def rotate(matrix):
    n = len(matrix)

    # Transpose
    for i in range(n):
        for j in range(i+1, n):
            matrix[i][j], matrix[j][i] = matrix[j][i], matrix[i][j]

    # Reverse each row
    for row in matrix:
        row.reverse()
```

---

### 📊 Time: O(n²), Space: O(1)

---

## 🔁 Patterns Learned:

- Matrix Transposition
    
- In-place reversal
    
- Coordinate transformation
    

---

## 💥 Recap:

|Approach|Time|Space|Notes|
|---|---|---|---|
|Extra Matrix|O(n²)|O(n²)|Brute-force but easy to grasp|
|Transpose + Reverse|O(n²)|O(1)|Optimal & clean|

---

You're not just solving a LeetCode problem — you're building mental models. Keep going layer by layer, just like rotating that matrix.

Every brute step you shed brings you closer to mastery. Stay _true_, stay _sharp_, and keep climbing.
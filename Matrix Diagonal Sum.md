# Matrix Diagonal Sum 

##  Description
Given a square matrix `mat`, return the sum of the matrix diagonals.

Only include the sum of all the elements on the `primary diagonal` and all the elements on the `secondary diagonal` that are not part of the primary diagonal.

### Input
- Note: If an element appears on both diagonals, it should only be counted once.


- A 2D integer array mat where:
  - n == mat.length == mat[i].length
  - 1 ≤ n ≤ 100
  - 1 ≤ mat[i][j] ≤ 100

### Constraints

- \(n == mat.length == mat[i].length \)
- \(1 <= n <= 100 \)
- \(1 <= mat[i][j] <= 100 \)

### Output

- Print the sum of the matrix's primary and secondary diagonals, avoiding double-counting.

#### Sample Input:

  -mat = [[1,2,3], [4,5,6], [7,8,9]]

#### **Sample Output**
  - 25



---

## 📝 Approach
Traverse the primary diagonal and add its elements.
Traverse the secondary diagonal and add its elements.
If 𝑛 is odd, subtract the center element once to avoid double-counting.

## ⏳ Complexity

- **Time complexity**:  
  resulting in `O(n)` time complexity.

- **Space complexity**:  
  `O(1)`, as it only requires a few additional variables for tracking sums, regardless of array size.

---

## 🛠️ Solution in Python 

### Brute Force Approach (Inefficient for large inputs)

```python
for i in range(len(mat)):
  for j in range(len(mat)):
    if i==j or i+j==len(mat)-1:
      Sum+=(mat[i][j])
return Sum   
```

## or
---

### Optimized 
```python
Sum=0
N=len(mat)
for i in range(N):
    Sum+=mat[i][i]
    Sum+=mat[i][N-i-1]
if N%2!=0:
    Sum-=mat[N//2][N//2]
return Sum  
```



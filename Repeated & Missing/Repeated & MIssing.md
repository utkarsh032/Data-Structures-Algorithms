# Repeated and Missing

##  Description
Given an array of size `n`. Array elements are in the range from `1 to n`. In the given array, one
number from set {1, 2, ... n} is missing and one number occurs twice in the array. Find these
two numbers.
Print the missing one first and then the repeated one with a space character in between
them.
**Expected Auxillary Space Complexity** - `O(1)`.

### 📥 Input Format
- The first line contains an integer `t`, the number of test cases.
- For each test case:
  - The first line contains an integer `n`, the size of the array.
  - The second line contains `n` integers representing the array elements.

### 📤 Output Format
- For each test case, print the missing number followed by the repeated number, separated by a space.

### 🧩 Constraints
- **Expected Auxiliary Space Complexity**: `O(1)`
- **Input Constraints:**
  - `1 ≤ t ≤ 10`  *(Number of test cases)*
  - `2 ≤ n ≤ 100,000` *(Size of the array for each test case)*
  - `1 ≤ Ai ≤ n` *(Values in the array)*

---


#### Sample Input:

  - 3
  - 5
  - 1 2 3 3 4
  - 2
  - 1 1
  - 3
  - 1 2 2

#### **Sample Output**
  - 5 3
  - 2 1
  - 3 1

---


## 💡 Approach

To solve this problem efficiently, we leverage **mathematical formulas**:

1. **Expected Sum and Squared Sum Formulas**:
   - Sum of numbers from `1` to `n`:  
     \[
     \text{expected\_sum} = \frac{n \times (n + 1)}{2}
     \]
   - Sum of squares from `1` to `n`:  
     \[
     \text{expected\_square\_sum} = \frac{n \times (n + 1) \times (2 \times n + 1)}{6}
     \]

2. **Calculate Differences**:
   - Compute the differences between actual and expected sums (`sum_diff`) and squares (`square_sum_diff`).

3. **Deriving Missing and Repeated Values**:
   - Use the differences to form two equations and solve for the missing and repeated numbers.

This approach is optimal, achieving **O(n)** time complexity and **O(1)** auxiliary space.

---

## ⏳ Complexity Analysis

- **Time Complexity**:  
  Each test case runs in `O(n)`, resulting in a total complexity of `O(n * t)` for all test cases.

- **Space Complexity**:  
  `O(1)`, as only a constant number of variables are used.

---

## 🛠️ Solution in Python 

```python
T=int(input())
for  _  in range(T):
    N=int(input())
    A=list(map(int,input().split()))
    
    expectSum=N*(N+1)//2
    expectSquSum=N*(N+1)*(2*N+1)//6
    
    actSum=sum(A)
    actSquSum=sum(ele ** 2 for ele in A)
    
    sumDiff = actSum-expectSum
    sumSquDiff = actSquSum-expectSquSum
    
    repeatedMiss= sumSquDiff//sumDiff
    
    repeated=(sumDiff+repeatedMiss)//2
    missing=repeatedMiss-repeated
    
    print(missing,repeated)

```



# Arrays Modification

## 📜 Description

Alice is organizing a series of array modification queries for her programming practice. She has an array of integers and wants to perform various operations on it based on a set of queries.

The array modification rules are as follows:
- **Query Type 0:** Add `1` to each element in the array from index `0` to a specified index (inclusive).
- **Query Type 1:** Subtract `1` from the value at a specified index in the array.

Alice is given an initial array, and she needs to apply the given queries to modify the array accordingly.

---

## 📥 Input Format
1. The first line contains an integer `N` representing the size of the initial array.
2. The second line contains `N` integers representing the initial values of the array.
3. The third line contains an integer `Q` representing the number of queries.
4. The next `Q` lines contain two integers `Type` and `index`:
   - `Type` (0 or 1): The type of query.
   - `index`: The index for the query.

---

## 📤 Output Format
1. The first line contains the final state of the modified array.
2. The second line contains the result of each query:
   - For **Query Type 0**, the sum of the modified array.
   - For **Query Type 1**, the value at the specified index.

---

## 🧩 Constraints
- \( 1 \leq N \leq 10^5 \) (Size of the array)
- \( 1 \leq A[i] \leq 10^9 \) (Values in the array)
- \( 1 \leq Q \leq 10^5 \) (Number of queries)
- \( 0 \leq Type \leq 1 \) (Query Type)
- \( 0 \leq index < N \) (Index for the query)

---

#### 🔢 Sample Input

  - 4
  - 10 20 30 40
  - 2
  - 0 3
  - 1 1

#### **Sample Output**
  - 11 21 31 41
  - 19
  
## 💡 Approach

1. **Query Type 0** (Add 1 from index `0` to `index`):
   - Iterate over the range `0` to `index` and increment each element by `1`.
   - Compute the sum of the array after modification and store it in the results.

2. **Query Type 1** (Subtract 1 from element at `index`):
   - Decrement the value at the given `index` by `1`.
   - Store the value at the specified index in the results.

3. Modify the array directly to ensure changes persist across queries.

---

## ⏳ Complexity Analysis

- **Time Complexity**:
  - Query Type 0: \(O(k)\), where \(k\) is the target index.
  - Query Type 1: \(O(1)\).
  - Total: \(O(Q \times k)\) (worst case).

- **Space Complexity**:
  - \(O(N + Q)\) for storing the array and queries.

---

## 🛠️ Solution in Python

```python
def solve(N,A,Type,index):
    newArr=[]
    if Type==0:
        for i in range(Type,index+1):
            newArr.append(A[i]+1)
    elif Type==1:
        for i in range(Type,index+1):
            newArr.append(A[i]-1)
    return newArr


# Input Reading
N=int(input())
A=list(map(int,input().split()))
Q=int(input())
for _ in range(Q):
    Type,index=list(map(int,input().split()))
    print(solve(N,A,Type,index))
    
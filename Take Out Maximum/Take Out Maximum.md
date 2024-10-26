# Take Out Maximum

##  Description

Given an array of integers and a number `k`, find the **maximum sum** of a subarray of size `k`.

### Input

- The first line consists of two integers `n` and `k`, separated by space:
  - `n` - the length of the array.
  - `k` - the size of the subarray.
- The second line consists of `n` integers separated by spaces, representing the elements of the array.

### Constraints

- \( 1 \leq n \leq 10^7 \)
- \( 1 \leq k \leq 10^6 \)

### Output

- Print the maximum sum of a subarray of size `k`.

#### Sample Input:

  - 10 3
  - 1-1-21-241939

#### **Sample Output**
  - 21



---

## 📝 Approach

To find the maximum sum of a subarray of fixed size `k`, we can use an **efficient sliding window approach** rather than the brute-force approach to keep the solution within time limits for large inputs.

### Sliding Window Approach

1. **Initialize the first window:**  
   - Compute the sum of the first `k` elements. This is our initial window sum.
  
2. **Slide the window across the array:**  
   - For each subsequent element from index `k` to `n-1`:
     - Adjust the window sum by **subtracting the element that is no longer in the window** (at the start of the window) and **adding the new element** (at the end of the window).
     - Update the maximum sum if the current window sum is greater.

3. **Result:**  
   - By the end of the array, the maximum sum recorded will be the maximum sum of any subarray of size `k`.

This approach is efficient, achieving an **O(n)** time complexity.

---

## ⏳ Complexity

- **Time complexity**:  
  The sliding window technique processes each element exactly once, resulting in `O(n)` time complexity.

- **Space complexity**:  
  `O(1)`, as it only requires a few additional variables for tracking sums, regardless of array size.

---

## 🛠️ Solution in Python 

### Brute Force Approach (Inefficient for large inputs)

This approach checks each possible subarray of size `k` and calculates their sum, comparing each with the maximum sum so far. 

```python
n, k = map(int, input().split())
A = list(map(int, input().split()))
max_sub_sum = 0

for i in range(n - k + 1):
    target_sum = sum(A[i:i+k])
    if target_sum > max_sub_sum:
        max_sub_sum = target_sum

print(max_sub_sum)
```

# or

```python
mxSubSum=0
for i in range(N-K+1):
    targetSum=0
    for j in range(i,K+i):
        targetSum+=A[j]
        if targetSum>mxSubSum:
            mxSubSum=targetSum
print(mxSubSum)
```

### Sliding Window : 
```python
n, k = map(int, input().split())
A = list(map(int, input().split()))
window_sum = sum(A[:k])
max_sum = window_sum

for i in range(k, n):
    window_sum += A[i] - A[i - k]
    max_sum = max(max_sum, window_sum)
print(max_sum)

```



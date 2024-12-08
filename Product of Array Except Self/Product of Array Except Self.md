# Product of Array Except Self

## 📜 Description
Given an integer array `nums`, return an array `answer` such that `answer[i]` is equal to the product of all elements of `nums` except `nums[i]`.  

### Notes:
- The product of any prefix or suffix of `nums` is guaranteed to fit in a 32-bit integer.
- You **must not use the division operation**.
- The algorithm should run in **O(n)** time complexity.

---

## 📥 Input Format
- A single integer array `nums` containing `n` integers.

---

## 📤 Output Format
- A single integer array `answer` of size `n` where `answer[i]` contains the product of all elements of `nums` except `nums[i]`.

---

## 🧩 Constraints
- ` 1 <= t <= 10^3 ` 
- ` 2 <= nums.length <= 10^5 ` 
- ` -30 <= nums[i] <= 30 `
---

#### Sample Input:
  - 2
  - 4
  - 1 2 3 4
  - 5
  - -1 1 0 3 -3
  
#### **Sample Output**
  - 24 12 8 6
  - 0 0 9 0 0


---

## 💡 Approach

1. **Prefix and Postfix Products**:
   - Use prefix and postfix arrays to store cumulative products.
   - Prefix array calculates cumulative product from the start to each index.
   - Postfix array calculates cumulative product from the end to each index.

2. **Single Pass Optimization**:
   - Avoid using extra space for prefix and postfix arrays by calculating them directly during traversal.

3. **Final Calculation**:
   - For each index `i`, multiply the prefix product (excluding `nums[i]`) with the postfix product.

This approach ensures **O(n)** time complexity and **O(1)** space complexity (excluding the output array).

---

## ⏳ Complexity Analysis

- **Time Complexity**: \( O(n) \)  
  Two passes are made over the array (one for prefix and one for postfix).  

- **Space Complexity**: \( O(1) \)  
  The solution uses constant space (excluding the output array).

---

## 🛠️ Solution in Python

```python
def product_except_self(nums):
    N = len(nums)
    res = [1] * N 
    
    prefix = 1
    for i in range(N):
        res[i] = prefix
        prefix *= nums[i]

    postfix = 1
    for i in range(N - 1, -1, -1):
        res[i] *= postfix
        postfix *= nums[i]

    return res

print(product_except_self(nums))


# Lifeboats Problem

## 🚢 Description

Given `n` passengers who are going to board the ship for a journey, you are the captain of the ship and are responsible for their safety. You have an array `W` of size `n` which contains the weights of all the passengers. 

For ensuring the safety of the passengers, you are required to calculate the **minimum number of lifeboats** needed for the journey.

Each lifeboat can carry at most **2 people at the same time**, provided the sum of the weights of those people is within the limit `k` (max holding capacity of a lifeboat). It is ensured that each person can be carried by a lifeboat.

### Input

- The first line of input contains an integer `t` (1 ≤ t ≤ 10) — the number of test cases.
- For each test case:
  - The first line contains two integers `n` and `k` (1 ≤ n, k ≤ 100000) — the number of people and the weight limit of the boat, respectively.
  - The second line contains `n` integers `W1, W2, ..., Wn` (1 ≤ Wi ≤ k) — the weights of each person.

### Output

For each test case, print the answer: the number of lifeboats required.

### Example

#### **Sample Input**
  2
  4 5
  3 5 3 4
  4 3
  1 2 2 3

#### **Sample Output**
 4
 3



---


## 📝 Approach

1. **Sorting the weights**:  
   The key to minimizing the number of boats is to pair the heaviest person with the lightest person if their combined weight is within the boat's capacity.

2. **Two-pointer technique**:  
   Use two pointers:
   - One starting from the lightest person (`l`).
   - One starting from the heaviest person (`r`).

   - **If the lightest and heaviest can share a boat** (`W[l] + W[r] <= K`), move both pointers.
   - **Otherwise**, move only the pointer for the heavier person (`r`).

3. **Increment the boat count**:  
   For every pair checked, increment the number of required boats.

---

## ⏳ Complexity
- **Time complexity**:  
  Sorting the list of weights takes `O(n log n)`, and the two-pointer approach runs in `O(n)`. Hence, the total time complexity for each test case is `O(n log n)`.

- **Space complexity**:  
  `O(n)` for storing the list of weights.


## 🛠️ Solution in Python

```python
T = int(input())
for _ in range(T):
  N, K = list(map(int, input().split()))
  W = list(map(int, input().split()))
  W.sort()
  rBoats = 0
  l, r = 0, N - 1
  while l <= r:
    if W[l] + W[r] <= K:
      l += 1
    r -= 1
    rBoats += 1
  print(rBoats)

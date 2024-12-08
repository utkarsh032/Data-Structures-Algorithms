# All Numbers Are Beautiful

## 📜 Description
You believe that all numbers are beautiful, but your boss disagrees. According to your boss, a number's beauty depends on certain factors and another integer `k`.  

The **k-beauty** of an integer `num` is defined as the number of substrings of `num` (when read as a string) that meet the following conditions:  
1. It has a length of `k`.  
2. It is a divisor of `num`.  

### Notes:  
- Leading zeros are allowed.  
- 0 is not a divisor of any value.  
- A substring is a contiguous sequence of characters in a string.

---

## 📥 Input Format
- The first line contains an integer `t` - the number of test cases.
- The next `t` lines describe the test cases:
  - Each test case contains two space-separated integers `num` and `k`.

---

## 📤 Output Format
For each test case, print the k-beauty of the number.

---

## 🧩 Constraints
- `1<= t <= 1000 ` 
- `1<= num <= 10^9` 
- `1<= k <= num.length` *(taking num as string)*
---

#### Sample Input:
  - 2
  - 240 2
  - 430043 2
  
#### **Sample Output**
  - 2
  - 2

## 💡 Approach

To solve the problem:  
1. **Convert the number to a string**: This allows easy slicing to extract substrings.  
2. **Iterate through all substrings of length `k`**:
   - Extract substrings from `num` using sliding window techniques.  
   - Convert the substring back to an integer to check divisibility.  
3. **Count divisors**: Check if the substring (as an integer) divides `num` without a remainder.  
4. **Handle edge cases**:
   - Skip substrings starting with `0`.
   - Avoid division by `0`.

This solution ensures we efficiently calculate the k-beauty for each test case.

---

## ⏳ Complexity Analysis
- **Time Complexity**: \( O(T \times N) \)  
  - \( T \): Number of test cases.  
  - \( N \): Length of `num`.  
  Each substring extraction and divisibility check takes \( O(N) \) time.

- **Space Complexity**: \( O(1) \)  
  Only a few variables are used, independent of input size.

---

## 🛠️ Solution in Python

```python
def solve(num,K):
    strNum=str(num)
    N=len(strNum)
    count=0
    for i in range(N-1):
        res=int(strNum[i:K+i])
        if res!=0 and num%res==0:
            count+=1
    return count

# Input handling
T=int(input())
for _ in range(T):
    num,K=list(map(int,input().split()))
    print(solve(num,K))




# Rule of Ones

## 📝 Description

You are given a binary string `s` consisting of only '0's and '1's. Your task is to count how many substrings have **dominant ones**.

### What is a Dominant Substring?
A substring is considered dominant if the number of `'1'`s in the substring is **greater than or equal to the square of the number of `'0'`s**.

Your mission is to find the count of such dominant substrings for the given binary string.

---

## 📥 Input Format

1. The first line contains an integer `t`, the number of test cases.
2. For each test case:
   - The first line contains an integer `n`, the size of the string `s`.
   - The second line contains the binary string `s`.

---

## 📤 Output Format

- For each test case, print the count of dominant substrings.

---

## 🧩 Constraints
- \( 1 <= t <= 100 \)
- \( 2 <= n <= 100 \)

---

## 🧪 Sample Input
    2
    5
    00011
    6
    101101
  
## **Sample Output**
    5
    16
    
    
## 💡 Approach

1. **Iterate Through All Substrings:**
   - Use two nested loops to generate all possible substrings of the string `s`.
     - Outer loop (`i`) for the starting position of the substring.
     - Inner loop (`j`) for the ending position of the substring.
2. **Count Zeros and Ones:**
   - For each substring, count the occurrences of `'0'` and `'1'`.
3. **Check Dominance:**
   - Check if the number of `'1'`s is greater than or equal to the square of the number of `'0'`s.
   - If the condition is satisfied, increment the count.
4. **Output the Count:**
   - Print the count of dominant substrings for each test case.

---

## ⏳ Complexity Analysis

### Time Complexity
- **Substring Generation:** \( O(n^2) \) for each string due to nested loops.
- **Zero/One Count:** \( O(n) \) for each substring using Python’s `count()` method.
- **Overall per Test Case:** \( O(n^3) \).
- For \( t \) test cases, the complexity is \( O(t \times n^3) \).

### Space Complexity
- **Substring Storage:** \( O(n) \) for storing substrings.
- Total: \( O(n) \).

---

## 🛠️ Solution in Python

```python
def count_dominant_substrings(t, test_cases):
    results = []
    for case in test_cases:
        n, s = case
        count = 0
        for i in range(n):
            for j in range(i, n):
                sub = s[i:j + 1]
                zero = sub.count('0')
                one = sub.count('1')
                if one >= zero ** 2:
                    count += 1
        results.append(count)
    return results

t = 2
test_cases = [(5, "00011"), (6, "101101")]

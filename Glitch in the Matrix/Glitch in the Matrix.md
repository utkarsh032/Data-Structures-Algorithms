# Glitch in the Matrix

## 📜 Description
You are given an integer `n` representing the height and width of a square. Your task is to generate a pattern of a hollow square of size \( n \times n \). The square should be composed of `*` characters on its borders and spaces inside it.

---

## 📥 Input Format
- The first line contains an integer `t` - the number of test cases.
- For each test case, a single integer `n` is provided, representing the size of the square.

---

## 📤 Output Format
For each test case, print the hollow square pattern of size \( n \times n \) as described. Each test case's output should be separated by a blank line.

---

## 🧩 Constraints
- \( 1 <= t <= 100 \)
- \( 2 <= n <= 100 \)

---

## 🧪 Sample Input
    3
    2
    5
    3
  
## **Sample Output**
    **
    **
    
    ***
    * *
    ***
    
    *****
    *   *
    *   *
    *   *
    *****
    
## 💡 Approach

1. **Outer Loop (`i`):** Iterate through each row from `0` to `N - 1`.
2. **Inner Loop (`j`):** Iterate through each column for the current row.
3. **Condition for `*`:**
   - Print `*` if the current cell lies on the border:
     - Top row (`i == 0`)
     - Bottom row (`i == N - 1`)
     - First column (`j == 0`)
     - Last column (`j == N - 1`)
   - Otherwise, print a space (`' '`).
4. After printing all columns in a row, move to the next line using `print()`.

---

## ⏳ Complexity Analysis

### Time Complexity
- The **outer loop** runs \( N \) times (for each row).
- The **inner loop** runs \( N \) times for each row (for each column).
- **Total Iterations:** \( N \times N \).
- **Overall Time Complexity:** \( O(N^2) \).

### Space Complexity
- No additional data structures are used, so the space complexity is **\( O(1) \)**.

---

## 🛠️ Solution in Python

```python
def print_hollow_square(N):
    for i in range(N):
        for j in range(N):
            # Print '*' for border cells, else print ' '
            if i == 0 or i == N - 1 or j == 0 or j == N - 1:
                print('*', end='')
            else:
                print(' ', end='')
        print()  # Move to the next line after each row

N = 3
print_hollow_square(N)


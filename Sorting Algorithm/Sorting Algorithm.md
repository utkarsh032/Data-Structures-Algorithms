# Sorting Algorithms Documentation

## **Bubble Sort**

- **Definition:** Bubble Sort is a simple sorting algorithm that repeatedly steps through the list, compares adjacent elements, and swaps them if they are in the wrong order.

- **Time Complexity:**
  - Best Case: O(N)
  - Average Case: O(N²)
  - Worst Case: O(N²)

- **Space Complexity:** O(1)

- **Advantages:**
  - Simple and easy to implement
  - Works well for small datasets

- **Disadvantages:**
  - Inefficient for large datasets
  - High number of comparisons and swaps

```Python
# Bubble Sort Implementation
def bubble_sort(A, N):
    for i in range(N):
        for j in range(N-i-1):
            if A[j] > A[j+1]:
                A[j], A[j+1] = A[j+1], A[j]
    print(A)

A = [2, 0, 2, 1, 1, 0]
N = len(A)
bubble_sort(A, N)
```

## **Insertion Sort**

- **Definition:** Insertion Sort builds the final sorted array one item at a time by taking each element and inserting it into its correct position.

- **Time Complexity:**
  - Best Case: O(N)
  - Average Case: O(N²)
  - Worst Case: O(N²)

- **Space Complexity:** O(1)

- **Advantages:**
  - Efficient for small datasets
  - Adaptive for nearly sorted data

- **Disadvantages:**
  - Inefficient for large datasets

```Python
# Insertion Sort Implementation
def insertion_sort(A, N):
    for i in range(N):
        key = A[i]
        j = i - 1
        while j >= 0 and key < A[j]:
            A[j + 1] = A[j]
            j -= 1
        A[j + 1] = key
    print(A)

A = [2, 0, 2, 1, 1, 0]
N = len(A)
insertion_sort(A, N)
```

## **Selection Sort**

- **Definition:** Selection Sort repeatedly selects the smallest element from the unsorted portion and swaps it with the first unsorted element.

- **Time Complexity:**
  - Best Case: O(N²)
  - Average Case: O(N²)
  - Worst Case: O(N²)

- **Space Complexity:** O(1)

- **Advantages:**
  - Simple and easy to implement
  - Works well for small datasets

- **Disadvantages:**
  - Inefficient for large datasets
  - High number of comparisons

```Python
# Selection Sort Implementation
def selection_sort(A, N):
    for i in range(N-1):
        mn_idx = i
        for j in range(i+1, N):
            if A[j] < A[mn_idx]:
                mn_idx = j
        A[i], A[mn_idx] = A[mn_idx], A[i]
    print(A)

A = [2, 0, 2, 1, 1, 0]
N = len(A)
selection_sort(A, N)
```

## **Quick Sort**

- **Definition:** Quick Sort is a divide-and-conquer algorithm that selects a pivot element and partitions the array into two subarrays, recursively sorting them.

- **Time Complexity:**
  - Best Case: O(N log N)
  - Average Case: O(N log N)
  - Worst Case: O(N²)

- **Space Complexity:** O(log N)

- **Advantages:**
  - Very efficient for large datasets
  - Works well for general-purpose sorting

- **Disadvantages:**
  - Worst case occurs when pivot selection is poor
  - Not stable

```Python
# Quick Sort Implementation
def quick_sort(A):
    if len(A) <= 1:
        return A
    pivot = A[len(A) // 2]
    left = [x for x in A if x < pivot]
    middle = [x for x in A if x == pivot]
    right = [x for x in A if x > pivot]
    return quick_sort(left) + middle + quick_sort(right)

A = [2, 0, 2, 1, 1, 0]
print(quick_sort(A))
```

## **Merge Sort**

- **Definition:** Merge Sort is a divide-and-conquer algorithm that splits the array into halves, recursively sorts them, and merges them back together.

- **Time Complexity:** O(N log N) for all cases
- **Space Complexity:** O(N)

- **Advantages:**
  - Stable sorting algorithm
  - Efficient for large datasets

- **Disadvantages:**
  - Requires extra space
  - Slower than Quick Sort in practice

```Python
# Merge Sort Implementation
def merge_sort(A):
    if len(A) <= 1:
        return A
    mid = len(A) // 2
    left = merge_sort(A[:mid])
    right = merge_sort(A[mid:])
    return merge(left, right)

def merge(left, right):
    result = []
    i = j = 0
    while i < len(left) and j < len(right):
        if left[i] < right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1
    result.extend(left[i:])
    result.extend(right[j:])
    return result

A = [2, 0, 2, 1, 1, 0]
print(merge_sort(A))
```

## **Heap Sort**

- **Definition:** Heap Sort is a comparison-based sorting algorithm that builds a binary heap and extracts the largest element one by one.

- **Time Complexity:** O(N log N) for all cases
- **Space Complexity:** O(1)

- **Advantages:**
  - Efficient and does not require extra space
  - Works well in systems with limited memory

- **Disadvantages:**
  - Not stable
  - Slower in practice than Quick Sort

```Python
# Heap Sort Implementation
import heapq

def heap_sort(A):
    heapq.heapify(A)
    return [heapq.heappop(A) for _ in range(len(A))]

A = [2, 0, 2, 1, 1, 0]
print(heap_sort(A))
```

## **Comparison**

| Algorithm     | Best Case | Average Case | Worst Case | Space Complexity |
|--------------|----------|--------------|------------|------------------|
| Bubble Sort  | O(N)     | O(N²)       | O(N²)     | O(1)             |
| Insertion Sort | O(N)  | O(N²)       | O(N²)     | O(1)             |
| Selection Sort | O(N²) | O(N²)       | O(N²)     | O(1)             |
| Quick Sort   | O(N log N) | O(N log N) | O(N²)     | O(log N)         |
| Merge Sort   | O(N log N) | O(N log N) | O(N log N) | O(N)             |
| Heap Sort    | O(N log N) | O(N log N) | O(N log N) | O(1)             |

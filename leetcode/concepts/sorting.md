# Sorting - Interview Preparation Guide

## Theory & Intuition
Sorting is the process of arranging data in a particular order (ascending or descending). Efficient sorting is crucial for optimizing the performance of other algorithms (like search and merge operations).

- **Comparison-based sorts**: e.g., Bubble, Selection, Insertion, Merge, Quick, Heap sort.
- **Non-comparison sorts**: e.g., Counting, Radix, Bucket sort (for integers or fixed range).
- **Stability**: A stable sort preserves the relative order of equal elements.

### When to Use
- When you need to preprocess data for binary search or deduplication.
- When you need to order data for reporting or further processing.

## Common Algorithms
- Bubble Sort: O(n^2)
- Insertion Sort: O(n^2)
- Merge Sort: O(n log n)
- Quick Sort: O(n log n) average, O(n^2) worst
- Heap Sort: O(n log n)
- Counting/Radix Sort: O(n) for integers

## Example 1: Merge Sort (Python)
```python
def merge_sort(arr):
    if len(arr) <= 1:
        return arr
    mid = len(arr) // 2
    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])
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
```

## Example 2: Quick Sort (Python)
```python
def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    pivot = arr[0]
    less = [x for x in arr[1:] if x < pivot]
    greater = [x for x in arr[1:] if x >= pivot]
    return quick_sort(less) + [pivot] + quick_sort(greater)
```

## Example 3: Counting Sort (for small integers)
```python
def counting_sort(arr):
    count = [0] * (max(arr) + 1)
    for num in arr:
        count[num] += 1
    result = []
    for i, c in enumerate(count):
        result.extend([i] * c)
    return result
```

## Diagram
```
Unsorted: [4, 2, 5, 1, 3]
Sorted:   [1, 2, 3, 4, 5]
```

## Extra Study Material
- [Sorting Algorithms (GeeksforGeeks)](https://www.geeksforgeeks.org/sorting-algorithms/)
- [Sorting - LeetCode Explore](https://leetcode.com/explore/learn/card/sorting/)

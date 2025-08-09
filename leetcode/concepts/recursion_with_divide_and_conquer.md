# Recursion with Divide and Conquer - Interview Preparation Guide

## Theory & Intuition
Divide and conquer is a technique where a problem is divided into smaller subproblems, each solved recursively, and their solutions are combined to solve the original problem. It is a fundamental paradigm in computer science.

- Divide: Break the problem into subproblems.
- Conquer: Solve each subproblem recursively.
- Combine: Merge the solutions.

### When to Use
- When a problem can be broken into similar subproblems.
- Used in sorting (merge sort, quicksort), searching, and tree/graph algorithms.

## Example 1: Merge Sort
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

## Example 2: Maximum Subarray (LeetCode 53, Divide & Conquer)
```python
def max_subarray(nums):
    def helper(l, r):
        if l == r:
            return nums[l]
        m = (l + r) // 2
        left = helper(l, m)
        right = helper(m+1, r)
        cross = max_crossing(nums, l, m, r)
        return max(left, right, cross)
    def max_crossing(nums, l, m, r):
        left_sum = right_sum = float('-inf')
        s = 0
        for i in range(m, l-1, -1):
            s += nums[i]
            left_sum = max(left_sum, s)
        s = 0
        for i in range(m+1, r+1):
            s += nums[i]
            right_sum = max(right_sum, s)
        return left_sum + right_sum
    return helper(0, len(nums)-1)
```

## Example 3: Quick Sort
```python
def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    pivot = arr[0]
    left = [x for x in arr[1:] if x < pivot]
    right = [x for x in arr[1:] if x >= pivot]
    return quick_sort(left) + [pivot] + quick_sort(right)
```

## Diagram
```
Divide: [1,2,3,4,5,6,7,8]
   /                \
[1,2,3,4]        [5,6,7,8]
... and so on
```

## Extra Study Material
- [Divide and Conquer (LeetCode Explore)](https://leetcode.com/explore/learn/card/recursion-i/)
- [Divide and Conquer (GeeksforGeeks)](https://www.geeksforgeeks.org/divide-and-conquer/)

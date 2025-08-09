# Binary Search - Interview Preparation Guide

## Theory & Intuition
Binary search is a divide-and-conquer algorithm for finding an element in a sorted array by repeatedly dividing the search interval in half. It has O(log n) time complexity.

- Works only on sorted data.
- Can be adapted for lower/upper bounds, first/last occurrence, and search in rotated arrays.

### When to Use
- When you need to search, count, or optimize over a sorted array or monotonic function.

## Example 1: Standard Binary Search
```python
def binary_search(arr, target):
    left, right = 0, len(arr) - 1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1
```

## Example 2: Lower Bound (First Occurrence)
```python
def lower_bound(arr, target):
    left, right = 0, len(arr)
    while left < right:
        mid = (left + right) // 2
        if arr[mid] < target:
            left = mid + 1
        else:
            right = mid
    return left
```

## Example 3: Search in Rotated Sorted Array
```python
def search_rotated(arr, target):
    left, right = 0, len(arr) - 1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid
        if arr[left] <= arr[mid]:
            if arr[left] <= target < arr[mid]:
                right = mid - 1
            else:
                left = mid + 1
        else:
            if arr[mid] < target <= arr[right]:
                left = mid + 1
            else:
                right = mid - 1
    return -1
```

## Diagram
```
[1, 3, 5, 7, 9]
 ^     ^     ^
L=0   M=2   R=4
```

## Extra Study Material
- [Binary Search Patterns (LeetCode)](https://leetcode.com/explore/learn/card/binary-search/)
- [Binary Search (GeeksforGeeks)](https://www.geeksforgeeks.org/binary-search/)

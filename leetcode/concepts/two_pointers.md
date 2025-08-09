# Two Pointers - Interview Preparation Guide

## Theory & Intuition
The two pointers technique involves using two indices to traverse a data structure, often from opposite ends or at different speeds. It is widely used for array and linked list problems.

- **Left/right pointers**: Start at both ends and move towards each other.
- **Slow/fast pointers**: Move at different speeds (e.g., cycle detection).

### When to Use
- When searching for pairs or subarrays (e.g., sum problems, palindromes).
- When you need to process data in-place with O(1) extra space.

## Example 1: Reverse an Array
```python
def reverse(arr):
    left, right = 0, len(arr) - 1
    while left < right:
        arr[left], arr[right] = arr[right], arr[left]
        left += 1
        right -= 1
```

## Example 2: Two Sum II (Sorted Array)
```python
def two_sum(arr, target):
    left, right = 0, len(arr) - 1
    while left < right:
        s = arr[left] + arr[right]
        if s == target:
            return [left, right]
        elif s < target:
            left += 1
        else:
            right -= 1
```

## Example 3: Remove Duplicates from Sorted Array
```python
def remove_duplicates(nums):
    if not nums:
        return 0
    write = 1
    for read in range(1, len(nums)):
        if nums[read] != nums[read-1]:
            nums[write] = nums[read]
            write += 1
    return write
```

## Diagram
```
Array: [1, 2, 3, 4, 5]
left →        ← right
```

## Extra Study Material
- [Two Pointers (LeetCode)](https://leetcode.com/tag/two-pointers/)
- [Two Pointer Technique (GeeksforGeeks)](https://www.geeksforgeeks.org/two-pointers-technique/)

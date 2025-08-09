# Arrays - Interview Preparation Guide

## Theory & Intuition
Arrays are a fundamental data structure that store elements in a contiguous block of memory. They allow constant-time access by index and are widely used for storing and manipulating collections of data.

- **Fixed size**: The size is set at creation (in most languages).
- **Indexed access**: O(1) time to access or update any element by index.
- **Memory layout**: Elements are stored sequentially in memory.

### When to Use
- When you need fast, random access to elements.
- When the number of elements is known and fixed (or rarely changes).

## Common Operations
- Access: `arr[i]` (O(1))
- Update: `arr[i] = x` (O(1))
- Insert/Delete (at end): O(1) for dynamic arrays, O(n) for fixed-size
- Insert/Delete (at start/middle): O(n)

## Example 1: Find Maximum Element
```python
arr = [3, 1, 4, 1, 5, 9]
max_val = arr[0]
for num in arr:
    if num > max_val:
        max_val = num
print(max_val)  # Output: 9
```

## Example 2: Reverse an Array In-Place
```python
arr = [1, 2, 3, 4]
left, right = 0, len(arr) - 1
while left < right:
    arr[left], arr[right] = arr[right], arr[left]
    left += 1
    right -= 1
print(arr)  # Output: [4, 3, 2, 1]
```

## Example 3: Two Sum (Find if any two numbers sum to target)
```python
def two_sum(arr, target):
    seen = set()
    for num in arr:
        if target - num in seen:
            return True
        seen.add(num)
    return False
```

## Diagram
```
Index:  0   1   2   3   4
Array: [10, 20, 30, 40, 50]
```

## Extra Study Material
- [Arrays (GeeksforGeeks)](https://www.geeksforgeeks.org/array-data-structure/)
- [Array - LeetCode Explore](https://leetcode.com/explore/learn/card/array-and-string/)

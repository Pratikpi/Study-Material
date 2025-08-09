# Prefix Product - Interview Preparation Guide

## Theory & Intuition
Prefix product is a technique where you compute the product of all elements before a given index in an array. It is commonly used in problems like "Product of Array Except Self" to avoid division and achieve O(n) time.

- **Prefix product array**: Each element at index i is the product of all elements before i.
- **Can be combined with suffix product for full solution.**

### When to Use
- When you need to compute products of subarrays efficiently.
- When division is not allowed or possible.

## Example 1: Compute Prefix Product Array
```python
def prefix_product(arr):
    n = len(arr)
    prefix = [1]*n
    for i in range(1, n):
        prefix[i] = prefix[i-1] * arr[i-1]
    return prefix
```

## Example 2: Product of Array Except Self
```python
def product_except_self(nums):
    n = len(nums)
    res = [1]*n
    left = 1
    for i in range(n):
        res[i] = left
        left *= nums[i]
    right = 1
    for i in range(n-1, -1, -1):
        res[i] *= right
        right *= nums[i]
    return res
```

## Example 3: Prefix Product for Range Queries
```python
def range_product(arr, l, r):
    prefix = [1]*(len(arr)+1)
    for i in range(1, len(arr)+1):
        prefix[i] = prefix[i-1] * arr[i-1]
    return prefix[r+1] // prefix[l]
```

## Diagram
```
arr:    [2, 3, 4, 5]
prefix: [1, 2, 6, 24]
```

## Extra Study Material
- [Product of Array Except Self (LeetCode)](https://leetcode.com/problems/product-of-array-except-self/)
- [Prefix Product (GeeksforGeeks)](https://www.geeksforgeeks.org/prefix-product-array/)

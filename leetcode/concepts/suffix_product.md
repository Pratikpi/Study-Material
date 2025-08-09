# Suffix Product - Interview Preparation Guide

## Theory & Intuition
Suffix product is a technique where you compute the product of all elements after a given index in an array. It is often paired with prefix product to solve problems like "Product of Array Except Self" efficiently.

- **Suffix product array**: Each element at index i is the product of all elements after i.
- **Used with prefix product for O(n) solutions.**

### When to Use
- When you need to compute products of subarrays efficiently from the end.
- When division is not allowed or possible.

## Example 1: Compute Suffix Product Array
```python
def suffix_product(arr):
    n = len(arr)
    suffix = [1]*n
    for i in range(n-2, -1, -1):
        suffix[i] = suffix[i+1] * arr[i+1]
    return suffix
```

## Example 2: Product of Array Except Self (with prefix)
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

## Example 3: Suffix Product for Range Queries
```python
def range_product(arr, l, r):
    suffix = [1]*(len(arr)+1)
    for i in range(len(arr)-1, -1, -1):
        suffix[i] = suffix[i+1] * arr[i]
    return suffix[l] // suffix[r+1]
```

## Diagram
```
arr:    [2, 3, 4, 5]
suffix: [60, 20, 5, 1]
```

## Extra Study Material
- [Product of Array Except Self (LeetCode)](https://leetcode.com/problems/product-of-array-except-self/)
- [Prefix and Suffix Product (GeeksforGeeks)](https://www.geeksforgeeks.org/prefix-product-array/)

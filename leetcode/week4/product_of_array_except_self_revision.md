# LeetCode: Product of Array Except Self - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/product-of-array-except-self/description/)

## Problem Statement
Given an integer array nums, return an array answer such that answer[i] is equal to the product of all the elements of nums except nums[i].

The solution must be O(n) and not use division.

### Example
- Input: nums = [1,2,3,4]
  Output: [24,12,8,6]

- Input: nums = [-1,1,0,-3,3]
  Output: [0,0,9,0,0]

### Constraints
- 2 <= nums.length <= 10^5
- -30 <= nums[i] <= 30
- The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.

---

## Concepts Required
- Arrays
- Prefix Product
- Suffix Product

---

## Prefix and Suffix Product Approach
- Compute prefix and suffix products for each index.
- Time Complexity: O(n)
- Space Complexity: O(1) extra (output array not counted)

### Pseudocode
```
output = [1]*n
for i in 1..n-1: output[i] = output[i-1] * nums[i-1]
right = 1
for i in n-1..0: output[i] *= right; right *= nums[i]
return output
```

---

## Python Code
```python
def productExceptSelf(nums):
    n = len(nums)
    output = [1]*n
    for i in range(1, n):
        output[i] = output[i-1] * nums[i-1]
    right = 1
    for i in range(n-1, -1, -1):
        output[i] *= right
        right *= nums[i]
    return output
```

---

## Key Takeaways
- Prefix and suffix products allow O(n) solution without division.
- Practice both extra array and in-place solutions.

---

## Follow-up
- How would you handle zeros in the array?
  - Count zeros: if more than one, all outputs are zero; if one, only the zero's position is nonzero (product of nonzero elements).
- Can you do it with constant space?
  - Yes, output array doesn't count as extra space; use two passes (left and right products) and only a few variables.

---

## Related Problems
- Subarray Product Less Than K
- Maximum Product Subarray
- Array of Products

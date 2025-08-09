# LeetCode: Maximum Subarray - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/maximum-subarray/description/)

## Problem Statement
Given an integer array `nums`, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

### Example
- Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
  Output: 6
  Explanation: [4,-1,2,1] has the largest sum = 6.

- Input: nums = [1]
  Output: 1

### Constraints
- 1 <= nums.length <= 10^5
- -10^4 <= nums[i] <= 10^4

---

## Concepts Required
- Arrays
- Dynamic Programming (Kadane's Algorithm)

---

## Kadane's Algorithm
- Track the maximum sum ending at each position.
- Time Complexity: O(n)

### Pseudocode
```
max_sum = curr_sum = nums[0]
for num in nums[1:]:
    curr_sum = max(num, curr_sum + num)
    max_sum = max(max_sum, curr_sum)
return max_sum
```

---

## Python Code
```python
def maxSubArray(nums):
    max_sum = curr_sum = nums[0]
    for num in nums[1:]:
        curr_sum = max(num, curr_sum + num)
        max_sum = max(max_sum, curr_sum)
    return max_sum
```

---

## Key Takeaways
- Kadane's Algorithm is optimal for this problem.
- Always consider both starting a new subarray and extending the current one.
- Practice variations: return the subarray, not just the sum.

---

## Follow-up
- How would you solve it with divide and conquer?
- Can you return the actual subarray?

---

## Related Problems
- Maximum Product Subarray
- Subarray Sum Equals K
- Best Time to Buy and Sell Stock

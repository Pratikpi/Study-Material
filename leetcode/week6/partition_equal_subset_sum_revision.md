# LeetCode: Partition Equal Subset Sum - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/partition-equal-subset-sum/description/)

## Problem Statement
Given a non-empty array nums containing only positive integers, find if the array can be partitioned into two subsets such that the sum of elements in both subsets is equal.

### Example
- Input: nums = [1,5,11,5]
  Output: true

- Input: nums = [1,2,3,5]
  Output: false

### Constraints
- 1 <= nums.length <= 200
- 1 <= nums[i] <= 100

---

## Concepts Required
- Dynamic Programming (Subset Sum)
- Arrays

---

## DP Approach
- Use a boolean DP array to track possible sums up to total//2.
- Time Complexity: O(n*sum(nums))

### Pseudocode
```
total = sum(nums)
if total % 2 != 0: return False
target = total // 2
dp = [True] + [False]*target
for num in nums:
    for i in range(target, num-1, -1):
        dp[i] = dp[i] or dp[i-num]
return dp[target]
```

---

## Python Code
```python
def canPartition(nums):
    total = sum(nums)
    if total % 2 != 0:
        return False
    target = total // 2
    dp = [True] + [False]*target
    for num in nums:
        for i in range(target, num-1, -1):
            dp[i] = dp[i] or dp[i-num]
    return dp[target]
```

---

## Key Takeaways
- Subset sum DP is optimal for partition problems.
- Practice both DP and backtracking solutions.

---

## Follow-up
- How would you return the actual subsets?
  - Track choices during DP or use backtracking to reconstruct the subsets that sum to the target.
- Can you do it with less space?
  - Yes, use a 1D DP array instead of 2D to reduce space complexity.

---

## Related Problems
- Subset Sum
- Target Sum
- Coin Change

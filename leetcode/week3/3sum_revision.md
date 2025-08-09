# LeetCode: 3Sum - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/3sum/description/)

## Problem Statement
Given an integer array `nums`, return all the triplets [nums[i], nums[j], nums[k]] such that i != j != k and nums[i] + nums[j] + nums[k] == 0.

The solution set must not contain duplicate triplets.

### Example
- Input: nums = [-1,0,1,2,-1,-4]
  Output: [[-1,-1,2],[-1,0,1]]

### Constraints
- 3 <= nums.length <= 3000
- -10^5 <= nums[i] <= 10^5

---

## Concepts Required
- Sorting
- Two Pointers
- Hash Set

---

## Two Pointers Approach
- Sort the array, fix one element, use two pointers for the rest.
- Skip duplicates to avoid repeated triplets.
- Time Complexity: O(n^2)

### Pseudocode
```
sort nums
for i in range(len(nums)):
    if i > 0 and nums[i] == nums[i-1]: continue
    left, right = i+1, len(nums)-1
    while left < right:
        s = nums[i] + nums[left] + nums[right]
        if s == 0:
            add triplet
            move left/right, skip duplicates
        elif s < 0: left += 1
        else: right -= 1
```

---

## Python Code
```python
def threeSum(nums):
    nums.sort()
    res = []
    for i in range(len(nums)):
        if i > 0 and nums[i] == nums[i-1]:
            continue
        l, r = i+1, len(nums)-1
        while l < r:
            s = nums[i] + nums[l] + nums[r]
            if s == 0:
                res.append([nums[i], nums[l], nums[r]])
                l += 1
                r -= 1
                while l < r and nums[l] == nums[l-1]: l += 1
                while l < r and nums[r] == nums[r+1]: r -= 1
            elif s < 0:
                l += 1
            else:
                r -= 1
    return res
```

---

## Key Takeaways
- Sorting and two pointers is optimal for 3Sum.
- Always skip duplicates for unique triplets.
- Practice both brute force and optimized solutions.

---

## Follow-up
- How would you solve 4Sum?
  - Use two pointers and nested loops, or generalize with recursion to reduce 4Sum to 3Sum.
- Can you generalize to kSum?
  - Yes, use recursion to reduce kSum to (k-1)Sum, applying two pointers at the base case.

---

## Related Problems
- 4Sum
- Two Sum
- 3Sum Closest

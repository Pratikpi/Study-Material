# LeetCode: Permutations - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/permutations/description/)

## Problem Statement
Given an array nums of distinct integers, return all possible permutations.

### Example
- Input: nums = [1,2,3]
  Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]

### Constraints
- 1 <= nums.length <= 6
- -10 <= nums[i] <= 10
- All the integers of nums are unique.

---

## Concepts Required
- Backtracking
- Recursion
- Arrays

---

## Backtracking Approach
- Build permutations by swapping elements or using a visited array.
- Time Complexity: O(n!)

### Pseudocode
```
permute(nums, path, used):
    if len(path) == len(nums):
        add path to result
    for i in range(len(nums)):
        if not used[i]:
            used[i] = True
            permute(nums, path + [nums[i]], used)
            used[i] = False
```

---

## Python Code
```python
def permute(nums):
    res = []
    def backtrack(path, used):
        if len(path) == len(nums):
            res.append(path[:])
            return
        for i in range(len(nums)):
            if not used[i]:
                used[i] = True
                backtrack(path + [nums[i]], used)
                used[i] = False
    backtrack([], [False]*len(nums))
    return res
```

---

## Key Takeaways
- Backtracking is optimal for generating permutations.
- Practice both swapping and used-array approaches.

---

## Follow-up
- How would you handle duplicates?
  - Sort the array and skip duplicates during backtracking to avoid repeated permutations.
- Can you generate permutations in lexicographic order?
  - Yes, use the next permutation algorithm or backtracking with sorted input to generate permutations in order.

---

## Related Problems
- Permutations II
- Combinations
- Subsets

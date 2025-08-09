# LeetCode: Subsets - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/subsets/description/)

## Problem Statement
Given an integer array nums of unique elements, return all possible subsets (the power set).

### Example
- Input: nums = [1,2,3]
  Output: [[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]

### Constraints
- 1 <= nums.length <= 10
- -10 <= nums[i] <= 10
- All elements of nums are unique.

---

## Concepts Required
- Backtracking
- Bit Manipulation
- Arrays

---

## Backtracking Approach
- For each element, decide to include or not.
- Time Complexity: O(2^n)

### Pseudocode
```
backtrack(start, path):
    add path to result
    for i in range(start, len(nums)):
        backtrack(i+1, path + [nums[i]])
```

---

## Python Code
```python
def subsets(nums):
    res = []
    def backtrack(start, path):
        res.append(path[:])
        for i in range(start, len(nums)):
            backtrack(i+1, path + [nums[i]])
    backtrack(0, [])
    return res
```

---

## Key Takeaways
- Backtracking is optimal for generating all subsets.
- Practice both backtracking and bitmask solutions.

---

## Follow-up
- How would you handle duplicates?
  - Sort input and skip duplicates during backtracking to avoid repeated subsets.
- Can you return only subsets of a certain size?
  - Add a size check in the backtracking recursion to include only subsets of the desired size.

---

## Related Problems
- Subsets II
- Permutations
- Combination Sum

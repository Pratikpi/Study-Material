# LeetCode: Combination Sum - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/combination-sum/description/)

## Problem Statement
Given an array of distinct integers candidates and a target integer target, return a list of all unique combinations of candidates where the chosen numbers sum to target. Each number may be used unlimited times.

### Example
- Input: candidates = [2,3,6,7], target = 7
  Output: [[2,2,3],[7]]

- Input: candidates = [2,3,5], target = 8
  Output: [[2,2,2,2],[2,3,3],[3,5]]

### Constraints
- 1 <= candidates.length <= 30
- 2 <= candidates[i] <= 40
- All elements of candidates are distinct.
- 1 <= target <= 40

---

## Concepts Required
- Backtracking
- Recursion
- Arrays

---

## Backtracking Approach
- Try each candidate, subtract from target, recurse, allow reuse.
- Time Complexity: O(2^n)

### Pseudocode
```
backtrack(remain, comb, start):
    if remain == 0: add comb to result
    for i from start to len(candidates):
        if candidates[i] > remain: continue
        backtrack(remain - candidates[i], comb + [candidates[i]], i)
```

---

## Python Code
```python
def combinationSum(candidates, target):
    res = []
    def backtrack(remain, comb, start):
        if remain == 0:
            res.append(list(comb))
            return
        for i in range(start, len(candidates)):
            if candidates[i] > remain:
                continue
            backtrack(remain - candidates[i], comb + [candidates[i]], i)
    backtrack(target, [], 0)
    return res
```

---

## Key Takeaways
- Backtracking is optimal for combination problems.
- Practice both with and without duplicates.

---

## Follow-up
- How would you handle candidates with duplicates?
- Can you return only the count?

---

## Related Problems
- Combination Sum II
- Subsets
- Permutations

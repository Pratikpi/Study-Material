# LeetCode: First Bad Version - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/first-bad-version/description/)

## Problem Statement
You are a product manager and currently leading a team to develop a new product. Unfortunately, the latest version fails the quality check. Given `n` versions [1, 2, ..., n] and a function `isBadVersion(version)`, find the first bad version.

### Example
- Input: n = 5, bad = 4
  Output: 4

- Input: n = 1, bad = 1
  Output: 1

### Constraints
- 1 <= bad <= n <= 2^31 - 1

---

## Concepts Required
- Binary Search
- Search Space Reduction

---

## Binary Search Approach
- Use binary search to minimize calls to isBadVersion.
- Time Complexity: O(log n)

### Pseudocode
```
left, right = 1, n
while left < right:
    mid = (left + right) // 2
    if isBadVersion(mid):
        right = mid
    else:
        left = mid + 1
return left
```

---

## Python Code
```python
def firstBadVersion(n):
    left, right = 1, n
    while left < right:
        mid = (left + right) // 2
        if isBadVersion(mid):
            right = mid
        else:
            left = mid + 1
    return left
```

---

## Key Takeaways
- Binary search is optimal for minimizing API calls.
- Always check for off-by-one errors in search space problems.

---

## Follow-up
- What if you don't know the value of n?
- Can you generalize to other monotonic functions?

---

## Related Problems
- Search Insert Position
- Find Minimum in Rotated Sorted Array
- Peak Index in a Mountain Array

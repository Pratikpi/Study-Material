# LeetCode: Unique Paths - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/unique-paths/description/)

## Problem Statement
A robot is located at the top-left corner of an m x n grid. The robot can only move either down or right at any point in time. Return the number of possible unique paths to the bottom-right corner.

### Example
- Input: m = 3, n = 7
  Output: 28

- Input: m = 3, n = 2
  Output: 3

### Constraints
- 1 <= m, n <= 100

---

## Concepts Required
- Dynamic Programming
- Combinatorics

---

## DP Approach
- dp[i][j] = dp[i-1][j] + dp[i][j-1]
- Time Complexity: O(m*n)

### Pseudocode
```
dp = [[1]*n for _ in range(m)]
for i in 1..m-1:
    for j in 1..n-1:
        dp[i][j] = dp[i-1][j] + dp[i][j-1]
return dp[m-1][n-1]
```

---

## Python Code
```python
def uniquePaths(m, n):
    dp = [[1]*n for _ in range(m)]
    for i in range(1, m):
        for j in range(1, n):
            dp[i][j] = dp[i-1][j] + dp[i][j-1]
    return dp[-1][-1]
```

---

## Key Takeaways
- DP is optimal for grid path counting.
- Practice both DP and combinatorial (nCr) solutions.

---

## Follow-up
- How would you handle obstacles?
  - Modify DP to set paths to 0 where obstacles are present (as in Unique Paths II).
- Can you do it with O(1) space?
  - Yes, reuse the input grid or a single row/column for DP to achieve O(1) extra space.

---

## Related Problems
- Unique Paths II
- Minimum Path Sum
- Robot Room Cleaner

# LeetCode: Climbing Stairs - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/climbing-stairs/description/)

## Problem Statement
You are climbing a staircase. It takes `n` steps to reach the top. Each time you can climb 1 or 2 steps. In how many distinct ways can you climb to the top?

### Example
- Input: n = 2
  Output: 2
  Explanation: 1+1, 2

- Input: n = 3
  Output: 3
  Explanation: 1+1+1, 1+2, 2+1

### Constraints
- 1 <= n <= 45

---

## Concepts Required
- Dynamic Programming
- Recursion
- Fibonacci Sequence

---

## Dynamic Programming Approach
- The number of ways to reach step n is the sum of ways to reach n-1 and n-2.
- Time Complexity: O(n)

### Pseudocode
```
if n <= 2: return n
a, b = 1, 2
for i in range(3, n+1):
    a, b = b, a + b
return b
```

---

## Python Code
```python
def climbStairs(n):
    if n <= 2:
        return n
    a, b = 1, 2
    for _ in range(3, n+1):
        a, b = b, a + b
    return b
```

---

## Key Takeaways
- This is a classic Fibonacci problem.
- Practice both DP and recursion with memoization.

---

## Follow-up
- How would you solve it with O(1) space?
- Can you generalize to k steps?

---

## Related Problems
- Min Cost Climbing Stairs
- House Robber
- Decode Ways

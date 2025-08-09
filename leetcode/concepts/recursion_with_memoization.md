# Recursion with Memoization - Interview Preparation Guide

## Theory & Intuition
Memoization is an optimization technique used with recursion to store the results of expensive function calls and return the cached result when the same inputs occur again. This avoids redundant calculations and reduces time complexity, often converting exponential time to polynomial time.

- Typically implemented with a hash map or array.
- Used in dynamic programming (top-down approach).

### When to Use
- When a recursive solution has overlapping subproblems.
- Common in problems like Fibonacci, unique paths, coin change, etc.

## Example 1: Fibonacci with Memoization
```python
def fib(n, memo={}):
    if n in memo:
        return memo[n]
    if n <= 1:
        return n
    memo[n] = fib(n-1, memo) + fib(n-2, memo)
    return memo[n]
```

## Example 2: Unique Paths (LeetCode 62)
```python
def unique_paths(m, n, memo={}):
    if m == 1 or n == 1:
        return 1
    if (m, n) in memo:
        return memo[(m, n)]
    memo[(m, n)] = unique_paths(m-1, n, memo) + unique_paths(m, n-1, memo)
    return memo[(m, n)]
```

## Example 3: Coin Change
```python
def coin_change(coins, amount, memo={}):
    if amount == 0:
        return 0
    if amount < 0:
        return float('inf')
    if amount in memo:
        return memo[amount]
    memo[amount] = min(coin_change(coins, amount - coin, memo) + 1 for coin in coins)
    return memo[amount]
```

## Diagram
```
Fibonacci recursion tree (without memoization):
        fib(5)
       /     \
   fib(4)   fib(3)
   ...      ...
With memoization, repeated calls are avoided.
```

## Extra Study Material
- [Memoization (LeetCode Explore)](https://leetcode.com/explore/learn/card/recursion-ii/472/backtracking/2796/)
- [Memoization (GeeksforGeeks)](https://www.geeksforgeeks.org/memoization-1d-2d-and-multidimensional/)

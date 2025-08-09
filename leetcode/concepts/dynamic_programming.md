# Dynamic Programming (DP) - Interview Preparation Guide

## Theory & Intuition
Dynamic Programming (DP) is an optimization technique used to solve problems by breaking them down into overlapping subproblems and storing the results of subproblems to avoid redundant computation.

- **Memoization (Top-Down)**: Store results of recursive calls.
- **Tabulation (Bottom-Up)**: Build up solutions iteratively.
- **Optimal substructure**: The problem can be solved using solutions to subproblems.
- **Overlapping subproblems**: The same subproblems are solved multiple times.

### When to Use
- When a problem can be broken into subproblems that repeat.
- When recursion leads to exponential time due to repeated work.

## Example 1: Fibonacci (Memoization)
```python
def fib(n, memo={}):
    if n <= 1:
        return n
    if n not in memo:
        memo[n] = fib(n-1, memo) + fib(n-2, memo)
    return memo[n]
```

## Example 2: Coin Change (Tabulation)
```python
def coin_change(coins, amount):
    dp = [float('inf')] * (amount + 1)
    dp[0] = 0
    for coin in coins:
        for x in range(coin, amount + 1):
            dp[x] = min(dp[x], dp[x - coin] + 1)
    return dp[amount] if dp[amount] != float('inf') else -1
```

## Example 3: Longest Increasing Subsequence
```python
def lengthOfLIS(nums):
    dp = [1] * len(nums)
    for i in range(len(nums)):
        for j in range(i):
            if nums[i] > nums[j]:
                dp[i] = max(dp[i], dp[j] + 1)
    return max(dp)
```

## Diagram
```
DP Table for Coin Change:
Amount: 0 1 2 3 4 5
DP:     0 1 1 2 2 1
```

## Extra Study Material
- [Dynamic Programming (GeeksforGeeks)](https://www.geeksforgeeks.org/dynamic-programming/)
- [DP Patterns - LeetCode Explore](https://leetcode.com/explore/learn/card/dynamic-programming/)

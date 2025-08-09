# LeetCode: Coin Change - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/coin-change/description/)

## Problem Statement
Given an integer array coins and an integer amount, return the fewest number of coins that you need to make up that amount. If that amount cannot be made up by any combination of the coins, return -1.

### Example
- Input: coins = [1,2,5], amount = 11
  Output: 3
  Explanation: 11 = 5 + 5 + 1

- Input: coins = [2], amount = 3
  Output: -1

### Constraints
- 1 <= coins.length <= 12
- 1 <= coins[i] <= 2^31 - 1
- 0 <= amount <= 10^4

---

## Concepts Required
- Dynamic Programming (DP)
- Coin Change
- Unbounded Knapsack

---

## DP Approach
- dp[i] = min coins to make amount i
- Time Complexity: O(amount * len(coins))

### Pseudocode
```
dp = [inf] * (amount + 1)
dp[0] = 0
for coin in coins:
    for i in coin..amount:
        dp[i] = min(dp[i], dp[i-coin] + 1)
return dp[amount] if dp[amount] != inf else -1
```

---

## Python Code
```python
def coinChange(coins, amount):
    dp = [float('inf')] * (amount + 1)
    dp[0] = 0
    for coin in coins:
        for i in range(coin, amount + 1):
            dp[i] = min(dp[i], dp[i - coin] + 1)
    return dp[amount] if dp[amount] != float('inf') else -1
```

---

## Key Takeaways
- DP is optimal for coin change problems.
- Practice both top-down and bottom-up DP.

---

## Follow-up
- How would you return the actual coins used?
  - Track the last coin used for each amount in a separate array during DP, then backtrack from the target to reconstruct the coins used.
- Can you do it recursively with memoization?
  - Yes, use a recursive function with memoization (cache) to avoid recomputation. Store results for each subproblem to improve efficiency.

---

## Related Problems
- Minimum Coin Change
- Combination Sum IV
- Perfect Squares

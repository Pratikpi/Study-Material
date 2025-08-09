# Knapsack Problem - Interview Preparation Guide

## Theory & Intuition
The knapsack problem is a classic dynamic programming problem where you must maximize the total value of items placed in a knapsack of limited capacity. Each item has a weight and a value. The most common version is the 0/1 knapsack, where each item can be taken at most once.

- **DP Table**: dp[i][w] = max value using first i items and capacity w.
- **Variants**: 0/1 knapsack, unbounded knapsack, fractional knapsack (greedy).
- **Time complexity**: O(nW), where n is number of items, W is capacity.

### When to Use
- When you need to optimize value under a weight/size constraint.
- When the problem involves choices with capacity limits.

## Example 1: 0/1 Knapsack (DP)
```python
def knapsack(weights, values, W):
    n = len(weights)
    dp = [[0]*(W+1) for _ in range(n+1)]
    for i in range(1, n+1):
        for w in range(W+1):
            if weights[i-1] <= w:
                dp[i][w] = max(dp[i-1][w], dp[i-1][w-weights[i-1]] + values[i-1])
            else:
                dp[i][w] = dp[i-1][w]
    return dp[n][W]
```

## Example 2: Unbounded Knapsack
```python
def unbounded_knapsack(weights, values, W):
    dp = [0]*(W+1)
    for w in range(W+1):
        for i in range(len(weights)):
            if weights[i] <= w:
                dp[w] = max(dp[w], dp[w-weights[i]] + values[i])
    return dp[W]
```

## Example 3: Fractional Knapsack (Greedy)
```python
def fractional_knapsack(weights, values, W):
    items = sorted(zip(values, weights), key=lambda x: x[0]/x[1], reverse=True)
    total = 0
    for v, w in items:
        if W >= w:
            total += v
            W -= w
        else:
            total += v * (W/w)
            break
    return total
```

## Diagram
```
Items:  (weight, value)
1: (2, 3)
2: (3, 4)
3: (4, 5)
Capacity: 5
DP Table:
   0 1 2 3 4 5
0 [0 0 0 0 0 0]
1 [0 0 3 3 3 3]
2 [0 0 3 4 4 7]
3 [0 0 3 4 5 7]
```

## Extra Study Material
- [Knapsack Problem (GeeksforGeeks)](https://www.geeksforgeeks.org/0-1-knapsack-problem-dp-10/)
- [Knapsack (LeetCode Discuss)](https://leetcode.com/discuss/general-discussion/1046743/knapsack-problems-summary)

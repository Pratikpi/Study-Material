# LeetCode: Best Time to Buy and Sell Stock - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/)

## Problem Statement
You are given an array `prices` where `prices[i]` is the price of a given stock on the `i`th day. Return the maximum profit you can achieve from one transaction (buy and sell one share). If you cannot achieve any profit, return 0.

### Example
- Input: prices = [7,1,5,3,6,4]
  Output: 5
  Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.

- Input: prices = [7,6,4,3,1]
  Output: 0
  Explanation: No profit can be made.

### Constraints
- 1 <= prices.length <= 10^5
- 0 <= prices[i] <= 10^4

---

## Concepts Required
- Arrays
- Greedy Algorithms
- Dynamic Programming (1D)

---

## Greedy Approach
- Track the minimum price so far and the maximum profit.
- Time Complexity: O(n)

### Pseudocode
```
min_price = inf
max_profit = 0
for price in prices:
    min_price = min(min_price, price)
    max_profit = max(max_profit, price - min_price)
return max_profit
```

---

## Python Code
```python
def maxProfit(prices):
    min_price = float('inf')
    max_profit = 0
    for price in prices:
        min_price = min(min_price, price)
        max_profit = max(max_profit, price - min_price)
    return max_profit
```

---

## Key Takeaways
- Always keep track of the minimum so far for single transaction stock problems.
- Greedy is optimal for this problem.
- Practice variations with multiple transactions.

---

## Follow-up
- What if you can complete as many transactions as you like?
- What if you can only complete at most two transactions?

---

## Related Problems
- Best Time to Buy and Sell Stock II
- Maximum Subarray
- Maximum Profit in Job Scheduling

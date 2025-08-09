# Greedy Algorithms - Interview Preparation Guide

## Theory & Intuition
A greedy algorithm builds up a solution piece by piece, always choosing the next piece that offers the most immediate benefit. It does not reconsider its choices, aiming for local optimums that may lead to a global optimum.

- **No backtracking**: Once a choice is made, it is never changed.
- **Optimal substructure**: The optimal solution to the problem contains optimal solutions to subproblems.
- **Greedy choice property**: A global optimum can be arrived at by selecting a local optimum.

### When to Use
- When the problem has the greedy-choice property and optimal substructure (e.g., activity selection, coin change, interval scheduling).

## Example 1: Activity Selection
```python
def activity_selection(activities):
    activities.sort(key=lambda x: x[1])  # sort by finish time
    res = [activities[0]]
    for act in activities[1:]:
        if act[0] >= res[-1][1]:
            res.append(act)
    return res
```

## Example 2: Coin Change (Greedy)
```python
def coin_change_greedy(coins, amount):
    coins.sort(reverse=True)
    count = 0
    for coin in coins:
        while amount >= coin:
            amount -= coin
            count += 1
    return count if amount == 0 else -1
```

## Example 3: Fractional Knapsack
```python
def fractional_knapsack(weights, values, capacity):
    items = sorted(zip(weights, values), key=lambda x: x[1]/x[0], reverse=True)
    total = 0
    for w, v in items:
        if capacity >= w:
            total += v
            capacity -= w
        else:
            total += v * (capacity / w)
            break
    return total
```

## Diagram
```
Greedy: Always take the best available option at each step.
```

## Extra Study Material
- [Greedy Algorithms (GeeksforGeeks)](https://www.geeksforgeeks.org/greedy-algorithms/)
- [Greedy - LeetCode Explore](https://leetcode.com/tag/greedy/)

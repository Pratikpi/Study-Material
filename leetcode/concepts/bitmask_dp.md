# Bitmask Dynamic Programming (Bitmask DP) - Interview Preparation Guide

## Theory & Intuition
Bitmask DP is a dynamic programming technique where the state is represented using a bitmask (an integer whose bits represent the inclusion/exclusion of elements). It is especially useful for problems involving subsets, permutations, or combinations of a small set (usually n ≤ 20).

- **State compression**: Each bit in the mask represents an element (on/off).
- **DP Table**: dp[mask][...] where mask is a bitmask of used elements.
- **Time complexity**: O(2^n * n) for n elements.

### When to Use
- When the problem involves subsets, permutations, or visiting all nodes (e.g., TSP, assignment problems).
- When n is small (≤ 20).

## Example 1: Traveling Salesman Problem (TSP)
```python
def tsp(graph):
    n = len(graph)
    dp = [[float('inf')]*n for _ in range(1<<n)]
    dp[1][0] = 0
    for mask in range(1<<n):
        for u in range(n):
            if not (mask & (1<<u)):
                continue
            for v in range(n):
                if mask & (1<<v):
                    continue
                dp[mask | (1<<v)][v] = min(dp[mask | (1<<v)][v], dp[mask][u] + graph[u][v])
    return min(dp[(1<<n)-1][i] + graph[i][0] for i in range(n))
```

## Example 2: Count Number of Ways to Partition Set
```python
def count_partitions(n):
    dp = [0]*(1<<n)
    dp[0] = 1
    for mask in range(1<<n):
        for i in range(n):
            if not (mask & (1<<i)):
                dp[mask | (1<<i)] += dp[mask]
    return dp[(1<<n)-1]
```

## Example 3: Minimum Path Cover in DAG
```python
# For small n, use bitmask to represent covered nodes
```

## Diagram
```
Bitmask for n=3: 000, 001, 010, 011, 100, 101, 110, 111
Each bit: 0=not used, 1=used
```

## Extra Study Material
- [Bitmask DP (LeetCode Discuss)](https://leetcode.com/discuss/general-discussion/1075078/bitmask-dp-explained)
- [Bitmask DP (GeeksforGeeks)](https://www.geeksforgeeks.org/dynamic-programming-bitmasking-technique/)

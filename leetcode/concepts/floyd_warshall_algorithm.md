# Floyd-Warshall Algorithm - Interview Preparation Guide

## Theory & Intuition
The Floyd-Warshall algorithm is a dynamic programming technique for finding shortest paths between all pairs of vertices in a weighted graph (with positive or negative edge weights, but no negative cycles). It works by incrementally improving the solution by considering all possible intermediate vertices.

- **All-pairs shortest path**: Computes shortest distances between every pair of nodes.
- **Dynamic programming**: Uses a 2D distance matrix, updating via intermediate nodes.
- **Time complexity**: O(V^3), where V is the number of vertices.

### When to Use
- When you need shortest paths between all pairs of nodes.
- When the graph is dense or you need to detect negative cycles.

## Example 1: Standard Floyd-Warshall Implementation
```python
def floyd_warshall(graph):
    n = len(graph)
    dist = [row[:] for row in graph]
    for k in range(n):
        for i in range(n):
            for j in range(n):
                if dist[i][k] + dist[k][j] < dist[i][j]:
                    dist[i][j] = dist[i][k] + dist[k][j]
    return dist
# graph[i][j] = weight from i to j, or float('inf') if no edge
```

## Example 2: Detecting Negative Cycles
```python
def has_negative_cycle(graph):
    dist = floyd_warshall(graph)
    for i in range(len(graph)):
        if dist[i][i] < 0:
            return True
    return False
```

## Example 3: Path Reconstruction
```python
def floyd_warshall_with_path(graph):
    n = len(graph)
    dist = [row[:] for row in graph]
    next_node = [[j if graph[i][j] != float('inf') else None for j in range(n)] for i in range(n)]
    for k in range(n):
        for i in range(n):
            for j in range(n):
                if dist[i][k] + dist[k][j] < dist[i][j]:
                    dist[i][j] = dist[i][k] + dist[k][j]
                    next_node[i][j] = next_node[i][k]
    return dist, next_node
```

## Diagram
```
Initial matrix:
A  0  3  ∞
B  ∞ 0  1
C  2 ∞  0

After running Floyd-Warshall:
A  0  3  4
B  3  0  1
C  2  5  0
```

## Extra Study Material
- [Floyd-Warshall Algorithm (GeeksforGeeks)](https://www.geeksforgeeks.org/floyd-warshall-algorithm-dp-16/)
- [Floyd-Warshall (LeetCode Discuss)](https://leetcode.com/discuss/general-discussion/1127235/floyd-warshall-algorithm-explained)

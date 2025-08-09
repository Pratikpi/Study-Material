# Recursion with BFS (Breadth-First Search) - Interview Preparation Guide

## Theory & Intuition
Breadth-First Search (BFS) is a graph/tree traversal technique that explores all neighbors at the current depth before moving to the next level. BFS is typically implemented with a queue, but recursive BFS is rare and usually simulated with helper functions.

- Used for shortest path, level order traversal, and connected components.
- BFS is iterative by nature, but recursion can be used for level-order traversal in trees.

### When to Use
- When you need to find the shortest path or traverse level by level.
- When the problem requires visiting nodes in increasing order of distance from the source.

## Example 1: Level Order Traversal (Binary Tree)
```python
def level_order(root):
    res = []
    def helper(node, level):
        if not node:
            return
        if len(res) == level:
            res.append([])
        res[level].append(node.val)
        helper(node.left, level+1)
        helper(node.right, level+1)
    helper(root, 0)
    return res
```

## Example 2: BFS on a Graph (Iterative)
```python
from collections import deque
def bfs(graph, start):
    visited = set([start])
    q = deque([start])
    while q:
        node = q.popleft()
        for neighbor in graph[node]:
            if neighbor not in visited:
                visited.add(neighbor)
                q.append(neighbor)
```

## Example 3: Shortest Path in Unweighted Graph
```python
from collections import deque
def shortest_path(graph, start, end):
    q = deque([(start, 0)])
    visited = set([start])
    while q:
        node, dist = q.popleft()
        if node == end:
            return dist
        for neighbor in graph[node]:
            if neighbor not in visited:
                visited.add(neighbor)
                q.append((neighbor, dist+1))
    return -1
```

## Diagram
```
BFS Traversal:
Level 0: [A]
Level 1: [B, C]
Level 2: [D, E, F]
```

## Extra Study Material
- [BFS (LeetCode Explore)](https://leetcode.com/explore/learn/card/graph/619/breadth-first-search-in-graph/)
- [BFS (GeeksforGeeks)](https://www.geeksforgeeks.org/breadth-first-search-or-bfs-for-a-graph/)

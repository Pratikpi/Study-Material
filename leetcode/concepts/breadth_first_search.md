# Breadth-First Search (BFS) - Interview Preparation Guide

## Theory & Intuition
Breadth-First Search (BFS) is an algorithm for traversing or searching tree or graph data structures. It explores all neighbors at the present depth before moving on to nodes at the next depth level.

- **Queue-based**: Uses a queue to track nodes to visit.
- **Level-order traversal**: Visits nodes level by level.

### When to Use
- When you need the shortest path in unweighted graphs.
- When you want to explore all nodes at a certain "distance" from the start.

## Example 1: BFS in a Graph
```python
from collections import deque
def bfs(graph, start):
    visited = set([start])
    queue = deque([start])
    while queue:
        node = queue.popleft()
        print(node)
        for neighbor in graph[node]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)
```

## Example 2: BFS in a Binary Tree (Level Order)
```python
from collections import deque
def level_order(root):
    if not root:
        return []
    queue = deque([root])
    res = []
    while queue:
        node = queue.popleft()
        res.append(node.val)
        if node.left:
            queue.append(node.left)
        if node.right:
            queue.append(node.right)
    return res
```

## Example 3: Shortest Path in Unweighted Graph
```python
def shortest_path(graph, start, end):
    from collections import deque
    queue = deque([(start, 0)])
    visited = set([start])
    while queue:
        node, dist = queue.popleft()
        if node == end:
            return dist
        for neighbor in graph[node]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append((neighbor, dist+1))
    return -1
```

## Diagram
```
Graph: 0-1-2-3
BFS Order: 0, 1, 2, 3
```

## Extra Study Material
- [Breadth-First Search (GeeksforGeeks)](https://www.geeksforgeeks.org/breadth-first-search-or-bfs-for-a-graph/)
- [BFS - LeetCode Explore](https://leetcode.com/explore/learn/card/queue-stack/239/conclusion/1393/)

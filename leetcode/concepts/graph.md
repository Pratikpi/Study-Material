# Graph - Interview Preparation Guide

## Theory & Intuition
A graph is a collection of nodes (vertices) and edges connecting pairs of nodes. Graphs can be directed or undirected, weighted or unweighted, and are used to model relationships and networks.

- **Adjacency list**: Common way to represent graphs in code.
- **Adjacency matrix**: 2D array for dense graphs.
- **Directed/Undirected**: Edges have direction or not.
- **Weighted/Unweighted**: Edges may have weights.

### When to Use
- When modeling relationships, networks, or connections (e.g., social networks, maps).

## Example 1: Adjacency List Representation
```python
graph = {
    0: [1, 2],
    1: [0, 3],
    2: [0],
    3: [1]
}
```

## Example 2: BFS Traversal
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

## Example 3: DFS Traversal
```python
def dfs(graph, node, visited=None):
    if visited is None:
        visited = set()
    visited.add(node)
    print(node)
    for neighbor in graph[node]:
        if neighbor not in visited:
            dfs(graph, neighbor, visited)
```

## Diagram
```
0---1
|   |
2   3
```

## Extra Study Material
- [Graph Data Structure (GeeksforGeeks)](https://www.geeksforgeeks.org/graph-data-structure-and-algorithms/)
- [Graph - LeetCode Explore](https://leetcode.com/explore/learn/card/graph/)

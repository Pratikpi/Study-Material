# Depth-First Search (DFS) - Interview Preparation Guide

## Theory & Intuition
Depth-First Search (DFS) is an algorithm for traversing or searching tree or graph data structures. It explores as far as possible along each branch before backtracking.

- **Stack-based**: Uses recursion or an explicit stack.
- **Preorder, inorder, postorder**: For trees, DFS can be in different orders.

### When to Use
- When you need to explore all possible paths (e.g., backtracking, connected components).
- When you want to check for cycles or connectivity.

## Example 1: DFS in a Graph (Recursive)
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

## Example 2: DFS in a Binary Tree (Preorder)
```python
def preorder(root):
    if not root:
        return
    print(root.val)
    preorder(root.left)
    preorder(root.right)
```

## Example 3: Connected Components in a Graph
```python
def count_components(n, edges):
    graph = {i: [] for i in range(n)}
    for u, v in edges:
        graph[u].append(v)
        graph[v].append(u)
    visited = set()
    def dfs(u):
        visited.add(u)
        for v in graph[u]:
            if v not in visited:
                dfs(v)
    count = 0
    for i in range(n):
        if i not in visited:
            dfs(i)
            count += 1
    return count
```

## Diagram
```
Graph: 0-1-2-3
DFS Order: 0, 1, 2, 3
```

## Extra Study Material
- [Depth-First Search (GeeksforGeeks)](https://www.geeksforgeeks.org/depth-first-search-or-dfs-for-a-graph/)
- [DFS - LeetCode Explore](https://leetcode.com/explore/learn/card/graph/619/depth-first-search/)

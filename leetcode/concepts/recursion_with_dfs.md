# Recursion with DFS (Depth-First Search) - Interview Preparation Guide

## Theory & Intuition
Depth-First Search (DFS) is a graph/tree traversal technique that explores as far as possible along each branch before backtracking. When implemented recursively, DFS is concise and leverages the call stack for traversal.

- Used for traversing or searching tree/graph data structures.
- Can be used to detect cycles, connected components, and solve puzzles.

### When to Use
- When you need to explore all possible paths or components in a graph/tree.
- When the problem requires backtracking or pathfinding.

## Example 1: DFS on a Binary Tree
```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def dfs(root):
    if not root:
        return
    print(root.val)
    dfs(root.left)
    dfs(root.right)
```

## Example 2: DFS on a Graph
```python
def dfs_graph(graph, node, visited=None):
    if visited is None:
        visited = set()
    if node in visited:
        return
    visited.add(node)
    for neighbor in graph[node]:
        dfs_graph(graph, neighbor, visited)
```

## Example 3: Number of Islands (LeetCode 200)
```python
def num_islands(grid):
    def dfs(r, c):
        if r < 0 or r >= len(grid) or c < 0 or c >= len(grid[0]) or grid[r][c] != '1':
            return
        grid[r][c] = '#'
        for dr, dc in [(0,1),(1,0),(-1,0),(0,-1)]:
            dfs(r+dr, c+dc)
    count = 0
    for r in range(len(grid)):
        for c in range(len(grid[0])):
            if grid[r][c] == '1':
                dfs(r, c)
                count += 1
    return count
```

## Diagram
```
DFS Traversal:
Start -> Left -> Left ... Backtrack -> Right
```

## Extra Study Material
- [DFS (LeetCode Explore)](https://leetcode.com/explore/learn/card/graph/619/depth-first-search-in-graph/)
- [DFS (GeeksforGeeks)](https://www.geeksforgeeks.org/depth-first-search-or-dfs-for-a-graph/)

# LeetCode: Number of Islands - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/number-of-islands/description/)

## Problem Statement
Given a 2D grid map of '1's (land) and '0's (water), count the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically.

### Example
- Input: grid = [
  ["1","1","1","1","0"],
  ["1","1","0","1","0"],
  ["1","1","0","0","0"],
  ["0","0","0","0","0"]
]
  Output: 1

- Input: grid = [
  ["1","1","0","0","0"],
  ["1","1","0","0","0"],
  ["0","0","1","0","0"],
  ["0","0","0","1","1"]
]
  Output: 3

### Constraints
- m == grid.length
- n == grid[i].length
- 1 <= m, n <= 300
- grid[i][j] is '0' or '1'.

---

## Concepts Required
- Depth-First Search (DFS)
- Breadth-First Search (BFS)
- Matrix Traversal

---

## DFS Approach
- For each land cell, run DFS to mark all connected land.
- Time Complexity: O(m * n)

### Pseudocode
```
count = 0
for each cell in grid:
    if cell is land:
        dfs(cell)
        count += 1
dfs(cell):
    mark cell as visited
    for each neighbor:
        if neighbor is land:
            dfs(neighbor)
return count
```

---

## Python Code
```python
def numIslands(grid):
    if not grid: return 0
    m, n = len(grid), len(grid[0])
    def dfs(r, c):
        if r<0 or r>=m or c<0 or c>=n or grid[r][c]!='1':
            return
        grid[r][c] = '0'
        for dr, dc in [(-1,0),(1,0),(0,-1),(0,1)]:
            dfs(r+dr, c+dc)
    count = 0
    for r in range(m):
        for c in range(n):
            if grid[r][c] == '1':
                dfs(r, c)
                count += 1
    return count
```

---

## Key Takeaways
- DFS/BFS is optimal for connected component counting in grids.
- Always mark visited cells to avoid cycles.

---

## Follow-up
- How would you use BFS?
- Can you use Union-Find?

---

## Related Problems
- 01 Matrix
- Surrounded Regions
- Walls and Gates

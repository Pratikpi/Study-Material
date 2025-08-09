# LeetCode: Rotting Oranges - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/rotting-oranges/description/)

## Problem Statement
Given a grid of oranges, each cell can be empty, have a fresh orange, or a rotten orange. Every minute, any fresh orange adjacent to a rotten one becomes rotten. Return the minimum number of minutes until no cell has a fresh orange. If impossible, return -1.

### Example
- Input: grid = [[2,1,1],[1,1,0],[0,1,1]]
  Output: 4

- Input: grid = [[2,1,1],[0,1,1],[1,0,1]]
  Output: -1

### Constraints
- 1 <= grid.length, grid[0].length <= 10^2
- 0 <= grid[i][j] <= 2

---

## Concepts Required
- Breadth-First Search (BFS)
- Matrix Traversal
- Queue

---

## BFS Approach
- Start BFS from all rotten oranges, count minutes as levels.
- Time Complexity: O(m * n)

### Pseudocode
```
queue = all rotten oranges
fresh = count of fresh oranges
minutes = 0
while queue and fresh > 0:
    for each orange in queue:
        rot adjacent fresh oranges
        decrease fresh count
        add to queue
    minutes += 1
return minutes if fresh == 0 else -1
```

---

## Python Code
```python
from collections import deque

def orangesRotting(grid):
    rows, cols = len(grid), len(grid[0])
    queue = deque()
    fresh = 0
    for r in range(rows):
        for c in range(cols):
            if grid[r][c] == 2:
                queue.append((r, c))
            elif grid[r][c] == 1:
                fresh += 1
    minutes = 0
    while queue and fresh > 0:
        for _ in range(len(queue)):
            r, c = queue.popleft()
            for dr, dc in [(-1,0),(1,0),(0,-1),(0,1)]:
                nr, nc = r+dr, c+dc
                if 0<=nr<rows and 0<=nc<cols and grid[nr][nc]==1:
                    grid[nr][nc]=2
                    fresh -= 1
                    queue.append((nr, nc))
        minutes += 1
    return minutes if fresh == 0 else -1
```

---

## Key Takeaways
- BFS is optimal for multi-source shortest path in grids.
- Always check for impossible cases.

---

## Follow-up
- How would you handle diagonals?
  - Add diagonal directions to the BFS traversal (i.e., 8 directions instead of 4).
- Can you do it in-place?
  - Yes, use the grid itself to track time or state changes, marking cells with the minute they rot or a special marker.

---

## Related Problems
- 01 Matrix
- Number of Islands
- Walls and Gates

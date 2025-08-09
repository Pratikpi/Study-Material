# LeetCode: 01 Matrix - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/01-matrix/description/)

## Problem Statement
Given an m x n binary matrix mat, return the distance of the nearest 0 for each cell.

The distance between two adjacent cells is 1.

### Example
- Input: mat = [[0,0,0],[0,1,0],[1,1,1]]
  Output: [[0,0,0],[0,1,0],[1,2,1]]

### Constraints
- m == mat.length
- n == mat[i].length
- 1 <= m, n <= 10^4
- 1 <= m * n <= 10^4
- mat[i][j] is either 0 or 1.
- There is at least one 0 in mat.

---

## Concepts Required
- Breadth-First Search (BFS)
- Matrix Traversal
- Dynamic Programming

---

## BFS Approach
- Start BFS from all 0s, update distances for 1s.
- Time Complexity: O(m * n)

### Pseudocode
```
queue = all positions with 0
for each cell in mat:
    if cell == 1: set to inf
while queue:
    i, j = queue.pop()
    for each neighbor:
        if mat[ni][nj] > mat[i][j] + 1:
            mat[ni][nj] = mat[i][j] + 1
            queue.append((ni, nj))
return mat
```

---

## Python Code
```python
from collections import deque

def updateMatrix(mat):
    m, n = len(mat), len(mat[0])
    queue = deque()
    for i in range(m):
        for j in range(n):
            if mat[i][j] == 0:
                queue.append((i, j))
            else:
                mat[i][j] = float('inf')
    for i, j in queue:
        for di, dj in [(-1,0),(1,0),(0,-1),(0,1)]:
            ni, nj = i+di, j+dj
            if 0<=ni<m and 0<=nj<n and mat[ni][nj] > mat[i][j] + 1:
                mat[ni][nj] = mat[i][j] + 1
                queue.append((ni, nj))
    return mat
```

---

## Key Takeaways
- BFS from all 0s is optimal for shortest distance in unweighted grid.
- Practice both BFS and DP approaches.

---

## Follow-up
- How would you solve it with DP only?
- Can you do it in-place?

---

## Related Problems
- Walls and Gates
- Shortest Path in Binary Matrix
- Rotting Oranges

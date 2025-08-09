# Matrix Traversal - Interview Preparation Guide

## Theory & Intuition
Matrix traversal refers to systematically visiting each cell in a 2D grid (matrix). Traversal can be row-wise, column-wise, or in more complex patterns (spiral, diagonal, zigzag).

- **Row/Column traversal**: Visit all cells in a row or column.
- **DFS/BFS**: For connected components, islands, or flood fill.
- **Boundary checks**: Always check for valid indices.

### When to Use
- When working with 2D grids (e.g., image processing, board games, islands problems).

## Example 1: Row-wise and Column-wise Traversal
```python
def row_col_traversal(matrix):
    for i in range(len(matrix)):
        for j in range(len(matrix[0])):
            print(matrix[i][j])
```

## Example 2: Spiral Order Traversal
```python
def spiral_order(matrix):
    res = []
    if not matrix: return res
    top, bottom, left, right = 0, len(matrix)-1, 0, len(matrix[0])-1
    while top <= bottom and left <= right:
        for j in range(left, right+1):
            res.append(matrix[top][j])
        top += 1
        for i in range(top, bottom+1):
            res.append(matrix[i][right])
        right -= 1
        if top <= bottom:
            for j in range(right, left-1, -1):
                res.append(matrix[bottom][j])
            bottom -= 1
        if left <= right:
            for i in range(bottom, top-1, -1):
                res.append(matrix[i][left])
            left += 1
    return res
```

## Example 3: Flood Fill (DFS)
```python
def flood_fill(matrix, x, y, new_color):
    orig = matrix[x][y]
    if orig == new_color: return
    def dfs(i, j):
        if (i < 0 or i >= len(matrix) or j < 0 or j >= len(matrix[0]) or matrix[i][j] != orig):
            return
        matrix[i][j] = new_color
        for dx, dy in [(-1,0),(1,0),(0,-1),(0,1)]:
            dfs(i+dx, j+dy)
    dfs(x, y)
```

## Diagram
```
Matrix:
1 2 3
4 5 6
7 8 9
```

## Extra Study Material
- [Matrix Traversal (GeeksforGeeks)](https://www.geeksforgeeks.org/print-matrix-in-diagonal-pattern/)
- [Spiral Matrix - LeetCode](https://leetcode.com/problems/spiral-matrix/)

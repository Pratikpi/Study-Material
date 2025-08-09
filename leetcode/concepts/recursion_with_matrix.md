# Recursion with Matrix - Interview Preparation Guide

## Theory & Intuition
Many matrix/grid problems can be solved using recursion, especially when exploring connected regions, searching, or filling. Recursion is used to traverse cells, mark visited, and backtrack as needed.

- Used for flood fill, island counting, pathfinding, and region labeling.
- Be careful with boundaries and visited cells to avoid infinite recursion.

### When to Use
- When you need to explore or modify connected regions in a grid.
- When the problem involves 2D traversal with constraints.

## Example 1: Flood Fill
```python
def flood_fill(image, sr, sc, newColor):
    orig = image[sr][sc]
    if orig == newColor:
        return image
    def dfs(r, c):
        if (0 <= r < len(image) and 0 <= c < len(image[0]) and image[r][c] == orig):
            image[r][c] = newColor
            for dr, dc in [(-1,0),(1,0),(0,-1),(0,1)]:
                dfs(r+dr, c+dc)
    dfs(sr, sc)
    return image
```

## Example 2: Number of Islands
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

## Example 3: Word Search
```python
def exist(board, word):
    def dfs(r, c, idx):
        if idx == len(word):
            return True
        if (r < 0 or r >= len(board) or c < 0 or c >= len(board[0]) or board[r][c] != word[idx]):
            return False
        tmp, board[r][c] = board[r][c], '#'
        found = any(dfs(r+dr, c+dc, idx+1) for dr, dc in [(-1,0),(1,0),(0,-1),(0,1)])
        board[r][c] = tmp
        return found
    for r in range(len(board)):
        for c in range(len(board[0])):
            if dfs(r, c, 0):
                return True
    return False
```

## Diagram
```
Grid traversal:
[1,1,0]
[0,1,0]
[0,0,1]
```

## Extra Study Material
- [Matrix Recursion (LeetCode)](https://leetcode.com/tag/matrix/)
- [Matrix Recursion (GeeksforGeeks)](https://www.geeksforgeeks.org/matrix-questions-for-interviews/)

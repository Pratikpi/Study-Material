# LeetCode: Flood Fill - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/flood-fill/description/)

## Problem Statement
You are given an image represented by an `m x n` grid of integers `image`, where `image[i][j]` represents the pixel value of the image. You are also given three integers `sr`, `sc`, and `color`. Perform a flood fill on the image starting from the pixel `image[sr][sc]`.

Flood fill changes the color of the starting pixel and all adjacent pixels (up, down, left, right) with the same original color to the new color.

### Example
- Input: image = [[1,1,1],[1,1,0],[1,0,1]], sr = 1, sc = 1, color = 2
  Output: [[2,2,2],[2,2,0],[2,0,1]]

- Input: image = [[0,0,0],[0,0,0]], sr = 0, sc = 0, color = 0
  Output: [[0,0,0],[0,0,0]]

### Constraints
- 1 <= m, n <= 50
- 0 <= image[i][j], color < 2^16
- 0 <= sr < m
- 0 <= sc < n

---

## Concepts Required
- Depth-First Search (DFS)
- Breadth-First Search (BFS)
- Matrix Traversal

---

## DFS Approach
- Use DFS to visit all connected pixels with the same color and change them.
- Time Complexity: O(m * n)

### Pseudocode
```
if image[sr][sc] == color: return image
dfs(r, c):
    if out of bounds or image[r][c] != old_color: return
    image[r][c] = color
    for each neighbor: dfs(neighbor)
dfs(sr, sc)
return image
```

---

## Python Code
```python
def floodFill(image, sr, sc, color):
    old_color = image[sr][sc]
    if old_color == color: return image
    def dfs(r, c):
        if (r < 0 or r >= len(image) or c < 0 or c >= len(image[0]) or image[r][c] != old_color):
            return
        image[r][c] = color
        for dr, dc in [(-1,0),(1,0),(0,-1),(0,1)]:
            dfs(r+dr, c+dc)
    dfs(sr, sc)
    return image
```

---

## Key Takeaways
- DFS and BFS are both valid for flood fill.
- Always check for already-filled color to avoid infinite recursion.
- Practice both recursive and iterative (queue) solutions.

---

## Follow-up
- How would you implement this with BFS?
- What if diagonal neighbors are also considered?

---

## Related Problems
- Number of Islands
- Surrounded Regions
- Island Perimeter

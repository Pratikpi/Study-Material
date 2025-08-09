# LeetCode: Spiral Matrix - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/spiral-matrix/description/)

## Problem Statement
Given an m x n matrix, return all elements of the matrix in spiral order.

### Example
- Input: matrix = [[1,2,3],[4,5,6],[7,8,9]]
  Output: [1,2,3,6,9,8,7,4,5]

### Constraints
- m == matrix.length
- n == matrix[i].length
- 1 <= m, n <= 10

---

## Concepts Required
- Matrix Traversal
- Simulation
- Arrays

---

## Simulation Approach
- Use four pointers to track boundaries, traverse in spiral.
- Time Complexity: O(m*n)

### Pseudocode
```
left, right, top, bottom = 0, n-1, 0, m-1
while left <= right and top <= bottom:
    traverse top row
    traverse right col
    traverse bottom row
    traverse left col
    move boundaries
```

---

## Python Code
```python
def spiralOrder(matrix):
    res = []
    if not matrix: return res
    top, bottom, left, right = 0, len(matrix)-1, 0, len(matrix[0])-1
    while left <= right and top <= bottom:
        for i in range(left, right+1):
            res.append(matrix[top][i])
        top += 1
        for i in range(top, bottom+1):
            res.append(matrix[i][right])
        right -= 1
        if top <= bottom:
            for i in range(right, left-1, -1):
                res.append(matrix[bottom][i])
            bottom -= 1
        if left <= right:
            for i in range(bottom, top-1, -1):
                res.append(matrix[i][left])
            left += 1
    return res
```

---

## Key Takeaways
- Simulation is optimal for spiral traversal.
- Practice both simulation and recursive solutions.

---

## Follow-up
- How would you handle jagged matrices?
  - Check bounds for each row/column access to avoid index errors.
- Can you do it in-place?
  - Yes, if allowed to overwrite visited cells or use markers to track progress.

---

## Related Problems
- Spiral Matrix II
- Rotate Image
- Diagonal Traverse

# Backtracking - Interview Preparation Guide

## Theory & Intuition
Backtracking is a general algorithmic technique for solving problems recursively by trying to build a solution incrementally, removing solutions that fail to satisfy the constraints of the problem at any point ("backtrack").

- **Recursive exploration**: Try all possibilities, backtrack if constraints are violated.
- **Pruning**: Stop exploring a path as soon as it is invalid.

### When to Use
- When you need to generate all combinations, permutations, or subsets.
- When the problem involves constraints (e.g., Sudoku, N-Queens).

## Example 1: Subsets
```python
def subsets(nums):
    res = []
    def backtrack(start, path):
        res.append(path[:])
        for i in range(start, len(nums)):
            path.append(nums[i])
            backtrack(i+1, path)
            path.pop()
    backtrack(0, [])
    return res
```

## Example 2: Permutations
```python
def permute(nums):
    res = []
    def backtrack(path, used):
        if len(path) == len(nums):
            res.append(path[:])
            return
        for i in range(len(nums)):
            if used[i]: continue
            used[i] = True
            path.append(nums[i])
            backtrack(path, used)
            path.pop()
            used[i] = False
    backtrack([], [False]*len(nums))
    return res
```

## Example 3: N-Queens
```python
def solveNQueens(n):
    res = []
    board = [['.']*n for _ in range(n)]
    def is_valid(r, c):
        for i in range(r):
            if board[i][c] == 'Q': return False
            if c-(r-i) >= 0 and board[i][c-(r-i)] == 'Q': return False
            if c+(r-i) < n and board[i][c+(r-i)] == 'Q': return False
        return True
    def backtrack(r):
        if r == n:
            res.append([''.join(row) for row in board])
            return
        for c in range(n):
            if is_valid(r, c):
                board[r][c] = 'Q'
                backtrack(r+1)
                board[r][c] = '.'
    backtrack(0)
    return res
```

## Diagram
```
Backtracking tree for permutations:
         []
      /  |  \
    [1] [2] [3]
   ...
```

## Extra Study Material
- [Backtracking (LeetCode)](https://leetcode.com/tag/backtracking/)
- [Backtracking (GeeksforGeeks)](https://www.geeksforgeeks.org/backtracking-algorithms/)

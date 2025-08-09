# Recursion with Backtracking - Interview Preparation Guide

## Theory & Intuition
Backtracking is a general algorithm for finding all (or some) solutions to problems by incrementally building candidates and abandoning a candidate as soon as it is determined to be invalid. It is implemented using recursion and is often used for combinatorial problems.

- Explore all possible options, revert (backtrack) when a path is invalid.
- Used in permutations, combinations, subsets, N-Queens, Sudoku, etc.

### When to Use
- When you need to generate all possible solutions or search for a valid one among many.
- When the problem can be modeled as a decision tree.

## Example 1: Subsets (LeetCode 78)
```python
def subsets(nums):
    res = []
    def backtrack(path, idx):
        res.append(path[:])
        for i in range(idx, len(nums)):
            path.append(nums[i])
            backtrack(path, i + 1)
            path.pop()
    backtrack([], 0)
    return res
```

## Example 2: Permutations (LeetCode 46)
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
def solve_n_queens(n):
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
Decision tree:
Start -> [Option1] -> [Option2] ...
         |             |
      Backtrack     Backtrack
```

## Extra Study Material
- [Backtracking (LeetCode Explore)](https://leetcode.com/explore/learn/card/recursion-ii/472/backtracking/)
- [Backtracking (GeeksforGeeks)](https://www.geeksforgeeks.org/backtracking-algorithms/)

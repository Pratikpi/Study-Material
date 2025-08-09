# LeetCode: Word Search - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/word-search/description/)

## Problem Statement
Given an m x n board and a word, return true if the word exists in the grid. The word can be constructed from letters of sequentially adjacent cells, where adjacent cells are horizontally or vertically neighboring. The same letter cell may not be used more than once.

### Example
- Input: board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "ABCCED"
  Output: true

- Input: board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "SEE"
  Output: true

- Input: board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "ABCB"
  Output: false

### Constraints
- 1 <= board.length, board[i].length <= 6
- 1 <= word.length <= 15
- board and word consists of only lowercase and uppercase English letters.

---

## Concepts Required
- Backtracking
- DFS
- Matrix Traversal

---

## Backtracking Approach
- For each cell, start DFS if first letter matches, mark visited.
- Time Complexity: O(m*n*3^L), L = word length

### Pseudocode
```
for each cell in board:
    if dfs(cell, 0): return True
dfs(r, c, i):
    if i == len(word): return True
    if out of bounds or board[r][c] != word[i]: return False
    mark visited
    for each neighbor: if dfs(neighbor, i+1): return True
    unmark visited
return False
```

---

## Python Code
```python
def exist(board, word):
    m, n = len(board), len(board[0])
    def dfs(r, c, i):
        if i == len(word): return True
        if r<0 or r>=m or c<0 or c>=n or board[r][c] != word[i]: return False
        tmp, board[r][c] = board[r][c], '#'
        found = (dfs(r+1,c,i+1) or dfs(r-1,c,i+1) or dfs(r,c+1,i+1) or dfs(r,c-1,i+1))
        board[r][c] = tmp
        return found
    for r in range(m):
        for c in range(n):
            if dfs(r, c, 0): return True
    return False
```

---

## Key Takeaways
- Backtracking is optimal for word search in grids.
- Always mark/unmark visited cells.

---

## Follow-up
- How would you search for multiple words?
  - Use a Trie to store all words and perform DFS from each cell, pruning paths that do not match any word prefix.
- Can you use a Trie for optimization?
  - Yes, a Trie allows efficient prefix checking and early termination during DFS.

---

## Related Problems
- Word Search II
- Number of Islands
- Letter Combinations of a Phone Number

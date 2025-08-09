# LeetCode: Invert Binary Tree - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/invert-binary-tree/description/)

## Problem Statement
Given the `root` of a binary tree, invert the tree, and return its root (mirror the tree).

### Example
- Input: root = [4,2,7,1,3,6,9]
  Output: [4,7,2,9,6,3,1]

- Input: root = [2,1,3]
  Output: [2,3,1]

- Input: root = []
  Output: []

### Constraints
- The number of nodes in the tree is in the range [0, 100].
- -100 <= Node.val <= 100

---

## Concepts Required
- Binary Tree
- Recursion
- Depth-First Search (DFS)

---

## Recursive Approach
- Swap the left and right children of every node.
- Use recursion to traverse the tree.
- Time Complexity: O(n)

### Pseudocode
```
if root is None:
    return None
swap left and right
invert left
invert right
return root
```

---

## Python Code
```python
def invertTree(root):
    if not root:
        return None
    root.left, root.right = invertTree(root.right), invertTree(root.left)
    return root
```

---

## Key Takeaways
- Recursion is a natural fit for tree problems.
- Swapping left and right at each node in DFS order inverts the tree.
- Practice both recursive and iterative (using a queue) solutions.

---

## Follow-up
- Can you invert the tree iteratively using a queue (BFS)?

---

## Related Problems
- Maximum Depth of Binary Tree
- Symmetric Tree
- Same Tree

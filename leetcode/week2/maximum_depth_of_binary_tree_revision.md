# LeetCode: Maximum Depth of Binary Tree - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/maximum-depth-of-binary-tree/description/)

## Problem Statement
Given the `root` of a binary tree, return its maximum depth.

The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

### Example
- Input: root = [3,9,20,null,null,15,7]
  Output: 3

- Input: root = [1,null,2]
  Output: 2

### Constraints
- The number of nodes in the tree is in the range [0, 10^4].
- -100 <= Node.val <= 100

---

## Concepts Required
- Binary Tree
- Recursion
- Depth-First Search (DFS)

---

## Recursive DFS Approach
- Recursively compute the depth of left and right subtrees.
- Time Complexity: O(n)

### Pseudocode
```
if not root: return 0
return 1 + max(depth(root.left), depth(root.right))
```

---

## Python Code
```python
def maxDepth(root):
    if not root:
        return 0
    return 1 + max(maxDepth(root.left), maxDepth(root.right))
```

---

## Key Takeaways
- Recursion is natural for tree depth problems.
- Practice both recursive and iterative (BFS) solutions.

---

## Follow-up
- How would you solve it using BFS?
- Can you do it iteratively?

---

## Related Problems
- Minimum Depth of Binary Tree
- Balanced Binary Tree
- Diameter of Binary Tree

# LeetCode: Validate Binary Search Tree - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/validate-binary-search-tree/description/)

## Problem Statement
Given the root of a binary tree, determine if it is a valid binary search tree (BST).

A valid BST is defined as follows:
- The left subtree of a node contains only nodes with keys less than the node's key.
- The right subtree only nodes with keys greater than the node's key.
- Both subtrees must also be BSTs.

### Example
- Input: root = [2,1,3]
  Output: true

- Input: root = [5,1,4,null,null,3,6]
  Output: false

### Constraints
- The number of nodes in the tree is in the range [1, 10^4].
- -2^31 <= Node.val <= 2^31 - 1

---

## Concepts Required
- Binary Tree
- Recursion
- Inorder Traversal

---

## Recursive Bounds Approach
- Pass down min and max bounds for each node.
- Time Complexity: O(n)

### Pseudocode
```
validate(node, min, max):
    if not node: return True
    if node.val <= min or node.val >= max: return False
    return validate(node.left, min, node.val) and validate(node.right, node.val, max)
```

---

## Python Code
```python
def isValidBST(root):
    def validate(node, low, high):
        if not node:
            return True
        if node.val <= low or node.val >= high:
            return False
        return validate(node.left, low, node.val) and validate(node.right, node.val, high)
    return validate(root, float('-inf'), float('inf'))
```

---

## Key Takeaways
- Always use strict < and > for BST validation.
- Practice both recursive and inorder traversal approaches.

---

## Follow-up
- How would you validate an iterative solution?
  - Use a stack to perform iterative inorder traversal, checking that each value is greater than the previous value seen.
- Can you do it with inorder traversal?
  - Yes, inorder traversal of a BST should yield a strictly increasing sequence. If any value is not greater than the previous, the tree is not a valid BST.

---

## Related Problems
- Recover Binary Search Tree
- Kth Smallest Element in a BST
- Binary Tree Inorder Traversal

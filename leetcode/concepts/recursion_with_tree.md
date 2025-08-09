# Recursion with Tree - Interview Preparation Guide

## Theory & Intuition
Recursion is a natural fit for tree problems because trees are recursively defined structures. Many tree algorithms (traversals, height, balance, etc.) are most easily and cleanly implemented with recursion.

- Each recursive call processes a node and recurses on its children.
- Used for traversals (inorder, preorder, postorder), computing height, checking balance, etc.

### When to Use
- When the problem involves hierarchical or nested data (trees, XML, etc.).
- When you need to process all nodes or aggregate information from subtrees.

## Example 1: Inorder Traversal
```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def inorder(root):
    if not root:
        return []
    return inorder(root.left) + [root.val] + inorder(root.right)
```

## Example 2: Compute Tree Height
```python
def tree_height(root):
    if not root:
        return 0
    return 1 + max(tree_height(root.left), tree_height(root.right))
```

## Example 3: Check if Tree is Balanced
```python
def is_balanced(root):
    def check(node):
        if not node:
            return 0
        left = check(node.left)
        if left == -1:
            return -1
        right = check(node.right)
        if right == -1:
            return -1
        if abs(left - right) > 1:
            return -1
        return 1 + max(left, right)
    return check(root) != -1
```

## Diagram
```
    1
   / \
  2   3
 / \
4   5
```

## Extra Study Material
- [Tree Recursion (LeetCode Explore)](https://leetcode.com/explore/learn/card/data-structure-tree/)
- [Tree Recursion (GeeksforGeeks)](https://www.geeksforgeeks.org/recursive-tree-traversals/)

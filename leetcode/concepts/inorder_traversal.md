# Inorder Traversal - Interview Preparation Guide

## Theory & Intuition
Inorder traversal is a method of visiting all the nodes in a binary tree in a specific order: left subtree, root, right subtree. For Binary Search Trees (BST), this yields nodes in sorted order.

- **Recursive**: Visit left, root, right.
- **Iterative**: Use a stack to simulate recursion.

### When to Use
- To retrieve elements of a BST in sorted order.
- To check BST properties or validate tree structure.

## Example 1: Recursive Inorder Traversal
```python
def inorder(root):
    if not root:
        return []
    return inorder(root.left) + [root.val] + inorder(root.right)
```

## Example 2: Iterative Inorder Traversal
```python
def inorder_iterative(root):
    stack, res = [], []
    curr = root
    while curr or stack:
        while curr:
            stack.append(curr)
            curr = curr.left
        curr = stack.pop()
        res.append(curr.val)
        curr = curr.right
    return res
```

## Example 3: Morris Inorder Traversal (O(1) space)
```python
def morris_inorder(root):
    res = []
    curr = root
    while curr:
        if not curr.left:
            res.append(curr.val)
            curr = curr.right
        else:
            pre = curr.left
            while pre.right and pre.right != curr:
                pre = pre.right
            if not pre.right:
                pre.right = curr
                curr = curr.left
            else:
                pre.right = None
                res.append(curr.val)
                curr = curr.right
    return res
```

## Diagram
```
    2
   / \
  1   3
Inorder: 1, 2, 3
```

## Extra Study Material
- [Inorder Traversal (GeeksforGeeks)](https://www.geeksforgeeks.org/inorder-tree-traversal/)
- [Binary Tree Inorder Traversal - LeetCode](https://leetcode.com/problems/binary-tree-inorder-traversal/)

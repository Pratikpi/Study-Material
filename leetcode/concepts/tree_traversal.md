# Tree Traversal - Interview Preparation Guide

## Theory & Intuition
Tree traversal is the process of visiting all the nodes in a tree data structure in a specific order. The main types are preorder, inorder, postorder (for binary trees), and level order.

- **Preorder**: Visit root, then left, then right.
- **Inorder**: Visit left, root, right (BST: sorted order).
- **Postorder**: Visit left, right, root.
- **Level order**: Visit nodes level by level (BFS).

### When to Use
- When you need to process or print all nodes in a tree.
- When converting a tree to/from a list or string.

## Example 1: Preorder Traversal (Recursive)
```python
def preorder(root):
    if not root:
        return
    print(root.val)
    preorder(root.left)
    preorder(root.right)
```

## Example 2: Inorder Traversal (Iterative)
```python
def inorder(root):
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

## Example 3: Postorder Traversal (Iterative)
```python
def postorder(root):
    stack, res = [], []
    last_visited = None
    curr = root
    while curr or stack:
        if curr:
            stack.append(curr)
            curr = curr.left
        else:
            peek = stack[-1]
            if peek.right and last_visited != peek.right:
                curr = peek.right
            else:
                res.append(peek.val)
                last_visited = stack.pop()
    return res
```

## Diagram
```
    1
   / \
  2   3
 / \
4   5
Preorder: 1,2,4,5,3
Inorder: 4,2,5,1,3
Postorder: 4,5,2,3,1
```

## Extra Study Material
- [Tree Traversal (GeeksforGeeks)](https://www.geeksforgeeks.org/tree-traversals-inorder-preorder-and-postorder/)
- [Binary Tree Traversal - LeetCode](https://leetcode.com/explore/learn/card/data-structure-tree/134/traverse-a-tree/)

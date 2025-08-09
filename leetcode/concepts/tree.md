# Tree - Interview Preparation Guide

## Theory & Intuition
A tree is a hierarchical data structure consisting of nodes, with a single root node and potentially many levels of additional nodes. Each node may have zero or more child nodes, and there are no cycles.

- **Root**: The top node in the tree.
- **Leaf**: A node with no children.
- **Height**: The length of the longest path from the root to a leaf.
- **Binary Tree**: Each node has at most two children.

### When to Use
- When representing hierarchical data (e.g., file systems, organization charts).
- When you need fast insert, delete, and search (e.g., BSTs).

## Example 1: Binary Tree Traversal (Preorder)
```python
def preorder(root):
    if not root:
        return
    print(root.val)
    preorder(root.left)
    preorder(root.right)
```

## Example 2: Level Order Traversal (BFS)
```python
from collections import deque
def level_order(root):
    if not root:
        return []
    queue = deque([root])
    res = []
    while queue:
        node = queue.popleft()
        res.append(node.val)
        if node.left:
            queue.append(node.left)
        if node.right:
            queue.append(node.right)
    return res
```

## Example 3: Check if a Tree is Balanced
```python
def is_balanced(root):
    def height(node):
        if not node:
            return 0
        left = height(node.left)
        right = height(node.right)
        if left == -1 or right == -1 or abs(left - right) > 1:
            return -1
        return max(left, right) + 1
    return height(root) != -1
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
- [Tree Data Structure (GeeksforGeeks)](https://www.geeksforgeeks.org/binary-tree-data-structure/)
- [Binary Tree - LeetCode Explore](https://leetcode.com/explore/learn/card/data-structure-tree/)

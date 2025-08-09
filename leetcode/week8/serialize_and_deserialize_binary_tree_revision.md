# LeetCode: Serialize and Deserialize Binary Tree - Interview Revision Guide

[LeetCode Problem Link](https://https://leetcode.com/problems/serialize-and-deserialize-binary-tree/description/)

## Problem Statement
Design an algorithm to serialize and deserialize a binary tree. Serialization is converting a tree to a string, and deserialization is converting the string back to the original tree structure.

### Example
- Input: root = [1,2,3,null,null,4,5]
  Output: [1,2,3,null,null,4,5]

### Constraints
- The number of nodes in the tree is in the range [0, 10^4].
- -1000 <= Node.val <= 1000

---

## Concepts Required
- Binary Tree
- BFS/DFS Traversal
- String Manipulation

---

## Approach
- Use BFS (level order) or DFS (preorder) for serialization.
- Use a delimiter (e.g., ',') and a marker for null (e.g., '#').
- For deserialization, split the string and rebuild the tree recursively or iteratively.
- Time Complexity: O(n)

### Pseudocode
```
serialize(root):
    if not root: return ""
    queue = [root], res = []
    while queue:
        node = queue.pop(0)
        if node:
            res.append(str(node.val))
            queue.append(node.left)
            queue.append(node.right)
        else:
            res.append('#')
    return ','.join(res)
deserialize(data):
    if not data: return None
    vals = data.split(',')
    root = TreeNode(vals[0])
    queue = [root]
    i = 1
    while queue:
        node = queue.pop(0)
        if vals[i] != '#':
            node.left = TreeNode(vals[i])
            queue.append(node.left)
        i += 1
        if vals[i] != '#':
            node.right = TreeNode(vals[i])
            queue.append(node.right)
        i += 1
    return root
```

---

## Python Code
```python
class Codec:
    def serialize(self, root):
        if not root: return ""
        queue, res = [root], []
        while queue:
            node = queue.pop(0)
            if node:
                res.append(str(node.val))
                queue.append(node.left)
                queue.append(node.right)
            else:
                res.append('#')
        return ','.join(res)
    def deserialize(self, data):
        if not data: return None
        vals = data.split(',')
        root = TreeNode(int(vals[0]))
        queue = [root]
        i = 1
        while queue:
            node = queue.pop(0)
            if vals[i] != '#':
                node.left = TreeNode(int(vals[i]))
                queue.append(node.left)
            i += 1
            if vals[i] != '#':
                node.right = TreeNode(int(vals[i]))
                queue.append(node.right)
            i += 1
        return root
```

---

## Key Takeaways
- Use a marker for null nodes.
- BFS is intuitive for serialization/deserialization.

---

## Follow-up
- How would you serialize a BST more efficiently?
  - Use preorder traversal without null markers; BST properties allow unique reconstruction from preorder alone.
- Can you do this with preorder traversal?
  - Yes, serialize with preorder and reconstruct using value bounds.

---

## Related Problems
- Binary Tree Preorder Traversal
- Construct Binary Tree from String

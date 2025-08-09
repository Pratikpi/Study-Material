# LeetCode: Binary Tree Level Order Traversal - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/binary-tree-level-order-traversal/description/)

## Problem Statement
Given the root of a binary tree, return the level order traversal of its nodes' values. (i.e., from left to right, level by level).

### Example
- Input: root = [3,9,20,null,null,15,7]
  Output: [[3],[9,20],[15,7]]

### Constraints
- The number of nodes in the tree is in the range [0, 2000].
- -1000 <= Node.val <= 1000

---

## Concepts Required
- Binary Tree
- Breadth-First Search (BFS)
- Queue

---

## BFS Approach
- Use a queue to traverse the tree level by level.
- Time Complexity: O(n)

### Pseudocode
```
if not root: return []
queue = [root]
result = []
while queue:
    level = []
    for _ in range(len(queue)):
        node = queue.pop(0)
        level.append(node.val)
        if node.left: queue.append(node.left)
        if node.right: queue.append(node.right)
    result.append(level)
return result
```

---

## Python Code
```python
def levelOrder(root):
    if not root:
        return []
    queue = [root]
    result = []
    while queue:
        level = []
        for _ in range(len(queue)):
            node = queue.pop(0)
            level.append(node.val)
            if node.left:
                queue.append(node.left)
            if node.right:
                queue.append(node.right)
        result.append(level)
    return result
```

---

## Key Takeaways
- BFS is the standard approach for level order traversal.
- Practice both iterative and recursive solutions.

---

## Follow-up
- How would you return a zigzag level order traversal?
- Can you do it recursively?

---

## Related Problems
- Binary Tree Right Side View
- Average of Levels in Binary Tree
- Minimum Depth of Binary Tree

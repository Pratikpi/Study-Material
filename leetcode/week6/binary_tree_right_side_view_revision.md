# LeetCode: Binary Tree Right Side View - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/binary-tree-right-side-view/description/)

## Problem Statement
Given the root of a binary tree, return the values of the nodes you can see ordered from top to bottom when looking from the right side.

### Example
- Input: root = [1,2,3,null,5,null,4]
  Output: [1,3,4]

- Input: root = [1,null,3]
  Output: [1,3]

### Constraints
- The number of nodes in the tree is in the range [0, 100].
- -100 <= Node.val <= 100

---

## Concepts Required
- Binary Tree
- Breadth-First Search (BFS)
- Level Order Traversal

---

## BFS Approach
- Traverse level by level, add the last node of each level to result.
- Time Complexity: O(n)

### Pseudocode
```
queue = [root]
while queue:
    for each node in level:
        add children to queue
    add last node's value to result
return result
```

---

## Python Code
```python
def rightSideView(root):
    if not root:
        return []
    res = []
    queue = [root]
    while queue:
        next_level = []
        for node in queue:
            if node.left:
                next_level.append(node.left)
            if node.right:
                next_level.append(node.right)
        res.append(queue[-1].val)
        queue = next_level
    return res
```

---

## Key Takeaways
- BFS is optimal for right side view.
- Practice both BFS and DFS (right-first) solutions.

---

## Follow-up
- How would you do it with DFS?
  - Traverse right before left, record the first node at each depth to get the right side view.
- Can you return the left side view?
  - Traverse left before right, record the first node at each depth to get the left side view.

---

## Related Problems
- Left Side View of Binary Tree
- Binary Tree Level Order Traversal
- Top View of Binary Tree

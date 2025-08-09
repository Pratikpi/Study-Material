# LeetCode: Diameter of Binary Tree - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/diameter-of-binary-tree/description/)

## Problem Statement
Given the root of a binary tree, return the length of the diameter of the tree.

The diameter is the length of the longest path between any two nodes in a tree. This path may or may not pass through the root.

### Example
- Input: root = [1,2,3,4,5]
  Output: 3
  Explanation: The longest path is [4,2,1,3] or [5,2,1,3], length = 3.

### Constraints
- The number of nodes in the tree is in the range [1, 10^4].
- -100 <= Node.val <= 100

---

## Concepts Required
- Binary Tree
- Recursion
- Depth-First Search (DFS)

---

## DFS Approach
- For each node, compute the depth of left and right subtrees.
- The diameter at each node is left_depth + right_depth.
- Time Complexity: O(n)

### Pseudocode
```
max_diameter = 0
def depth(node):
    if not node: return 0
    left = depth(node.left)
    right = depth(node.right)
    max_diameter = max(max_diameter, left + right)
    return max(left, right) + 1
depth(root)
return max_diameter
```

---

## Python Code
```python
def diameterOfBinaryTree(root):
    diameter = 0
    def depth(node):
        nonlocal diameter
        if not node:
            return 0
        left = depth(node.left)
        right = depth(node.right)
        diameter = max(diameter, left + right)
        return max(left, right) + 1
    depth(root)
    return diameter
```

---

## Key Takeaways
- The diameter may not pass through the root.
- Use post-order DFS to compute depths and update diameter.
- Practice both recursive and iterative approaches.

---

## Follow-up
- How would you return the actual path?
- Can you do it iteratively?

---

## Related Problems
- Maximum Depth of Binary Tree
- Balanced Binary Tree
- Binary Tree Maximum Path Sum

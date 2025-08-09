# LeetCode: Lowest Common Ancestor of a Binary Tree - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/description/)

## Problem Statement
Given a binary tree, find the lowest common ancestor (LCA) of two given nodes in the tree.

The LCA is the lowest node that has both nodes as descendants (a node can be a descendant of itself).

### Example
- Input: root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 1
  Output: 3

- Input: root = [1,2], p = 1, q = 2
  Output: 1

### Constraints
- The number of nodes in the tree is in the range [2, 10^5].
- -10^9 <= Node.val <= 10^9
- All Node.val are unique.
- p != q
- p and q will exist in the tree.

---

## Concepts Required
- Binary Tree
- Recursion
- Tree Traversal

---

## Recursive Approach
- Traverse the tree, return node if p or q found, else recurse left/right.
- Time Complexity: O(n)

### Pseudocode
```
if not root or root == p or root == q: return root
left = recurse left
right = recurse right
if left and right: return root
return left or right
```

---

## Python Code
```python
def lowestCommonAncestor(root, p, q):
    if not root or root == p or root == q:
        return root
    left = lowestCommonAncestor(root.left, p, q)
    right = lowestCommonAncestor(root.right, p, q)
    if left and right:
        return root
    return left or right
```

---

## Key Takeaways
- Recursion is optimal for LCA in binary trees.
- Practice both recursive and parent-pointer solutions.

---

## Follow-up
- How would you handle a BST?
  - Use BST properties: traverse left/right based on node values to find the split point.
- Can you do it iteratively?
  - Yes, use a loop instead of recursion, traversing down the tree until the split point is found.

---

## Related Problems
- Lowest Common Ancestor of a BST
- Binary Tree Paths
- Find Distance in a Binary Tree

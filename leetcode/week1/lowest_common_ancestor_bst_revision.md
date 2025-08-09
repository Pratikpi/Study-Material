# LeetCode: Lowest Common Ancestor of a Binary Search Tree - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/description/)

## Problem Statement
Given a binary search tree (BST), find the lowest common ancestor (LCA) node of two given nodes in the BST.

The LCA is defined as the lowest node that has both nodes as descendants (a node can be a descendant of itself).

### Example
- Input: root = [6,2,8,0,4,7,9,null,null,3,5], p = 2, q = 8
  Output: 6

- Input: root = [6,2,8,0,4,7,9,null,null,3,5], p = 2, q = 4
  Output: 2

- Input: root = [2,1], p = 2, q = 1
  Output: 2

### Constraints
- The number of nodes in the tree is in the range [2, 10^5].
- -10^9 <= Node.val <= 10^9
- All Node.val are unique.
- p != q
- p and q will exist in the BST.

---

## Concepts Required
- Binary Search Tree (BST)
- Tree Traversal
- Recursion/Iteration

---

## BST Property Approach
- Traverse the tree from the root.
- If both p and q are less than root, go left. If both are greater, go right. Else, root is LCA.
- Time Complexity: O(h), h = height of tree

### Pseudocode
```
while root:
    if p < root.val and q < root.val:
        root = root.left
    elif p > root.val and q > root.val:
        root = root.right
    else:
        return root
```

---

## Python Code
```python
def lowestCommonAncestor(root, p, q):
    while root:
        if p.val < root.val and q.val < root.val:
            root = root.left
        elif p.val > root.val and q.val > root.val:
            root = root.right
        else:
            return root
```

---

## Key Takeaways
- Use BST properties to efficiently find LCA.
- No need to store parent pointers or paths.
- Practice both iterative and recursive solutions.

---

## Follow-up
- How would you find LCA in a general binary tree?
- What if the tree is not a BST?

---

## Related Problems
- Lowest Common Ancestor of a Binary Tree
- Smallest Common Region
- Find Distance in a Binary Tree

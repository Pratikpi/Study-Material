# LeetCode: Balanced Binary Tree - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/balanced-binary-tree/description/)

## Problem Statement
Given a binary tree, determine if it is height-balanced.
A binary tree is balanced if the left and right subtrees of every node differ in height by no more than 1.

### Example
- Input: root = [3,9,20,null,null,15,7]
  Output: true

- Input: root = [1,2,2,3,3,null,null,4,4]
  Output: false

- Input: root = []
  Output: true

### Constraints
- The number of nodes in the tree is in the range [0, 5000].
- -10^4 <= Node.val <= 10^4

---

## Concepts Required
- Binary Tree
- Recursion
- Depth-First Search (DFS)

---

## DFS Approach
- Recursively check the height of left and right subtrees.
- If the difference is more than 1, the tree is not balanced.
- Time Complexity: O(n)

### Pseudocode
```
function height(node):
    if not node: return 0
    left = height(node.left)
    right = height(node.right)
    if abs(left - right) > 1: unbalanced
    return max(left, right) + 1
```

---

## Python Code
```python
def isBalanced(root):
    def height(node):
        if not node: return 0
        left = height(node.left)
        right = height(node.right)
        if left == -1 or right == -1 or abs(left - right) > 1:
            return -1
        return max(left, right) + 1
    return height(root) != -1
```

---

## Key Takeaways
- Use post-order DFS to check balance and height in one pass.
- Return -1 early if unbalanced for efficiency.
- Practice both recursive and iterative approaches.

---

## Follow-up
- How would you balance an unbalanced tree?
  - Use self-balancing trees (AVL, Red-Black) or rebuild the tree from inorder traversal for minimal height. For a BST, perform an inorder traversal to get sorted nodes, then recursively build a balanced tree. For general binary trees, apply rotations as in AVL/Red-Black trees after insertions/deletions.
- Can you do it iteratively?
  - Yes, by using a stack or queue for traversal and iterative rotations (as in AVL/Red-Black trees). For rebuilding, collect nodes iteratively and reconstruct the tree without recursion, ensuring balance at each step.

---

## Related Problems
- Maximum Depth of Binary Tree
- Symmetric Tree
- AVL Tree

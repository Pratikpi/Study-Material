# LeetCode: Kth Smallest Element in a BST - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/kth-smallest-element-in-a-bst/description/)

## Problem Statement
Given the root of a binary search tree, and an integer k, return the kth smallest value (1-indexed) of all the values of the nodes in the tree.

### Example
- Input: root = [3,1,4,null,2], k = 1
  Output: 1

- Input: root = [5,3,6,2,4,null,null,1], k = 3
  Output: 3

### Constraints
- The number of nodes in the tree is n.
- 1 <= k <= n <= 10^4
- 0 <= Node.val <= 10^4

---

## Concepts Required
- Binary Search Tree
- Inorder Traversal
- Recursion/Iteration

---

## Approach
- Inorder traversal of BST yields sorted order.
- Traverse inorder and count nodes until k is reached.
- Time Complexity: O(H + k), H = tree height

### Pseudocode
```
stack = []
while True:
    while root:
        stack.append(root)
        root = root.left
    root = stack.pop()
    k -= 1
    if k == 0: return root.val
    root = root.right
```

---

## Python Code
```python
def kthSmallest(root, k):
    stack = []
    while True:
        while root:
            stack.append(root)
            root = root.left
        root = stack.pop()
        k -= 1
        if k == 0:
            return root.val
        root = root.right
```

---

## Key Takeaways
- Inorder traversal is key for BST order.
- Both recursive and iterative solutions are possible.

---

## Follow-up
- How would you handle frequent modifications (insert/delete)?
  - Augment the BST with subtree sizes to support O(log n) queries and updates.
- Can you do this with O(1) extra space?
  - Use Morris traversal for inorder traversal with O(1) space.

---

## Related Problems
- Kth Largest Element in an Array
- Binary Search Tree Iterator

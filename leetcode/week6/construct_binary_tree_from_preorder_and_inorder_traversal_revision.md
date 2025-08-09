# LeetCode: Construct Binary Tree from Preorder and Inorder Traversal - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/description/)

## Problem Statement
Given two integer arrays preorder and inorder, construct and return the binary tree.

### Example
- Input: preorder = [3,9,20,15,7], inorder = [9,3,15,20,7]
  Output: [3,9,20,null,null,15,7]

### Constraints
- 1 <= preorder.length <= 3000
- inorder.length == preorder.length
- -3000 <= Node.val <= 3000
- All values are unique.

---

## Concepts Required
- Binary Tree
- Recursion
- Hash Map

---

## Recursive Approach
- The first element in preorder is the root. Find its index in inorder to split left/right subtrees.
- Time Complexity: O(n)

### Pseudocode
```
map = {val: idx for idx, val in enumerate(inorder)}
def build(pre_left, pre_right, in_left, in_right):
    if pre_left > pre_right: return None
    root_val = preorder[pre_left]
    root = TreeNode(root_val)
    in_root = map[root_val]
    left_size = in_root - in_left
    root.left = build(pre_left+1, pre_left+left_size, in_left, in_root-1)
    root.right = build(pre_left+left_size+1, pre_right, in_root+1, in_right)
    return root
```

---

## Python Code
```python
def buildTree(preorder, inorder):
    idx_map = {v: i for i, v in enumerate(inorder)}
    def helper(pre_left, pre_right, in_left, in_right):
        if pre_left > pre_right:
            return None
        root_val = preorder[pre_left]
        root = TreeNode(root_val)
        in_root = idx_map[root_val]
        left_size = in_root - in_left
        root.left = helper(pre_left+1, pre_left+left_size, in_left, in_root-1)
        root.right = helper(pre_left+left_size+1, pre_right, in_root+1, in_right)
        return root
    return helper(0, len(preorder)-1, 0, len(inorder)-1)
```

---

## Key Takeaways
- Use hash map for O(1) index lookup in inorder.
- Recursion is optimal for tree construction from traversals.

---

## Follow-up
- How would you do it iteratively?
  - Use a stack to simulate recursion and build the tree node by node.
- Can you construct from postorder and inorder?
  - Yes, similar logic but process postorder from the end, matching nodes with inorder positions.

---

## Related Problems
- Construct Binary Tree from Inorder and Postorder Traversal
- Serialize and Deserialize Binary Tree
- Binary Tree Preorder Traversal

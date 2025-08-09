# LeetCode: Merge Two Sorted Lists - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/merge-two-sorted-lists/description/)

## Problem Statement
You are given the heads of two sorted linked lists `list1` and `list2`. Merge the two lists into one sorted list by splicing together the nodes of the first two lists. Return the head of the merged linked list.

### Example
- Input: list1 = [1,2,4], list2 = [1,3,4]
  Output: [1,1,2,3,4,4]

- Input: list1 = [], list2 = []
  Output: []

- Input: list1 = [], list2 = [0]
  Output: [0]

### Constraints
- The number of nodes in both lists is in the range [0, 50].
- -100 <= Node.val <= 100
- Both `list1` and `list2` are sorted in non-decreasing order.

---

## Concepts Required
- Linked List
- Recursion
- Iteration

---

## Recursive Approach
- Compare the heads of both lists and recursively merge the rest.
- Time Complexity: O(n + m)

### Pseudocode
```
if not l1: return l2
if not l2: return l1
if l1.val < l2.val:
    l1.next = merge(l1.next, l2)
    return l1
else:
    l2.next = merge(l1, l2.next)
    return l2
```

---

## Python Code
```python
def mergeTwoLists(l1, l2):
    if not l1: return l2
    if not l2: return l1
    if l1.val < l2.val:
        l1.next = mergeTwoLists(l1.next, l2)
        return l1
    else:
        l2.next = mergeTwoLists(l1, l2.next)
        return l2
```

---

## Key Takeaways
- Recursion is elegant for merging lists.
- Iterative solutions use a dummy node and a pointer.
- Practice both recursive and iterative approaches.

---

## Follow-up
- How would you merge k sorted lists?
- Can you do it in-place without extra space?

---

## Related Problems
- Merge k Sorted Lists
- Merge Sorted Array
- Sort List

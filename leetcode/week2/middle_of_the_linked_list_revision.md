# LeetCode: Middle of the Linked List - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/middle-of-the-linked-list/description/)

## Problem Statement
Given the head of a singly linked list, return the middle node. If there are two middle nodes, return the second middle node.

### Example
- Input: head = [1,2,3,4,5]
  Output: [3,4,5]

- Input: head = [1,2,3,4,5,6]
  Output: [4,5,6]

### Constraints
- The number of nodes in the list is in the range [1, 100].

---

## Concepts Required
- Linked List
- Two Pointers (Slow and Fast)

---

## Two Pointers Approach
- Move slow by 1 and fast by 2. When fast reaches the end, slow is at the middle.
- Time Complexity: O(n)

### Pseudocode
```
slow = fast = head
while fast and fast.next:
    slow = slow.next
    fast = fast.next.next
return slow
```

---

## Python Code
```python
def middleNode(head):
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
    return slow
```

---

## Key Takeaways
- Two pointers is a classic pattern for linked list problems.
- Practice both array and pointer-based solutions.

---

## Follow-up
- How would you find the 1/3rd or 1/4th node?
  - Use slow/fast pointers with different step sizes (e.g., move one pointer every 3 steps for 1/3rd node).
- Can you do it in one pass?
  - Yes, with appropriate pointer increments, you can find fractional nodes in a single traversal.

---

## Related Problems
- Remove Nth Node From End of List
- Linked List Cycle
- Palindrome Linked List

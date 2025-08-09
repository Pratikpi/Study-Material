# LeetCode: Reverse Linked List - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/reverse-linked-list/description/)

## Problem Statement
Given the head of a singly linked list, reverse the list, and return the reversed list.

### Example
- Input: head = [1,2,3,4,5]
  Output: [5,4,3,2,1]

- Input: head = [1,2]
  Output: [2,1]

### Constraints
- The number of nodes in the list is in the range [0, 5000].
- -5000 <= Node.val <= 5000

---

## Concepts Required
- Linked List
- Iteration
- Recursion

---

## Iterative Approach
- Use three pointers: prev, curr, next.
- Time Complexity: O(n)

### Pseudocode
```
prev = None
curr = head
while curr:
    next = curr.next
    curr.next = prev
    prev = curr
    curr = next
return prev
```

---

## Python Code
```python
def reverseList(head):
    prev = None
    curr = head
    while curr:
        next = curr.next
        curr.next = prev
        prev = curr
        curr = next
    return prev
```

---

## Key Takeaways
- Iterative reversal is a classic linked list problem.
- Practice both iterative and recursive solutions.

---

## Follow-up
- How would you reverse a sublist?
  - Use pointers to reverse only the nodes between positions m and n, reconnecting the reversed part with the rest of the list.
- Can you do it recursively?
  - Yes, recursively reverse the list and adjust pointers as you return from recursion.

---

## Related Problems
- Reverse Linked List II
- Swap Nodes in Pairs
- Add Two Numbers

# LeetCode: Linked List Cycle - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/linked-list-cycle/description/)

## Problem Statement
Given `head`, the head of a linked list, determine if the linked list has a cycle in it.

A cycle exists if a node can be reached again by continuously following the `next` pointer.

### Example
- Input: head = [3,2,0,-4], pos = 1
  Output: true

- Input: head = [1,2], pos = 0
  Output: true

- Input: head = [1], pos = -1
  Output: false

### Constraints
- The number of nodes in the list is in the range [0, 10^4].
- -10^5 <= Node.val <= 10^5
- pos is -1 or a valid index in the linked-list.

---

## Concepts Required
- Linked List
- Two Pointers (Floyd's Tortoise and Hare)

---

## Two Pointers Approach
- Use slow and fast pointers. If they meet, there is a cycle.
- Time Complexity: O(n)
- Space Complexity: O(1)

### Pseudocode
```
slow = fast = head
while fast and fast.next:
    slow = slow.next
    fast = fast.next.next
    if slow == fast:
        return True
return False
```

---

## Python Code
```python
def hasCycle(head):
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow == fast:
            return True
    return False
```

---

## Key Takeaways
- Two pointers is a classic technique for cycle detection.
- O(1) space is optimal for this problem.
- Practice both hash set and two pointer approaches.

---

## Follow-up
- Can you find the node where the cycle begins?
- How would you modify the list to remove the cycle?

---

## Related Problems
- Linked List Cycle II
- Happy Number
- Detect Cycle in a Directed Graph

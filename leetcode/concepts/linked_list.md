# Linked List - Interview Preparation Guide

## Theory & Intuition
A linked list is a linear data structure where each element (node) contains a value and a reference (pointer) to the next node. Types include singly, doubly, and circular linked lists.

- **Singly linked list**: Each node points to the next.
- **Doubly linked list**: Each node points to both next and previous.
- **Circular linked list**: Last node points back to the head.

### When to Use
- When frequent insertions/deletions are needed (especially at the head/tail).
- When memory allocation needs to be dynamic.

## Example 1: Reverse a Linked List
```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def reverse_list(head):
    prev = None
    curr = head
    while curr:
        nxt = curr.next
        curr.next = prev
        prev = curr
        curr = nxt
    return prev
```

## Example 2: Detect Cycle (Floyd's Tortoise and Hare)
```python
def has_cycle(head):
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow == fast:
            return True
    return False
```

## Example 3: Merge Two Sorted Lists
```python
def merge_lists(l1, l2):
    dummy = curr = ListNode()
    while l1 and l2:
        if l1.val < l2.val:
            curr.next, l1 = l1, l1.next
        else:
            curr.next, l2 = l2, l2.next
        curr = curr.next
    curr.next = l1 or l2
    return dummy.next
```

## Diagram
```
1 -> 2 -> 3 -> 4 -> None
```

## Extra Study Material
- [Linked List (LeetCode Explore)](https://leetcode.com/explore/learn/card/linked-list/)
- [Linked List (GeeksforGeeks)](https://www.geeksforgeeks.org/data-structures/linked-list/)

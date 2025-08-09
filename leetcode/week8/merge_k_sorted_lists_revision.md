# LeetCode: Merge k Sorted Lists - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/merge-k-sorted-lists/description/)

## Problem Statement
You are given an array of k linked-lists lists, each linked-list is sorted in ascending order. Merge all the linked-lists into one sorted linked-list and return it.

### Example
- Input: lists = [[1,4,5],[1,3,4],[2,6]]
  Output: [1,1,2,3,4,4,5,6]

- Input: lists = []
  Output: []

- Input: lists = [[]]
  Output: []

### Constraints
- k == lists.length
- 0 <= k <= 10^4
- 0 <= lists[i].length <= 500
- -10^4 <= lists[i][j] <= 10^4

---

## Concepts Required
- Heap (Priority Queue)
- Linked List
- Divide and Conquer

---

## Approach
- Use a min-heap to always get the smallest node among the heads of the lists.
- Alternatively, merge lists pairwise (divide and conquer).
- Time Complexity: O(N log k), N = total nodes, k = number of lists

### Pseudocode
```
heap = []
for each list:
    if list: push (val, list_node) to heap
while heap:
    pop smallest node, add to result
    if node.next: push (node.next.val, node.next) to heap
return result.next
```

---

## Python Code
```python
import heapq
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def mergeKLists(lists):
    heap = []
    for i, node in enumerate(lists):
        if node:
            heapq.heappush(heap, (node.val, i, node))
    dummy = ListNode(0)
    curr = dummy
    while heap:
        val, i, node = heapq.heappop(heap)
        curr.next = node
        curr = curr.next
        if node.next:
            heapq.heappush(heap, (node.next.val, i, node.next))
    return dummy.next
```

---

## Key Takeaways
- Min-heap efficiently merges k sorted lists.
- Divide and conquer is an alternative approach.

---

## Follow-up
- How would you merge lists in place?
  - Merge nodes by rearranging pointers instead of creating new nodes.
- Can you do this with O(1) extra space?
  - Only if the input lists can be modified; otherwise, a heap requires O(k) space.

---

## Related Problems
- Merge Two Sorted Lists
- Kth Smallest Element in a Sorted Matrix

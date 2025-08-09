# LeetCode: LRU Cache - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/lru-cache/description/)

## Problem Statement
Design a data structure that follows the constraints of a Least Recently Used (LRU) cache. Implement the LRUCache class with get and put methods.

### Example
- Input: ["LRUCache","put","put","get","put","get","put","get","get","get"], [[2],[1,1],[2,2],[1],[3,3],[2],[4,4],[1],[3],[4]]
  Output: [null,null,null,1,null,-1,null,-1,3,4]

### Constraints
- 1 <= capacity <= 3000
- 0 <= key <= 10^4
- 0 <= value <= 10^5
- At most 2 * 10^5 calls will be made to get and put.

---

## Concepts Required
- Hash Map
- Doubly Linked List
- Design

---

## Doubly Linked List + Hash Map Approach
- Use a doubly linked list to track order, hash map for O(1) access.
- Time Complexity: O(1) for get and put

### Pseudocode
```
get(key): if key in map, move node to front, return value; else return -1
put(key, value): if key in map, update and move to front; else add node to front, evict if over capacity
```

---

## Python Code
```python
class Node:
    def __init__(self, key, val):
        self.key = key
        self.val = val
        self.prev = self.next = None

class LRUCache:
    def __init__(self, capacity):
        self.cap = capacity
        self.map = {}
        self.left, self.right = Node(0,0), Node(0,0)
        self.left.next, self.right.prev = self.right, self.left
    def remove(self, node):
        prev, nxt = node.prev, node.next
        prev.next, nxt.prev = nxt, prev
    def insert(self, node):
        prev, nxt = self.right.prev, self.right
        prev.next = nxt.prev = node
        node.prev, node.next = prev, nxt
    def get(self, key):
        if key in self.map:
            self.remove(self.map[key])
            self.insert(self.map[key])
            return self.map[key].val
        return -1
    def put(self, key, value):
        if key in self.map:
            self.remove(self.map[key])
        self.map[key] = Node(key, value)
        self.insert(self.map[key])
        if len(self.map) > self.cap:
            lru = self.left.next
            self.remove(lru)
            del self.map[lru.key]
```

---

## Key Takeaways
- Doubly linked list + hash map is optimal for LRU cache.
- Practice both custom and OrderedDict solutions.

---

## Follow-up
- How would you support time-based expiration?
  - Store timestamps with each entry and periodically remove expired items.
- Can you do it with a single linked list?
  - Yes, but you would need a hash map for O(1) access and a linked list for order; a doubly linked list is more efficient.

---

## Related Problems
- LFU Cache
- Design Hit Counter
- Design Twitter

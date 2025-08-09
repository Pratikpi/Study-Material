# LeetCode: Time Based Key-Value Store - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/time-based-key-value-store/description/)

## Problem Statement
Design a time-based key-value data structure that can store multiple values for the same key at different timestamps and retrieve the value at a given timestamp.

### Example
- Input: ["TimeMap","set","get","get","set","get","get"], [[],["foo","bar",1],["foo",1],["foo",3],["foo","bar2",4],["foo",4],["foo",5]]
  Output: [null,null,"bar","bar",null,"bar2","bar2"]

### Constraints
- 1 <= key.length, value.length <= 100
- 1 <= timestamp <= 10^7
- All set operations have strictly increasing timestamps.

---

## Concepts Required
- Hash Map
- Binary Search
- Design

---

## Hash Map + Binary Search Approach
- Store (timestamp, value) pairs for each key, use binary search for get.
- Time Complexity: O(log n) for get, O(1) for set

### Pseudocode
```
set(key, value, timestamp): append (timestamp, value) to key's list
get(key, timestamp): binary search for largest timestamp <= given timestamp
```

---

## Python Code
```python
from collections import defaultdict
import bisect

class TimeMap:
    def __init__(self):
        self.store = defaultdict(list)
    def set(self, key, value, timestamp):
        self.store[key].append((timestamp, value))
    def get(self, key, timestamp):
        arr = self.store[key]
        i = bisect.bisect_right(arr, (timestamp, chr(127)))
        return arr[i-1][1] if i else ""
```

---

## Key Takeaways
- Binary search is optimal for time-based queries.
- Practice both list and tree-based solutions.

---

## Follow-up
- How would you handle deletions?
- Can you optimize for memory?

---

## Related Problems
- Snapshot Array
- Logger Rate Limiter
- Design File System

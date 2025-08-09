# Design - Interview Preparation Guide

## Theory & Intuition
"Design" in coding interviews refers to the process of architecting scalable, maintainable, and efficient systems or data structures. It often involves:
- Choosing the right data structures and algorithms
- Balancing trade-offs (time, space, complexity)
- Handling edge cases and scalability

### When to Use
- When building custom data structures (e.g., LRU Cache, Min Stack)
- When asked to design a system or API

## Example 1: LRU Cache (Design)
```python
from collections import OrderedDict
class LRUCache:
    def __init__(self, capacity):
        self.cache = OrderedDict()
        self.capacity = capacity
    def get(self, key):
        if key not in self.cache:
            return -1
        self.cache.move_to_end(key)
        return self.cache[key]
    def put(self, key, value):
        if key in self.cache:
            self.cache.move_to_end(key)
        self.cache[key] = value
        if len(self.cache) > self.capacity:
            self.cache.popitem(last=False)
```

## Example 2: Min Stack (Design)
```python
class MinStack:
    def __init__(self):
        self.stack = []
        self.min_stack = []
    def push(self, x):
        self.stack.append(x)
        if not self.min_stack or x <= self.min_stack[-1]:
            self.min_stack.append(x)
    def pop(self):
        if self.stack.pop() == self.min_stack[-1]:
            self.min_stack.pop()
    def top(self):
        return self.stack[-1]
    def getMin(self):
        return self.min_stack[-1]
```

## Example 3: Time-Based Key-Value Store
```python
class TimeMap:
    def __init__(self):
        self.store = {}
    def set(self, key, value, timestamp):
        self.store.setdefault(key, []).append((timestamp, value))
    def get(self, key, timestamp):
        vals = self.store.get(key, [])
        l, r = 0, len(vals)-1
        res = ""
        while l <= r:
            m = (l+r)//2
            if vals[m][0] <= timestamp:
                res = vals[m][1]
                l = m+1
            else:
                r = m-1
        return res
```

## Diagram
```
[Design] <-> [Data Structure] <-> [API]
```

## Extra Study Material
- [System Design Primer (GitHub)](https://github.com/donnemartin/system-design-primer)
- [OOD Patterns (GeeksforGeeks)](https://www.geeksforgeeks.org/software-design-patterns/)

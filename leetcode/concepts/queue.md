# Queue - Interview Preparation Guide

## Theory & Intuition
A queue is a linear data structure that follows the First-In-First-Out (FIFO) principle. Elements are added at the rear and removed from the front. Queues are used in breadth-first search, scheduling, and buffering.

- **Types**: Simple queue, circular queue, deque (double-ended queue), priority queue.
- **Common operations**: enqueue, dequeue, peek/front, isEmpty.

### When to Use
- When you need to process items in the order they arrive.
- Useful in BFS, task scheduling, and streaming data.

## Example 1: Basic Queue (Python collections.deque)
```python
from collections import deque
q = deque()
q.append(1)  # enqueue
q.append(2)
print(q.popleft())  # dequeue, Output: 1
```

## Example 2: BFS Using Queue
```python
from collections import deque
def bfs(graph, start):
    visited = set([start])
    q = deque([start])
    while q:
        node = q.popleft()
        for neighbor in graph[node]:
            if neighbor not in visited:
                visited.add(neighbor)
                q.append(neighbor)
```

## Example 3: Implementing a Queue with Two Stacks
```python
class MyQueue:
    def __init__(self):
        self.in_stack, self.out_stack = [], []
    def push(self, x):
        self.in_stack.append(x)
    def pop(self):
        if not self.out_stack:
            while self.in_stack:
                self.out_stack.append(self.in_stack.pop())
        return self.out_stack.pop()
```

## Diagram
```
Front [1, 2, 3] Rear
```

## Extra Study Material
- [Queue (LeetCode Explore)](https://leetcode.com/explore/learn/card/queue-stack/)
- [Queue Data Structure (GeeksforGeeks)](https://www.geeksforgeeks.org/queue-data-structure/)

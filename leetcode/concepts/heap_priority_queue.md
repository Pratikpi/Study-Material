# Heap (Priority Queue) - Interview Preparation Guide

## Theory & Intuition
A heap is a specialized tree-based data structure that satisfies the heap property: in a max heap, every parent is greater than or equal to its children; in a min heap, every parent is less than or equal to its children. Priority queues are often implemented with heaps.

- **Binary heap**: Most common, implemented as an array.
- **Min heap**: Smallest element at the root.
- **Max heap**: Largest element at the root.

### When to Use
- When you need quick access to the smallest/largest element (e.g., Dijkstra's, median maintenance, scheduling).

## Example 1: Min Heap with heapq (Python)
```python
import heapq
heap = []
heapq.heappush(heap, 3)
heapq.heappush(heap, 1)
heapq.heappush(heap, 2)
print(heapq.heappop(heap))  # Output: 1
```

## Example 2: Kth Largest Element
```python
import heapq
def kth_largest(nums, k):
    return heapq.nlargest(k, nums)[-1]
```

## Example 3: Median Maintenance (Two Heaps)
```python
import heapq
low, high = [], []  # max-heap (invert sign), min-heap
# Add number:
heapq.heappush(low, -num)
heapq.heappush(high, -heapq.heappop(low))
if len(high) > len(low):
    heapq.heappush(low, -heapq.heappop(high))
# Median:
if len(low) > len(high):
    median = -low[0]
else:
    median = (-low[0] + high[0]) / 2
```

## Diagram
```
Min Heap (array): [1, 3, 2]
        1
       / \
      3   2
```

## Extra Study Material
- [Heap Data Structure (GeeksforGeeks)](https://www.geeksforgeeks.org/heap-data-structure/)
- [Heap - LeetCode Explore](https://leetcode.com/explore/learn/card/heap/)

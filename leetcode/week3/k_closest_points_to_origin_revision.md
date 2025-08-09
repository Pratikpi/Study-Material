# LeetCode: K Closest Points to Origin - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/k-closest-points-to-origin/description/)

## Problem Statement
Given an array of points where points[i] = [xi, yi] represents a point on the X-Y plane and an integer k, return the k closest points to the origin (0, 0).

The answer may be returned in any order.

### Example
- Input: points = [[1,3],[-2,2]], k = 1
  Output: [[-2,2]]

- Input: points = [[3,3],[5,-1],[-2,4]], k = 2
  Output: [[3,3],[-2,4]]

### Constraints
- 1 <= k <= points.length <= 10^4
- -10^4 < xi, yi < 10^4

---

## Concepts Required
- Heap (Priority Queue)
- Sorting
- Euclidean Distance

---

## Heap Approach
- Use a max-heap of size k to keep the closest points.
- Time Complexity: O(n log k)

### Pseudocode
```
heap = []
for (x, y) in points:
    push (-distance, (x, y)) to heap
    if heap size > k: pop
return points in heap
```

---

## Python Code
```python
import heapq

def kClosest(points, k):
    return heapq.nsmallest(k, points, key=lambda p: p[0]**2 + p[1]**2)
```

---

## Key Takeaways
- Use a heap for efficient k-selection.
- Practice both heap and sorting approaches.

---

## Follow-up
- How would you do it in-place?
- Can you use QuickSelect for O(n) average time?

---

## Related Problems
- Kth Largest Element in an Array
- Find K Pairs with Smallest Sums
- Closest Binary Search Tree Value

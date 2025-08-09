# LeetCode: Find Median from Data Stream - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/find-median-from-data-stream/description/)

## Problem Statement
The MedianFinder class is designed to add numbers from a data stream and find the median efficiently at any time.

### Example
- Input: ["MedianFinder","addNum","addNum","findMedian","addNum","findMedian"]
  [[ ],[1],[2],[ ],[3],[ ]]
  Output: [null,null,null,1.5,null,2.0]

### Constraints
- -10^5 <= num <= 10^5
- There will be at least one element in the data structure before calling findMedian.
- At most 5 * 10^4 calls will be made to addNum and findMedian.

---

## Concepts Required
- Heaps (Priority Queue)
- Data Structures
- Median Maintenance

---

## Approach
- Use two heaps: a max-heap for the lower half, a min-heap for the upper half.
- Balance heaps so their sizes differ by at most 1.
- Median is either the top of one heap or the average of tops.
- Time Complexity: O(log n) for addNum, O(1) for findMedian.

### Pseudocode
```
maxHeap = [] // lower half (invert sign for max-heap)
minHeap = [] // upper half
addNum(num):
    if maxHeap is empty or num <= -maxHeap[0]:
        push -num to maxHeap
    else:
        push num to minHeap
    // Balance
    if len(maxHeap) > len(minHeap) + 1:
        move top of maxHeap to minHeap
    if len(minHeap) > len(maxHeap):
        move top of minHeap to maxHeap
findMedian():
    if len(maxHeap) == len(minHeap):
        return (-maxHeap[0] + minHeap[0]) / 2
    else:
        return -maxHeap[0]
```

---

## Python Code
```python
import heapq
class MedianFinder:
    def __init__(self):
        self.maxHeap = []  # lower half
        self.minHeap = []  # upper half
    def addNum(self, num):
        heapq.heappush(self.maxHeap, -num)
        heapq.heappush(self.minHeap, -heapq.heappop(self.maxHeap))
        if len(self.minHeap) > len(self.maxHeap):
            heapq.heappush(self.maxHeap, -heapq.heappop(self.minHeap))
    def findMedian(self):
        if len(self.maxHeap) > len(self.minHeap):
            return -self.maxHeap[0]
        return (-self.maxHeap[0] + self.minHeap[0]) / 2
```

---

## Key Takeaways
- Two-heap approach is optimal for streaming median.
- Always balance heaps after insertion.

---

## Follow-up
- How would you handle deletions?
  - Use a balanced BST or two heaps with delayed deletion to support removals efficiently.
- Can you do this with a balanced BST?
  - Yes, insert and remove in O(log n) and find median in O(1) or O(log n).

---

## Related Problems
- Sliding Window Median
- Kth Largest Element in a Stream

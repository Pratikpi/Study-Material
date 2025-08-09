# LeetCode: Merge Intervals - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/merge-intervals/description/)

## Problem Statement
Given an array of intervals where intervals[i] = [starti, endi], merge all overlapping intervals, and return an array of the non-overlapping intervals that cover all the intervals in the input.

### Example
- Input: intervals = [[1,3],[2,6],[8,10],[15,18]]
  Output: [[1,6],[8,10],[15,18]]

- Input: intervals = [[1,4],[4,5]]
  Output: [[1,5]]

### Constraints
- 1 <= intervals.length <= 10^4
- intervals[i].length == 2
- 0 <= starti <= endi <= 10^4

---

## Concepts Required
- Arrays
- Sorting
- Interval Merging

---

## Sorting + Merge Approach
- Sort intervals by start, merge if overlapping.
- Time Complexity: O(n log n)

### Pseudocode
```
sort intervals by start
result = [intervals[0]]
for interval in intervals[1:]:
    if interval overlaps with result[-1]:
        merge
    else:
        add to result
return result
```

---

## Python Code
```python
def merge(intervals):
    intervals.sort(key=lambda x: x[0])
    merged = [intervals[0]]
    for start, end in intervals[1:]:
        if start <= merged[-1][1]:
            merged[-1][1] = max(merged[-1][1], end)
        else:
            merged.append([start, end])
    return merged
```

---

## Key Takeaways
- Always sort intervals before merging.
- Practice both in-place and new list solutions.

---

## Follow-up
- How would you handle unsorted intervals?
  - Sort intervals by start time before merging to ensure correct merging order.
- Can you do it in-place?
  - Yes, merge into the input array and return the relevant portion, minimizing extra space usage.

---

## Related Problems
- Insert Interval
- Meeting Rooms
- Summary Ranges

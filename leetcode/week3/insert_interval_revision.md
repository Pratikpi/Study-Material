# LeetCode: Insert Interval - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/insert-interval/description/)

## Problem Statement
You are given an array of non-overlapping intervals sorted by their start time, and an interval to insert. Insert the interval and merge if necessary.

### Example
- Input: intervals = [[1,3],[6,9]], newInterval = [2,5]
  Output: [[1,5],[6,9]]

- Input: intervals = [[1,2],[3,5],[6,7],[8,10],[12,16]], newInterval = [4,8]
  Output: [[1,2],[3,10],[12,16]]

### Constraints
- 0 <= intervals.length <= 10^4
- intervals[i].length == 2
- 0 <= intervals[i][0] <= intervals[i][1] <= 10^5
- intervals is sorted by start time.

---

## Concepts Required
- Arrays
- Interval Merging
- Sorting

---

## Merge Approach
- Add all intervals before newInterval, merge overlapping, add remaining.
- Time Complexity: O(n)

### Pseudocode
```
result = []
for interval in intervals:
    if interval ends before newInterval: add to result
    elif interval starts after newInterval: add newInterval, set newInterval = interval
    else: merge intervals
add newInterval to result
return result
```

---

## Python Code
```python
def insert(intervals, newInterval):
    res = []
    for i in range(len(intervals)):
        if intervals[i][1] < newInterval[0]:
            res.append(intervals[i])
        elif intervals[i][0] > newInterval[1]:
            res.append(newInterval)
            newInterval = intervals[i]
        else:
            newInterval[0] = min(newInterval[0], intervals[i][0])
            newInterval[1] = max(newInterval[1], intervals[i][1])
    res.append(newInterval)
    return res
```

---

## Key Takeaways
- Always merge overlapping intervals.
- Practice both in-place and new list solutions.

---

## Follow-up
- How would you handle unsorted intervals?
- Can you do it in-place?

---

## Related Problems
- Merge Intervals
- Meeting Rooms
- Summary Ranges

# Interval Merging - Interview Preparation Guide

## Theory & Intuition
Interval merging is a common technique for combining overlapping intervals into a minimal set of non-overlapping intervals. This is frequently used in scheduling, calendar, and range problems.

- **Sort intervals by start time**
- **Iterate and merge**: If the current interval overlaps with the previous, merge them; otherwise, add as a new interval.

### When to Use
- When you need to combine overlapping ranges (e.g., meeting times, memory blocks).

## Example 1: Merge Intervals (Python)
```python
def merge(intervals):
    intervals.sort(key=lambda x: x[0])
    merged = []
    for interval in intervals:
        if not merged or merged[-1][1] < interval[0]:
            merged.append(interval)
        else:
            merged[-1][1] = max(merged[-1][1], interval[1])
    return merged
```

## Example 2: Insert Interval
```python
def insert(intervals, new_interval):
    result = []
    for i, (start, end) in enumerate(intervals):
        if end < new_interval[0]:
            result.append([start, end])
        elif new_interval[1] < start:
            result.append(new_interval)
            return result + intervals[i:]
        else:
            new_interval[0] = min(new_interval[0], start)
            new_interval[1] = max(new_interval[1], end)
    result.append(new_interval)
    return result
```

## Example 3: Find Gaps Between Intervals
```python
def find_gaps(intervals):
    intervals.sort()
    gaps = []
    for i in range(1, len(intervals)):
        if intervals[i][0] > intervals[i-1][1]:
            gaps.append([intervals[i-1][1], intervals[i][0]])
    return gaps
```

## Diagram
```
Intervals:   [1,3] [2,6] [8,10] [9,12]
Merged:      [1,6] [8,12]
```

## Extra Study Material
- [Merge Intervals (LeetCode)](https://leetcode.com/problems/merge-intervals/)
- [Interval Problems (GeeksforGeeks)](https://www.geeksforgeeks.org/intervals-in-data-structure/)

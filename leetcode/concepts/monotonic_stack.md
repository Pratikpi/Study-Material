# Monotonic Stack - Interview Preparation Guide

## Theory & Intuition
A monotonic stack is a stack that maintains its elements in either increasing or decreasing order. It is used to solve problems involving next/previous greater/smaller elements efficiently in O(n) time.

- **Monotonically increasing stack**: Top is always the smallest.
- **Monotonically decreasing stack**: Top is always the largest.

### When to Use
- When you need to find the next/previous greater/smaller element for each item in an array.
- Common in histogram, stock span, and temperature problems.

## Example 1: Next Greater Element
```python
def next_greater(nums):
    res = [-1] * len(nums)
    stack = []
    for i, num in enumerate(nums):
        while stack and nums[stack[-1]] < num:
            res[stack.pop()] = num
        stack.append(i)
    return res
```

## Example 2: Largest Rectangle in Histogram
```python
def largest_rectangle(heights):
    stack = []
    max_area = 0
    heights.append(0)
    for i, h in enumerate(heights):
        while stack and heights[stack[-1]] > h:
            height = heights[stack.pop()]
            width = i if not stack else i - stack[-1] - 1
            max_area = max(max_area, height * width)
        stack.append(i)
    return max_area
```

## Example 3: Daily Temperatures
```python
def daily_temperatures(T):
    res = [0] * len(T)
    stack = []
    for i, temp in enumerate(T):
        while stack and T[stack[-1]] < temp:
            idx = stack.pop()
            res[idx] = i - idx
        stack.append(i)
    return res
```

## Diagram
```
Stack (indices): [0, 1, 2]
Heights:         [2, 1, 5]
```

## Extra Study Material
- [Monotonic Stack (LeetCode)](https://leetcode.com/tag/monotonic-stack/)
- [Monotonic Stack Pattern (GeeksforGeeks)](https://www.geeksforgeeks.org/monotonic-stack/)

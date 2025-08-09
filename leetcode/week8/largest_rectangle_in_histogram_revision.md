# LeetCode: Largest Rectangle in Histogram - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/largest-rectangle-in-histogram/description/)

## Problem Statement
Given an array of integers heights representing the histogram's bar height where the width of each bar is 1, return the area of the largest rectangle in the histogram.

### Example
- Input: heights = [2,1,5,6,2,3]
  Output: 10

- Input: heights = [2,4]
  Output: 4

### Constraints
- 1 <= heights.length <= 10^5
- 0 <= heights[i] <= 10^4

---

## Concepts Required
- Stack
- Monotonic Stack
- Array Manipulation

---

## Approach
- Use a stack to keep track of indices of increasing bars.
- For each bar, pop from stack until the current bar is taller, calculate area.
- Time Complexity: O(n)

### Pseudocode
```
append 0 to heights
stack = []
max_area = 0
for i, h in enumerate(heights):
    while stack and heights[stack[-1]] > h:
        height = heights[stack.pop()]
        width = i if not stack else i - stack[-1] - 1
        max_area = max(max_area, height * width)
    stack.append(i)
return max_area
```

---

## Python Code
```python
def largestRectangleArea(heights):
    heights.append(0)
    stack = []
    max_area = 0
    for i, h in enumerate(heights):
        while stack and heights[stack[-1]] > h:
            height = heights[stack.pop()]
            width = i if not stack else i - stack[-1] - 1
            max_area = max(max_area, height * width)
        stack.append(i)
    return max_area
```

---

## Key Takeaways
- Monotonic stack is optimal for this problem.
- Always append a sentinel value to process all bars.

---

## Follow-up
- How would you solve this with divide and conquer?
  - Recursively find the minimum bar, compute area, and solve for left/right subarrays.
- Can you do this in O(n) space?
  - Yes, the stack-based approach uses O(n) space.

---

## Related Problems
- Trapping Rain Water
- Maximal Rectangle

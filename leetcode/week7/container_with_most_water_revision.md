# LeetCode: Container With Most Water - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/container-with-most-water/description/)

## Problem Statement
Given n non-negative integers a1, a2, ..., an , where each represents a point at coordinate (i, ai). n vertical lines are drawn such that the two endpoints of the line i is at (i, ai) and (i, 0). Find two lines, which together with the x-axis forms a container, such that the container contains the most water.

Return the maximum amount of water a container can store.

### Example
- Input: height = [1,8,6,2,5,4,8,3,7]
  Output: 49

- Input: height = [1,1]
  Output: 1

### Constraints
- n == height.length
- 2 <= n <= 10^5
- 0 <= height[i] <= 10^4

---

## Concepts Required
- Two Pointers
- Greedy
- Array Manipulation

---

## Approach
- Use two pointers, one at the start and one at the end.
- Calculate area, move the pointer with the shorter line inward.
- Time Complexity: O(n)

### Pseudocode
```
left = 0, right = n-1, max_area = 0
while left < right:
    area = min(height[left], height[right]) * (right - left)
    max_area = max(max_area, area)
    if height[left] < height[right]:
        left += 1
    else:
        right -= 1
return max_area
```

---

## Python Code
```python
def maxArea(height):
    left, right = 0, len(height) - 1
    max_area = 0
    while left < right:
        area = min(height[left], height[right]) * (right - left)
        max_area = max(max_area, area)
        if height[left] < height[right]:
            left += 1
        else:
            right -= 1
    return max_area
```

---

## Key Takeaways
- Two pointer technique is optimal for this problem.
- Always move the pointer at the shorter line.

---

## Follow-up
- How would you solve this with brute force?
  - Check all pairs of lines (nested loops), compute area for each, and return the maximum. Time complexity: O(n^2).
- Can you generalize this to 3D?
  - Yes, but the problem becomes more complex; you would need to consider all pairs of planes and calculate the volume between them.

---

## Related Problems
- Trapping Rain Water
- Largest Rectangle in Histogram

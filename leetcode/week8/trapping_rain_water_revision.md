# LeetCode: Trapping Rain Water - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/trapping-rain-water/description/)

## Problem Statement
Given n non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it can trap after raining.

### Example
- Input: height = [0,1,0,2,1,0,1,3,2,1,2,1]
  Output: 6

- Input: height = [4,2,0,3,2,5]
  Output: 9

### Constraints
- n == height.length
- 1 <= n <= 2 * 10^4
- 0 <= height[i] <= 10^5

---

## Concepts Required
- Two Pointers
- Dynamic Programming
- Stack

---

## Approach
- Use two pointers (left, right) and track max heights from both ends.
- Water trapped at each index = min(max_left, max_right) - height[i].
- Time Complexity: O(n)

### Pseudocode
```
left, right = 0, n-1
left_max, right_max = 0, 0
ans = 0
while left < right:
    if height[left] < height[right]:
        if height[left] >= left_max:
            left_max = height[left]
        else:
            ans += left_max - height[left]
        left += 1
    else:
        if height[right] >= right_max:
            right_max = height[right]
        else:
            ans += right_max - height[right]
        right -= 1
return ans
```

---

## Python Code
```python
def trap(height):
    left, right = 0, len(height) - 1
    left_max = right_max = 0
    ans = 0
    while left < right:
        if height[left] < height[right]:
            if height[left] >= left_max:
                left_max = height[left]
            else:
                ans += left_max - height[left]
            left += 1
        else:
            if height[right] >= right_max:
                right_max = height[right]
            else:
                ans += right_max - height[right]
            right -= 1
    return ans
```

---

## Key Takeaways
- Two pointer technique is optimal for this problem.
- Understand the concept of left/right max boundaries.

---

## Follow-up
- Can you solve this with a stack?
  - Yes, use a monotonic stack to track boundaries and calculate trapped water.
- What if the bars are circular?
  - Treat the array as circular and check wrap-around cases for boundaries.

---

## Related Problems
- Container With Most Water
- Largest Rectangle in Histogram

# Sliding Window - Interview Preparation Guide

## Theory & Intuition
The sliding window technique is used to solve problems involving contiguous subarrays or substrings. It involves maintaining a window (range) over a portion of the data and moving it to efficiently compute results.

- Fixed-size window: Window size remains constant.
- Variable-size window: Window size changes based on conditions.

### When to Use
- When you need to find subarrays/substrings with certain properties (sum, length, distinct elements, etc.).
- When brute force is too slow (O(n^2)), sliding window can often reduce to O(n).

## Example 1: Maximum Sum Subarray of Size K
```python
def max_sum_subarray(arr, k):
    window_sum = sum(arr[:k])
    max_sum = window_sum
    for i in range(k, len(arr)):
        window_sum += arr[i] - arr[i - k]
        max_sum = max(max_sum, window_sum)
    return max_sum
```

## Example 2: Longest Substring Without Repeating Characters
```python
def length_of_longest_substring(s):
    char_set = set()
    left = max_len = 0
    for right in range(len(s)):
        while s[right] in char_set:
            char_set.remove(s[left])
            left += 1
        char_set.add(s[right])
        max_len = max(max_len, right - left + 1)
    return max_len
```

## Example 3: Minimum Window Substring
```python
# LeetCode 76
from collections import Counter
def min_window(s, t):
    need, missing = Counter(t), len(t)
    left = start = end = 0
    for right, char in enumerate(s, 1):
        if need[char] > 0:
            missing -= 1
        need[char] -= 1
        if missing == 0:
            while left < right and need[s[left]] < 0:
                need[s[left]] += 1
                left += 1
            if end == 0 or right - left < end - start:
                start, end = left, right
            need[s[left]] += 1
            missing += 1
            left += 1
    return s[start:end]
```

## Diagram
```
[1, 2, 3, 4, 5], k=3
Window: [1,2,3] -> [2,3,4] -> [3,4,5]
```

## Extra Study Material
- [Sliding Window (LeetCode Explore)](https://leetcode.com/explore/learn/card/sliding-window/)
- [Sliding Window Pattern (GeeksforGeeks)](https://www.geeksforgeeks.org/window-sliding-technique/)

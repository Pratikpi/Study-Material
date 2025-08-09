# LeetCode: Minimum Window Substring - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/minimum-window-substring/description/)

## Problem Statement
Given two strings s and t, return the minimum window in s which will contain all the characters in t. If there is no such window, return the empty string "".

### Example
- Input: s = "ADOBECODEBANC", t = "ABC"
  Output: "BANC"

- Input: s = "a", t = "a"
  Output: "a"

- Input: s = "a", t = "aa"
  Output: ""

### Constraints
- 1 <= s.length, t.length <= 10^5
- s and t consist of English letters.

---

## Concepts Required
- Sliding Window
- Hash Map
- Two Pointers

---

## Approach
- Use two pointers to maintain a window.
- Expand right pointer to include characters, contract left pointer to minimize window.
- Use hash maps to count required and current characters.
- Time Complexity: O(|S| + |T|)

### Pseudocode
```
need = Counter(t)
missing = len(t)
left = start = end = 0
for right, char in enumerate(s):
    if need[char] > 0:
        missing -= 1
    need[char] -= 1
    while missing == 0:
        if right - left < end - start:
            start, end = left, right
        need[s[left]] += 1
        if need[s[left]] > 0:
            missing += 1
        left += 1
return s[start:end+1] if end < len(s) else ""
```

---

## Python Code
```python
from collections import Counter

def minWindow(s, t):
    if not t or not s:
        return ""
    need = Counter(t)
    missing = len(t)
    left = start = end = 0
    for right, char in enumerate(s):
        if need[char] > 0:
            missing -= 1
        need[char] -= 1
        while missing == 0:
            if end == 0 or right - left < end - start:
                start, end = left, right + 1
            need[s[left]] += 1
            if need[s[left]] > 0:
                missing += 1
            left += 1
    return s[start:end]
```

---

## Key Takeaways
- Sliding window is optimal for substring search.
- Use hash maps for character counting.

---

## Follow-up
- How would you handle Unicode characters?
  - Use a dictionary to count all possible characters, not just ASCII.
- Can you solve this in-place?
  - Yes, by using pointers and modifying the input string if allowed.

---

## Related Problems
- Longest Substring Without Repeating Characters
- Substring with Concatenation of All Words

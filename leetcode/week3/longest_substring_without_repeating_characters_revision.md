# LeetCode: Longest Substring Without Repeating Characters - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/longest-substring-without-repeating-characters/description/)

## Problem Statement
Given a string `s`, find the length of the longest substring without repeating characters.

### Example
- Input: s = "abcabcbb"
  Output: 3
  Explanation: The answer is "abc", with the length of 3.

- Input: s = "bbbbb"
  Output: 1

### Constraints
- 0 <= s.length <= 5 * 10^4
- s consists of English letters, digits, symbols, and spaces.

---

## Concepts Required
- Sliding Window
- Hash Map
- String

---

## Sliding Window Approach
- Use a hash map to track the last index of each character.
- Move the left pointer to avoid repeats.
- Time Complexity: O(n)

### Pseudocode
```
char_index = {}
left = 0
max_len = 0
for right, c in enumerate(s):
    if c in char_index and char_index[c] >= left:
        left = char_index[c] + 1
    char_index[c] = right
    max_len = max(max_len, right - left + 1)
return max_len
```

---

## Python Code
```python
def lengthOfLongestSubstring(s):
    char_index = {}
    left = 0
    max_len = 0
    for right, c in enumerate(s):
        if c in char_index and char_index[c] >= left:
            left = char_index[c] + 1
        char_index[c] = right
        max_len = max(max_len, right - left + 1)
    return max_len
```

---

## Key Takeaways
- Sliding window is optimal for substring problems.
- Always update the left pointer to avoid repeats.
- Practice both brute force and optimized solutions.

---

## Follow-up
- How would you return the actual substring?
  - Track start/end indices of the max window while updating the hash map.
- Can you handle Unicode characters?
  - Use a dictionary to map all possible characters, not just ASCII.

---

## Related Problems
- Longest Substring with At Most Two Distinct Characters
- Substring with Concatenation of All Words
- Minimum Window Substring

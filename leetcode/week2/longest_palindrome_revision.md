# LeetCode: Longest Palindrome - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/longest-palindrome/description/)

## Problem Statement
Given a string `s` which consists of lowercase or uppercase letters, return the length of the longest palindrome that can be built with those letters.

### Example
- Input: s = "abccccdd"
  Output: 7
  Explanation: One longest palindrome is "dccaccd", length is 7.

- Input: s = "a"
  Output: 1

### Constraints
- 1 <= s.length <= 2000
- s consists of lowercase and/or uppercase English letters only.

---

## Concepts Required
- Hash Map
- Greedy
- String

---

## Greedy Approach
- Count the frequency of each character. Use all even counts, and at most one odd count in the center.
- Time Complexity: O(n)

### Pseudocode
```
count = Counter(s)
length = 0
odd_found = False
for freq in count.values():
    length += (freq // 2) * 2
    if freq % 2 == 1:
        odd_found = True
if odd_found:
    length += 1
return length
```

---

## Python Code
```python
from collections import Counter

def longestPalindrome(s):
    count = Counter(s)
    length = 0
    odd_found = False
    for freq in count.values():
        length += (freq // 2) * 2
        if freq % 2 == 1:
            odd_found = True
    if odd_found:
        length += 1
    return length
```

---

## Key Takeaways
- Use all even character counts, and at most one odd in the center.
- Greedy is optimal for this problem.
- Practice both counting and set-based solutions.

---

## Follow-up
- How would you build the actual palindrome?
- What if the string contains Unicode characters?

---

## Related Problems
- Longest Palindromic Substring
- Palindrome Permutation
- Valid Palindrome

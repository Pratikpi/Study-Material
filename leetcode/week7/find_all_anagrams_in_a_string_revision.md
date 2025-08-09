# LeetCode: Find All Anagrams in a String - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/find-all-anagrams-in-a-string/description/)

## Problem Statement
Given two strings s and p, return all the start indices of p's anagrams in s. You may return the answer in any order.

### Example
- Input: s = "cbaebabacd", p = "abc"
  Output: [0,6]

- Input: s = "abab", p = "ab"
  Output: [0,1,2]

### Constraints
- 1 <= s.length, p.length <= 3 * 10^4
- s and p consist of lowercase English letters.

---

## Concepts Required
- Sliding Window
- Hash Map
- String

---

## Sliding Window Approach
- Use a hash map to count characters, slide window, compare counts.
- Time Complexity: O(n)

### Pseudocode
```
count_p = Counter(p)
window = Counter(s[:len(p)])
for i in range(len(s)-len(p)+1):
    if window == count_p: add i to result
    move window by one character
```

---

## Python Code
```python
from collections import Counter

def findAnagrams(s, p):
    res = []
    len_p = len(p)
    count_p = Counter(p)
    window = Counter(s[:len_p-1])
    for i in range(len_p-1, len(s)):
        window[s[i]] += 1
        if window == count_p:
            res.append(i-len_p+1)
        window[s[i-len_p+1]] -= 1
        if window[s[i-len_p+1]] == 0:
            del window[s[i-len_p+1]]
    return res
```

---

## Key Takeaways
- Sliding window is optimal for substring anagram search.
- Practice both hash map and array-based solutions.

---

## Follow-up
- How would you handle Unicode characters?
  - Use a dictionary or collections.Counter to support all possible characters.
- Can you do it with less space?
  - Yes, use fixed-size arrays for character counts if the character set is small, or optimize sliding window logic.

---

## Related Problems
- Permutation in String
- Minimum Window Substring
- Group Anagrams

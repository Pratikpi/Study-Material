# LeetCode: Valid Anagram - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/valid-anagram/description/)

## Problem Statement
Given two strings `s` and `t`, return `true` if `t` is an anagram of `s`, and `false` otherwise.

### Example
- Input: s = "anagram", t = "nagaram"
  Output: true

- Input: s = "rat", t = "car"
  Output: false

### Constraints
- 1 <= s.length, t.length <= 5 * 10^4
- s and t consist of lowercase English letters.

---

## Concepts Required
- Hash Table
- String Manipulation
- Sorting

---

## Approach 1: Sorting
- Sort both strings and compare.
- Time Complexity: O(n log n)

### Pseudocode
```
if sorted(s) == sorted(t):
    return True
else:
    return False
```

---

## Approach 2: Hash Map (Counter)
- Count the frequency of each character in both strings and compare.
- Time Complexity: O(n)

### Pseudocode
```
if Counter(s) == Counter(t):
    return True
else:
    return False
```

---

## Python Code
```python
from collections import Counter

def isAnagram(s, t):
    return Counter(s) == Counter(t)
```

---

## Key Takeaways
- Anagrams have the same character counts for each letter.
- Sorting or hash maps are common approaches.
- Practice both methods for interviews.

---

## Follow-up
- How would you handle Unicode characters?
- What if the input is very large and you cannot sort?

---

## Related Problems
- Group Anagrams
- Find All Anagrams in a String
- Palindrome Permutation

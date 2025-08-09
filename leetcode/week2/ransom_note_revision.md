# LeetCode: Ransom Note - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/ransom-note/description/)

## Problem Statement
Given two strings `ransomNote` and `magazine`, return `true` if `ransomNote` can be constructed from `magazine` and `false` otherwise.

Each letter in `magazine` can only be used once in `ransomNote`.

### Example
- Input: ransomNote = "a", magazine = "b"
  Output: false

- Input: ransomNote = "aa", magazine = "ab"
  Output: false

- Input: ransomNote = "aa", magazine = "aab"
  Output: true

### Constraints
- 1 <= ransomNote.length, magazine.length <= 10^5
- ransomNote and magazine consist of lowercase English letters.

---

## Concepts Required
- Hash Map
- String

---

## Hash Map Approach
- Count the frequency of each letter in magazine and check if ransomNote can be formed.
- Time Complexity: O(n + m)

### Pseudocode
```
count = Counter(magazine)
for c in ransomNote:
    if count[c] == 0:
        return False
    count[c] -= 1
return True
```

---

## Python Code
```python
from collections import Counter

def canConstruct(ransomNote, magazine):
    count = Counter(magazine)
    for c in ransomNote:
        if count[c] == 0:
            return False
        count[c] -= 1
    return True
```

---

## Key Takeaways
- Hash maps are optimal for letter counting problems.
- Practice both hash map and sorting approaches.

---

## Follow-up
- What if magazine is very large and ransomNote is small?
- Can you do it in one pass?

---

## Related Problems
- Jewels and Stones
- Valid Anagram
- Construct String from Binary Tree

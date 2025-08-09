# LeetCode: Longest Palindromic Substring - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/longest-palindromic-substring/description/)

## Problem Statement
Given a string s, return the longest palindromic substring in s.

### Example
- Input: s = "babad"
  Output: "bab"

- Input: s = "cbbd"
  Output: "bb"

### Constraints
- 1 <= s.length <= 1000
- s consists of only digits and English letters.

---

## Concepts Required
- Dynamic Programming
- Expand Around Center
- String

---

## Expand Around Center Approach
- For each index, expand left/right to find palindromes.
- Time Complexity: O(n^2)

### Pseudocode
```
for i in 0..n-1:
    expand(i, i)   # odd length
    expand(i, i+1) # even length
expand(l, r):
    while l>=0 and r<n and s[l]==s[r]:
        update max palindrome
        l -= 1; r += 1
```

---

## Python Code
```python
def longestPalindrome(s):
    res = ""
    for i in range(len(s)):
        for a, b in [(i, i), (i, i+1)]:
            l, r = a, b
            while l >= 0 and r < len(s) and s[l] == s[r]:
                if r - l + 1 > len(res):
                    res = s[l:r+1]
                l -= 1
                r += 1
    return res
```

---

## Key Takeaways
- Expand around center is optimal for O(n^2) time and O(1) space.
- Practice both DP and center expansion solutions.

---

## Follow-up
- How would you return the count of palindromic substrings?
  - Use DP or expand-around-center for all substrings to count palindromic substrings efficiently.
- Can you do it in O(n) time (Manacher's Algorithm)?
  - Yes, Manacher's algorithm finds all palindromic substrings in O(n) time.

---

## Related Problems
- Palindromic Substrings
- Longest Palindromic Subsequence
- Valid Palindrome

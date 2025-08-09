# LeetCode: Valid Palindrome - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/valid-palindrome/description/)

## Problem Statement
A phrase is a palindrome if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Given a string `s`, return `true` if it is a palindrome, or `false` otherwise.

### Example
- Input: s = "A man, a plan, a canal: Panama"
  Output: true

- Input: s = "race a car"
  Output: false

- Input: s = " "
  Output: true

### Constraints
- 1 <= s.length <= 2 * 10^5
- s consists only of printable ASCII characters.

---

## Concepts Required
- String Manipulation
- Two Pointers
- Regular Expressions

---

## Two Pointers Approach
- Filter the string to keep only alphanumeric characters and convert to lowercase.
- Use two pointers to compare characters from both ends.
- Time Complexity: O(n)

### Pseudocode
```
filter s to keep only alphanumeric, lowercase
left, right = 0, len(s)-1
while left < right:
    if s[left] != s[right]:
        return False
    left += 1; right -= 1
return True
```

---

## Python Code
```python
import re

def isPalindrome(s):
    s = re.sub(r'[^a-zA-Z0-9]', '', s).lower()
    return s == s[::-1]
```

---

## Key Takeaways
- Always clean the input string as required by the problem.
- Two pointers is a common pattern for palindrome problems.
- Practice both pointer and slicing solutions.

---

## Follow-up
- How would you handle Unicode characters?
- Can you do it in-place without extra space?

---

## Related Problems
- Palindrome Linked List
- Valid Palindrome II
- Longest Palindromic Substring

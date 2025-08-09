# LeetCode: String to Integer (atoi) - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/string-to-integer-atoi/description/)

## Problem Statement
Implement the myAtoi(string s) function, which converts a string to a 32-bit signed integer (similar to C/C++'s atoi).

### Example
- Input: s = "42"
  Output: 42

- Input: s = "   -42"
  Output: -42

- Input: s = "4193 with words"
  Output: 4193

### Constraints
- 0 <= s.length <= 200
- s consists of English letters, digits, spaces, '+', '-', and '.'

---

## Concepts Required
- String Parsing
- Edge Case Handling

---

## Parsing Approach
- Skip whitespace, handle sign, parse digits, clamp to 32-bit int.
- Time Complexity: O(n)

### Pseudocode
```
index = 0, sign = 1, result = 0
skip whitespace
handle sign
while digit:
    result = result*10 + digit
clamp result to [-2^31, 2^31-1]
return sign*result
```

---

## Python Code
```python
def myAtoi(s):
    i, n, sign, result = 0, len(s), 1, 0
    while i < n and s[i] == ' ': i += 1
    if i < n and s[i] in '+-':
        sign = -1 if s[i] == '-' else 1
        i += 1
    while i < n and s[i].isdigit():
        result = result * 10 + int(s[i])
        i += 1
    result *= sign
    INT_MIN, INT_MAX = -2**31, 2**31-1
    if result < INT_MIN: return INT_MIN
    if result > INT_MAX: return INT_MAX
    return result
```

---

## Key Takeaways
- Always handle whitespace, sign, and overflow.
- Practice both manual and regex-based solutions.

---

## Follow-up
- How would you handle floating point numbers?
- Can you do it with regular expressions?

---

## Related Problems
- Valid Number
- Reverse Integer
- Parse Integer

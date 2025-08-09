# LeetCode: Add Binary - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/add-binary/description/)

## Problem Statement
Given two binary strings `a` and `b`, return their sum as a binary string.

### Example
- Input: a = "11", b = "1"
  Output: "100"

- Input: a = "1010", b = "1011"
  Output: "10101"

### Constraints
- 1 <= a.length, b.length <= 10^4
- a and b consist only of '0' or '1' characters.

---

## Concepts Required
- String Manipulation
- Binary Arithmetic

---

## Approach
- Add from right to left, keeping track of carry.
- Time Complexity: O(max(n, m))

### Pseudocode
```
i, j = len(a)-1, len(b)-1
carry = 0
result = []
while i >= 0 or j >= 0 or carry:
    sum = carry
    if i >= 0: sum += int(a[i]); i -= 1
    if j >= 0: sum += int(b[j]); j -= 1
    result.append(str(sum % 2))
    carry = sum // 2
return ''.join(reversed(result))
```

---

## Python Code
```python
def addBinary(a, b):
    i, j = len(a) - 1, len(b) - 1
    carry = 0
    result = []
    while i >= 0 or j >= 0 or carry:
        total = carry
        if i >= 0:
            total += int(a[i])
            i -= 1
        if j >= 0:
            total += int(b[j])
            j -= 1
        result.append(str(total % 2))
        carry = total // 2
    return ''.join(reversed(result))
```

---

## Key Takeaways
- Always process from right to left for addition.
- Handle carry at every step.
- Practice both manual and built-in (int, bin) solutions.

---

## Follow-up
- How would you handle very large numbers?
- Can you do it in-place?

---

## Related Problems
- Add Two Numbers
- Multiply Strings
- Sum of Two Integers

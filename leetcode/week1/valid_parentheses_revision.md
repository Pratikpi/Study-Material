# LeetCode: Valid Parentheses - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/valid-parentheses/description/)

## Problem Statement
Given a string `s` containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

A string is valid if:
1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.
3. Every close bracket has a corresponding open bracket of the same type.

### Example
- Input: s = "()"
  Output: true

- Input: s = "()[]{}"
  Output: true

- Input: s = "(]"
  Output: false

- Input: s = "([])"
  Output: true

- Input: s = "([)]"
  Output: false

### Constraints
- 1 <= s.length <= 10^4
- s consists of parentheses only '()[]{}'.

---

## Concepts Required
- Stack
- String

---

## Stack Approach
- Use a stack to track open brackets.
- Push open brackets, pop and check for matching on close.
- Time Complexity: O(n)

### Pseudocode
```
stack = []
for c in s:
    if c is open:
        stack.push(c)
    else:
        if stack is empty or top doesn't match:
            return False
return stack is empty
```

---

## Python Code
```python
def isValid(s):
    stack = []
    mapping = {')': '(', '}': '{', ']': '['}
    for c in s:
        if c in mapping.values():
            stack.append(c)
        elif c in mapping:
            if not stack or stack.pop() != mapping[c]:
                return False
    return not stack
```

---

## Key Takeaways
- Stack is the standard tool for matching parentheses.
- Always check for empty stack before popping.
- Practice with different types of brackets.

---

## Follow-up
- How would you handle a string with other characters?
- Can you generate all valid combinations?

---

## Related Problems
- Generate Parentheses
- Longest Valid Parentheses
- Remove Invalid Parentheses

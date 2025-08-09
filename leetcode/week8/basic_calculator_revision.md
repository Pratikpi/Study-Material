# LeetCode: Basic Calculator - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/basic-calculator/description/)

## Problem Statement
Implement a basic calculator to evaluate a simple expression string containing non-negative integers, '+', '-', '(', ')', and spaces.

### Example
- Input: s = "1 + 1"
  Output: 2

- Input: s = " 2-1 + 2 "
  Output: 3

- Input: s = "(1+(4+5+2)-3)+(6+8)"
  Output: 23

### Constraints
- 1 <= s.length <= 3 * 10^5
- s consists of digits, '+', '-', '(', ')', and ' '.
- s represents a valid expression.

---

## Concepts Required
- Stack
- String Parsing
- Operator Precedence

---

## Approach
- Use a stack to handle parentheses and sign changes.
- Parse the string character by character, updating result and sign.
- Time Complexity: O(n)

### Pseudocode
```
stack = []
result = 0
num = 0
sign = 1
for char in s:
    if char is digit: build num
    if char is '+': result += sign * num; sign = 1; num = 0
    if char is '-': result += sign * num; sign = -1; num = 0
    if char is '(': push result and sign; reset result and sign
    if char is ')': result += sign * num; pop sign and result
return result + sign * num
```

---

## Python Code
```python
def calculate(s):
    stack = []
    result = 0
    num = 0
    sign = 1
    for c in s:
        if c.isdigit():
            num = num * 10 + int(c)
        elif c in '+-':
            result += sign * num
            sign = 1 if c == '+' else -1
            num = 0
        elif c == '(': 
            stack.append(result)
            stack.append(sign)
            result = 0
            sign = 1
        elif c == ')':
            result += sign * num
            result *= stack.pop()
            result += stack.pop()
            num = 0
    return result + sign * num
```

---

## Key Takeaways
- Stack is essential for handling nested expressions.
- Always update result and sign at each operator.

---

## Follow-up
- How would you handle multiplication and division?
  - Extend the parser to handle '*' and '/' with correct precedence.
- Can you support variables?
  - Yes, use a symbol table (dictionary) to store and retrieve variable values.

---

## Related Problems
- Basic Calculator II
- Evaluate Reverse Polish Notation

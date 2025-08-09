# LeetCode: Evaluate Reverse Polish Notation - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/evaluate-reverse-polish-notation/description/)

## Problem Statement
Evaluate the value of an arithmetic expression in Reverse Polish Notation (RPN).

Valid operators are +, -, *, and /. Each operand may be an integer or another expression.

### Example
- Input: tokens = ["2","1","+","3","*"]
  Output: 9
  Explanation: ((2 + 1) * 3) = 9

- Input: tokens = ["4","13","5","/","+"]
  Output: 6
  Explanation: (4 + (13 / 5)) = 6

### Constraints
- 1 <= tokens.length <= 10^4
- tokens[i] is either an operator or an integer in the range [-200, 200].

---

## Concepts Required
- Stack
- String Parsing

---

## Stack Approach
- Use a stack to evaluate the expression.
- Push numbers, pop for operators, apply, and push result.
- Time Complexity: O(n)

### Pseudocode
```
stack = []
for token in tokens:
    if token is number:
        stack.push(int(token))
    else:
        b = stack.pop()
        a = stack.pop()
        result = apply_operator(a, b, token)
        stack.push(result)
return stack[0]
```

---

## Python Code
```python
def evalRPN(tokens):
    stack = []
    for token in tokens:
        if token not in '+-*/':
            stack.append(int(token))
        else:
            b = stack.pop()
            a = stack.pop()
            if token == '+': stack.append(a + b)
            elif token == '-': stack.append(a - b)
            elif token == '*': stack.append(a * b)
            else: stack.append(int(a / b))
    return stack[0]
```

---

## Key Takeaways
- Stack is the standard tool for RPN evaluation.
- Always pop operands in correct order.
- Practice with all four operators and negative numbers.

---

## Follow-up
- How would you handle variables or more operators?
- Can you convert infix to postfix?

---

## Related Problems
- Basic Calculator
- Basic Calculator II
- Polish Notation

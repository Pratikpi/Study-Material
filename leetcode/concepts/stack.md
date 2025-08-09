# Stack - Interview Preparation Guide

## Theory & Intuition
A stack is a linear data structure that follows the Last-In-First-Out (LIFO) principle. Elements are added and removed from the top of the stack only.

- **Push**: Add an element to the top.
- **Pop**: Remove the top element.
- **Peek/Top**: View the top element without removing it.

### When to Use
- When you need to reverse data (e.g., undo operations, backtracking).
- For parsing expressions, evaluating syntax, or managing function calls.

## Example 1: Basic Stack Operations
```python
stack = []
stack.append(1)  # push
stack.append(2)
print(stack.pop())  # Output: 2
print(stack[-1])    # Output: 1 (peek)
```

## Example 2: Valid Parentheses
```python
def is_valid(s):
    stack = []
    mapping = {')': '(', ']': '[', '}': '{'}
    for char in s:
        if char in mapping.values():
            stack.append(char)
        elif char in mapping:
            if not stack or stack.pop() != mapping[char]:
                return False
    return not stack
```

## Example 3: Evaluate Reverse Polish Notation
```python
def evalRPN(tokens):
    stack = []
    for token in tokens:
        if token in '+-*/':
            b, a = stack.pop(), stack.pop()
            stack.append(str(eval(a + token + b)))
        else:
            stack.append(token)
    return int(stack[0])
```

## Diagram
```
Stack (top at right): [1, 2, 3] -> push(4) -> [1, 2, 3, 4]
```

## Extra Study Material
- [Stack Data Structure (GeeksforGeeks)](https://www.geeksforgeeks.org/stack-data-structure/)
- [Stack - LeetCode Explore](https://leetcode.com/explore/learn/card/queue-stack/)

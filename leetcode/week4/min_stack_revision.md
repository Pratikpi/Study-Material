# LeetCode: Min Stack - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/min-stack/description/)

## Problem Statement
Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.

### Example
- Input: ["MinStack","push","push","push","getMin","pop","top","getMin"]
         [[],[-2],[0],[-3],[],[],[],[]]
  Output: [null,null,null,null,-3,null,0,-2]

### Constraints
- Methods pop, top and getMin operations will always be called on non-empty stacks.

---

## Concepts Required
- Stack
- Design

---

## Two Stack Approach
- Use one stack for values, another for current min.
- Time Complexity: O(1) for all operations.

### Pseudocode
```
push(x): stack.push(x); min_stack.push(min(x, min_stack[-1]))
pop(): stack.pop(); min_stack.pop()
top(): return stack[-1]
getMin(): return min_stack[-1]
```

---

## Python Code
```python
class MinStack:
    def __init__(self):
        self.stack = []
        self.min_stack = [float('inf')]
    def push(self, x):
        self.stack.append(x)
        self.min_stack.append(min(x, self.min_stack[-1]))
    def pop(self):
        self.stack.pop()
        self.min_stack.pop()
    def top(self):
        return self.stack[-1]
    def getMin(self):
        return self.min_stack[-1]
```

---

## Key Takeaways
- Use an auxiliary stack to track minimums.
- Practice both one-stack and two-stack solutions.

---

## Follow-up
- How would you do it with one stack?
  - Store pairs (value, current_min) in a single stack so each entry knows the min at that point.
- Can you support O(1) space for getMin?
  - Only if the input is monotonic; otherwise, O(1) time but not O(1) space is possible. For true O(1) space, you need to encode previous mins within the stack values, but this is not general for all cases.

---

## Related Problems
- Max Stack
- Stack with Increment Operation
- Implement Queue using Stacks

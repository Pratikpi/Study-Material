# LeetCode: Implement Queue using Stacks - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/implement-queue-using-stacks/description/)

## Problem Statement
Implement a first in first out (FIFO) queue using only two stacks. The implemented queue should support all the functions of a normal queue (`push`, `peek`, `pop`, and `empty`).

### Example
- Input: ["MyQueue", "push", "push", "peek", "pop", "empty"]
         [[], [1], [2], [], [], []]
  Output: [null, null, null, 1, 1, false]

### Constraints
- 1 <= x <= 9
- At most 100 calls will be made to push, pop, peek, and empty.
- All the calls to pop and peek are valid.

---

## Concepts Required
- Stack
- Queue
- Amortized Analysis

---

## Two Stack Approach
- Use two stacks: one for input, one for output.
- Push to input stack. For pop/peek, transfer to output stack if empty.
- Time Complexity: Amortized O(1) per operation.

### Pseudocode
```
push(x): stack_in.push(x)
pop(): if stack_out empty, move all from in to out; return stack_out.pop()
peek(): if stack_out empty, move all from in to out; return stack_out[-1]
empty(): return not stack_in and not stack_out
```

---

## Python Code
```python
class MyQueue:
    def __init__(self):
        self.in_stack, self.out_stack = [], []
    def push(self, x):
        self.in_stack.append(x)
    def pop(self):
        if not self.out_stack:
            while self.in_stack:
                self.out_stack.append(self.in_stack.pop())
        return self.out_stack.pop()
    def peek(self):
        if not self.out_stack:
            while self.in_stack:
                self.out_stack.append(self.in_stack.pop())
        return self.out_stack[-1]
    def empty(self):
        return not self.in_stack and not self.out_stack
```

---

## Key Takeaways
- Two stacks can simulate a queue efficiently.
- Amortized analysis is important for understanding performance.
- Practice both stack-to-queue and queue-to-stack conversions.

---

## Follow-up
- Can you implement a stack using queues?
- What if you need to support millions of operations?

---

## Related Problems
- Implement Stack using Queues
- Design Circular Queue

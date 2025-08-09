# Recursion - Interview Preparation Guide

## Theory & Intuition
Recursion is a method of solving problems where a function calls itself as a subroutine. It breaks down a problem into smaller subproblems of the same type, solving each recursively until reaching a base case.

- **Base case**: The condition under which the recursion ends.
- **Recursive case**: The part where the function calls itself.
- **Stack**: Each recursive call is placed on the call stack.

### When to Use
- When a problem can be divided into similar subproblems.
- When the problem has a natural recursive structure (e.g., trees, divide and conquer).

## Example 1: Factorial
```python
def factorial(n):
    if n == 0:
        return 1
    return n * factorial(n-1)
```

## Example 2: Fibonacci Sequence
```python
def fib(n):
    if n <= 1:
        return n
    return fib(n-1) + fib(n-2)
```

## Example 3: Tree Traversal (Preorder)
```python
def preorder(root):
    if not root:
        return
    print(root.val)
    preorder(root.left)
    preorder(root.right)
```

## Diagram
```
Recursion tree for fib(4):
        fib(4)
       /     \
   fib(3)   fib(2)
   ...
```

## Extra Study Material
- [Recursion (GeeksforGeeks)](https://www.geeksforgeeks.org/recursion/)
- [Recursion - LeetCode Explore](https://leetcode.com/explore/learn/card/recursion-i/)

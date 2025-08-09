# LeetCode: Letter Combinations of a Phone Number - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/letter-combinations-of-a-phone-number/description/)

## Problem Statement
Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent. Return the answer in any order.

A mapping of digits to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

### Example
- Input: digits = "23"
  Output: ["ad","ae","af","bd","be","bf","cd","ce","cf"]

- Input: digits = ""
  Output: []

- Input: digits = "2"
  Output: ["a","b","c"]

### Constraints
- 0 <= digits.length <= 4
- digits[i] is a digit in the range ['2', '9'].

---

## Concepts Required
- Backtracking
- Recursion
- String Manipulation

---

## Approach
- Use backtracking to build all possible combinations.
- For each digit, append each possible letter and recurse for the next digit.
- Time Complexity: O(3^N * 4^M), N = number of digits mapping to 3 letters, M = number mapping to 4 letters.

### Pseudocode
```
if digits is empty: return []
map = { '2': 'abc', ... }
result = []
def backtrack(index, path):
    if index == len(digits):
        result.append(path)
        return
    for letter in map[digits[index]]:
        backtrack(index+1, path+letter)
backtrack(0, "")
return result
```

---

## Python Code
```python
def letterCombinations(digits):
    if not digits:
        return []
    phone = {'2': 'abc', '3': 'def', '4': 'ghi', '5': 'jkl',
             '6': 'mno', '7': 'pqrs', '8': 'tuv', '9': 'wxyz'}
    res = []
    def backtrack(i, path):
        if i == len(digits):
            res.append(path)
            return
        for c in phone[digits[i]]:
            backtrack(i+1, path+c)
    backtrack(0, "")
    return res
```

---

## Key Takeaways
- Backtracking is ideal for generating all combinations.
- Understand digit-to-letter mapping.

---

## Follow-up
- How would you handle a much larger input?
  - Use iterative or queue-based approaches to avoid recursion stack overflow and optimize memory usage.
- Can you do this iteratively?
  - Yes, build combinations level by level using a queue or iterative loops.

---

## Related Problems
- Generate Parentheses
- Subsets
- Permutations

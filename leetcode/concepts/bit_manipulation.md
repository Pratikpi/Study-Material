# Bit Manipulation - Interview Preparation Guide

## Theory & Intuition
Bit manipulation involves using bitwise operators to solve problems efficiently by directly operating on the binary representations of numbers. Common operators: AND (&), OR (|), XOR (^), NOT (~), left shift (<<), right shift (>>).

### When to Use
- Problems involving parity, subsets, unique elements, or optimization of space/time.
- Useful for toggling, setting, clearing, or checking bits.

## Example 1: Check if a Number is a Power of Two
```python
def is_power_of_two(n):
    return n > 0 and (n & (n - 1)) == 0
```

## Example 2: Find the Single Number (LeetCode 136)
```python
def single_number(nums):
    result = 0
    for num in nums:
        result ^= num
    return result
```

## Example 3: Count Set Bits
```python
def count_bits(n):
    count = 0
    while n:
        n &= n - 1
        count += 1
    return count
```

## Diagram
```
XOR Truth Table:
A B | A^B
0 0 |  0
0 1 |  1
1 0 |  1
1 1 |  0
```

## Extra Study Material
- [Bit Manipulation (LeetCode Explore)](https://leetcode.com/explore/learn/card/bit-manipulation/)
- [Bit Manipulation Tricks (GeeksforGeeks)](https://www.geeksforgeeks.org/bitwise-hacks-for-competitive-programming/)

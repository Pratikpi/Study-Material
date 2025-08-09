# LeetCode: Majority Element - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/majority-element/description/)

## Problem Statement
Given an array `nums` of size n, return the majority element. The majority element is the element that appears more than ⌊n / 2⌋ times. You may assume that the majority element always exists in the array.

### Example
- Input: nums = [3,2,3]
  Output: 3

- Input: nums = [2,2,1,1,1,2,2]
  Output: 2

### Constraints
- n == nums.length
- 1 <= n <= 5 * 10^4
- -10^9 <= nums[i] <= 10^9

---

## Concepts Required
- Arrays
- Hash Map
- Boyer-Moore Voting Algorithm

---

## Boyer-Moore Voting Algorithm
- Track a candidate and a count. If count is 0, set candidate. If current num == candidate, increment count, else decrement.
- Time Complexity: O(n)
- Space Complexity: O(1)

### Pseudocode
```
candidate = None
count = 0
for num in nums:
    if count == 0:
        candidate = num
    count += (1 if num == candidate else -1)
return candidate
```

---

## Python Code
```python
def majorityElement(nums):
    count = 0
    candidate = None
    for num in nums:
        if count == 0:
            candidate = num
        count += (1 if num == candidate else -1)
    return candidate
```

---

## Key Takeaways
- Boyer-Moore is optimal for majority element.
- Hash maps can also be used but require extra space.
- Practice both approaches for interviews.

---

## Follow-up
- How would you solve it if the majority element may not exist?
- What if you need to find all elements appearing more than n/3 times?

---

## Related Problems
- Majority Element II
- Find the Duplicate Number
- Find All Duplicates in an Array

# LeetCode: Contains Duplicate - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/contains-duplicate/description/)

## Problem Statement
Given an integer array `nums`, return `true` if any value appears at least twice in the array, and return `false` if every element is distinct.

### Example
- Input: nums = [1,2,3,1]
  Output: true

- Input: nums = [1,2,3,4]
  Output: false

### Constraints
- 1 <= nums.length <= 10^5
- -10^9 <= nums[i] <= 10^9

---

## Concepts Required
- Arrays
- Hash Set

---

## Hash Set Approach
- Use a set to track seen elements.
- Time Complexity: O(n)

### Pseudocode
```
seen = set()
for num in nums:
    if num in seen:
        return True
    seen.add(num)
return False
```

---

## Python Code
```python
def containsDuplicate(nums):
    seen = set()
    for num in nums:
        if num in seen:
            return True
        seen.add(num)
    return False
```

---

## Key Takeaways
- Hash sets are optimal for duplicate detection.
- Practice both brute force and hash set solutions.

---

## Follow-up
- How would you solve it if you cannot use extra space?
  - Sort the array and check for adjacent duplicates in one pass.
- What if the array is sorted?
  - Just check for adjacent duplicates in one pass; no extra space needed.

---

## Related Problems
- Contains Duplicate II
- Contains Duplicate III
- Find All Duplicates in an Array

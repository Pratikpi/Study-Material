# LeetCode: Sort Colors - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/sort-colors/description/)

## Problem Statement
Given an array nums with n objects colored red, white, or blue, sort them in-place so that objects of the same color are adjacent, with the colors in the order red, white, and blue. Use integers 0, 1, and 2 to represent the colors.

### Example
- Input: nums = [2,0,2,1,1,0]
  Output: [0,0,1,1,2,2]

- Input: nums = [2,0,1]
  Output: [0,1,2]

### Constraints
- 1 <= nums.length <= 300
- nums[i] in {0,1,2}

---

## Concepts Required
- Arrays
- Two Pointers
- Dutch National Flag Algorithm

---

## Dutch National Flag Algorithm
- Use three pointers: low, mid, high.
- Time Complexity: O(n)

### Pseudocode
```
low, mid, high = 0, 0, len(nums)-1
while mid <= high:
    if nums[mid] == 0:
        swap nums[low], nums[mid]; low += 1; mid += 1
    elif nums[mid] == 1:
        mid += 1
    else:
        swap nums[mid], nums[high]; high -= 1
```

---

## Python Code
```python
def sortColors(nums):
    low, mid, high = 0, 0, len(nums) - 1
    while mid <= high:
        if nums[mid] == 0:
            nums[low], nums[mid] = nums[mid], nums[low]
            low += 1
            mid += 1
        elif nums[mid] == 1:
            mid += 1
        else:
            nums[mid], nums[high] = nums[high], nums[mid]
            high -= 1
```

---

## Key Takeaways
- Dutch National Flag is optimal for 3-way partitioning.
- Practice both counting and two-pointer solutions.

---

## Follow-up
- How would you generalize to k colors?
  - Use counting sort or a variant of the Dutch National Flag algorithm for k buckets.
- Can you do it with counting sort?
  - Yes, count occurrences of each color and overwrite the array in order.

---

## Related Problems
- Sort List
- Wiggle Sort II
- Partition List

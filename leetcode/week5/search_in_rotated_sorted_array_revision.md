# LeetCode: Search in Rotated Sorted Array - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/search-in-rotated-sorted-array/description/)

## Problem Statement
Given a sorted array that is rotated at an unknown pivot, and a target value, return its index if found, else -1. Must run in O(log n) time.

### Example
- Input: nums = [4,5,6,7,0,1,2], target = 0
  Output: 4

- Input: nums = [4,5,6,7,0,1,2], target = 3
  Output: -1

### Constraints
- 1 <= nums.length <= 5000
- -10^4 <= nums[i] <= 10^4
- All values of nums are unique.

---

## Concepts Required
- Binary Search
- Arrays
- Search Space Reduction

---

## Modified Binary Search Approach
- Find which half is sorted, adjust search accordingly.
- Time Complexity: O(log n)

### Pseudocode
```
left, right = 0, len(nums)-1
while left <= right:
    mid = (left + right) // 2
    if nums[mid] == target: return mid
    if nums[left] <= nums[mid]:
        if nums[left] <= target < nums[mid]: right = mid-1
        else: left = mid+1
    else:
        if nums[mid] < target <= nums[right]: left = mid+1
        else: right = mid-1
return -1
```

---

## Python Code
```python
def search(nums, target):
    left, right = 0, len(nums) - 1
    while left <= right:
        mid = (left + right) // 2
        if nums[mid] == target:
            return mid
        if nums[left] <= nums[mid]:
            if nums[left] <= target < nums[mid]:
                right = mid - 1
            else:
                left = mid + 1
        else:
            if nums[mid] < target <= nums[right]:
                left = mid + 1
            else:
                right = mid - 1
    return -1
```

---

## Key Takeaways
- Modified binary search is optimal for rotated arrays.
- Always check which half is sorted.

---

## Follow-up
- How would you handle duplicates?
  - Add extra checks when nums[mid] == nums[left] to skip duplicates and avoid ambiguity in binary search.
- Can you find the minimum in a rotated array?
  - Use modified binary search to find the inflection point (minimum element) efficiently.

---

## Related Problems
- Find Minimum in Rotated Sorted Array
- Search in Rotated Sorted Array II
- Search Insert Position

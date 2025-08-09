# LeetCode: Binary Search - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/binary-search/description/)

## Problem Statement
Given a sorted array of integers `nums` and an integer `target`, return the index of `target` if it exists in the array, otherwise return -1.

- The algorithm must run in O(log n) time.

### Example
- Input: nums = [-1,0,3,5,9,12], target = 9
  Output: 4
  Explanation: 9 exists in nums and its index is 4

- Input: nums = [-1,0,3,5,9,12], target = 2
  Output: -1
  Explanation: 2 does not exist in nums so return -1

### Constraints
- 1 <= nums.length <= 10^4
- -10^4 < nums[i], target < 10^4
- All the integers in nums are unique.
- nums is sorted in ascending order.

---

## Concepts Required
- Arrays
- Binary Search
- Time Complexity Analysis

---

## Binary Search Approach
- Use two pointers (left and right) to narrow down the search space.
- Calculate the middle index and compare with target.
- Adjust pointers based on comparison.
- Time Complexity: O(log n)

### Pseudocode
```
left = 0, right = len(nums) - 1
while left <= right:
    mid = (left + right) // 2
    if nums[mid] == target:
        return mid
    elif nums[mid] < target:
        left = mid + 1
    else:
        right = mid - 1
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
        elif nums[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1
```

---

## Key Takeaways
- Binary search is optimal for searching in sorted arrays.
- Always check for off-by-one errors in the loop condition.
- Practice both iterative and recursive implementations.

---

## Follow-up
- How would you modify the algorithm to return the index of the first or last occurrence if duplicates exist?
  - Adjust binary search to continue searching left/right after finding a match: for first occurrence, move right=mid-1; for last, move left=mid+1.
- Can you implement binary search recursively?
  - Yes, use a helper function with left/right bounds and call itself recursively until the base case is reached.

---

## Related Problems
- Search Insert Position
- Find Minimum in Rotated Sorted Array
- First Bad Version

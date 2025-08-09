# Dutch National Flag Algorithm - Interview Preparation Guide

## Theory & Intuition
The Dutch National Flag algorithm is a three-way partitioning algorithm that sorts an array of 0s, 1s, and 2s (or any three distinct values) in a single pass. It is named after the Dutch flag, which has three colors.

- **Three pointers**: low, mid, high.
- **Single pass**: O(n) time, O(1) space.

### When to Use
- When you need to sort arrays with three distinct values (e.g., sort colors problem).
- When you want an in-place, linear time solution.

## Example 1: Sort Colors (LeetCode 75)
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

## Example 2: Partition Array Around a Pivot
```python
def partition(nums, pivot):
    low, mid, high = 0, 0, len(nums) - 1
    while mid <= high:
        if nums[mid] < pivot:
            nums[low], nums[mid] = nums[mid], nums[low]
            low += 1
            mid += 1
        elif nums[mid] == pivot:
            mid += 1
        else:
            nums[mid], nums[high] = nums[high], nums[mid]
            high -= 1
```

## Example 3: Three-Way Partitioning for Quicksort
```python
def quicksort_3way(nums, lo, hi):
    if lo >= hi:
        return
    lt, i, gt = lo, lo+1, hi
    pivot = nums[lo]
    while i <= gt:
        if nums[i] < pivot:
            nums[lt], nums[i] = nums[i], nums[lt]
            lt += 1
            i += 1
        elif nums[i] > pivot:
            nums[i], nums[gt] = nums[gt], nums[i]
            gt -= 1
        else:
            i += 1
    quicksort_3way(nums, lo, lt-1)
    quicksort_3way(nums, gt+1, hi)
```

## Diagram
```
[0,1,2,0,1,2] → [0,0,1,1,2,2]
low→   mid→   ←high
```

## Extra Study Material
- [Dutch National Flag Problem (GeeksforGeeks)](https://www.geeksforgeeks.org/sort-an-array-of-0s-1s-and-2s/)
- [Sort Colors - LeetCode](https://leetcode.com/problems/sort-colors/)

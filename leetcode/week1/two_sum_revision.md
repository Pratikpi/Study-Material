# LeetCode: Two Sum - Interview Revision Guide

## Problem Statement
Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to `target`.

- Each input has exactly one solution.
- You may not use the same element twice.
- Return the answer in any order.

### Example
- Input: nums = [2,7,11,15], target = 9
  Output: [0,1]
  Explanation: nums[0] + nums[1] == 9

- Input: nums = [3,2,4], target = 6
  Output: [1,2]

- Input: nums = [3,3], target = 6
  Output: [0,1]

### Constraints
- 2 <= nums.length <= 10^4
- -10^9 <= nums[i] <= 10^9
- -10^9 <= target <= 10^9
- Only one valid answer exists.

---

## Concepts Required
- Arrays
- Hash Tables (Dictionaries/Maps)
- Time Complexity Analysis

---

## Brute Force Approach
- Check every pair of numbers to see if they sum to the target.
- Time Complexity: O(n^2)

### Pseudocode
```
for i from 0 to n-1:
    for j from i+1 to n-1:
        if nums[i] + nums[j] == target:
            return [i, j]
```

---

## Optimized Approach (Hash Map)
- Use a hash map to store value -> index as you iterate.
- For each number, check if (target - number) exists in the map.
- If yes, return indices.
- Time Complexity: O(n)
- Space Complexity: O(n)

### Pseudocode
```
map = {}
for i from 0 to n-1:
    complement = target - nums[i]
    if complement in map:
        return [map[complement], i]
    map[nums[i]] = i
```

---

## Python Code
```python
def twoSum(nums, target):
    num_to_index = {}
    for i, num in enumerate(nums):
        complement = target - num
        if complement in num_to_index:
            return [num_to_index[complement], i]
        num_to_index[num] = i
```

---

## Key Takeaways
- Always look for ways to reduce time complexity using extra space (hashing).
- Practice writing both brute force and optimized solutions.
- Understand how to use dictionaries/maps for quick lookups.

---

## Follow-up
- Can you solve it in one pass?
- What if the input array is sorted? (Try two pointers)

---

## Related Problems
- 3Sum
- 4Sum
- Two Sum II (sorted array)
- Subarray Sum Equals K

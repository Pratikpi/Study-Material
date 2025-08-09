# Meet in the Middle - Interview Preparation Guide

## Theory & Intuition
Meet in the middle is an algorithmic technique used to solve problems with exponential search space (typically n ≤ 40) by splitting the problem into two halves, solving each half independently, and then combining the results. It is often used for subset sum, knapsack, and combinatorial problems.

- **Divide**: Split the set into two halves.
- **Conquer**: Generate all possible sums/subsets for each half.
- **Combine**: Use binary search or hashing to efficiently combine results.
- **Time complexity**: O(2^(n/2) * n)

### When to Use
- When n is too large for brute force (n ≈ 30-40), but too small for DP.
- When the problem involves subsets, sums, or combinations.

## Example 1: Subset Sum (Meet in the Middle)
```python
def subset_sum(nums, target):
    from bisect import bisect_right
    n = len(nums)
    left, right = nums[:n//2], nums[n//2:]
    sums_left = [0]
    for num in left:
        sums_left += [num + x for x in sums_left]
    sums_right = [0]
    for num in right:
        sums_right += [num + x for x in sums_right]
    sums_right.sort()
    res = 0
    for s in sums_left:
        idx = bisect_right(sums_right, target - s)
        res += idx
    return res
```

## Example 2: Knapsack (Meet in the Middle)
```python
# Similar to subset sum, generate all possible weights/values for each half, then combine.
```

## Example 3: Partition to K Equal Sums
```python
# Use meet in the middle to generate all subset sums for each half, then match.
```

## Diagram
```
Split: [a, b, c, d] → [a, b] and [c, d]
Generate all subset sums for each, then combine.
```

## Extra Study Material
- [Meet in the Middle (GeeksforGeeks)](https://www.geeksforgeeks.org/meet-in-the-middle/)
- [Meet in the Middle (LeetCode Discuss)](https://leetcode.com/discuss/general-discussion/1127236/meet-in-the-middle-algorithm-explained)

# LeetCode: Maximum Profit in Job Scheduling - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/maximum-profit-in-job-scheduling/description/)

## Problem Statement
Given n jobs, where every job is represented by startTime[i], endTime[i], and profit[i], return the maximum profit you can take such that no two jobs overlap.

### Example
- Input: startTime = [1,2,3,3], endTime = [3,4,5,6], profit = [50,10,40,70]
  Output: 120

- Input: startTime = [1,2,3,4,6], endTime = [3,5,10,6,9], profit = [20,20,100,70,60]
  Output: 150

### Constraints
- 1 <= startTime.length == endTime.length == profit.length <= 5 * 10^4
- 1 <= startTime[i] < endTime[i] <= 10^9
- 1 <= profit[i] <= 10^4

---

## Concepts Required
- Dynamic Programming
- Binary Search
- Sorting

---

## Approach
- Sort jobs by end time.
- For each job, use binary search to find the last non-overlapping job.
- DP[i] = max(DP[i-1], profit[i] + DP[last_non_overlap])
- Time Complexity: O(n log n)

### Pseudocode
```
jobs = sorted by end time
DP = [0]
for each job:
    use binary search to find last job that ends <= current start
    DP.append(max(DP[-1], DP[idx+1] + profit))
return DP[-1]
```

---

## Python Code
```python
import bisect

def jobScheduling(startTime, endTime, profit):
    jobs = sorted(zip(startTime, endTime, profit), key=lambda x: x[1])
    dp = [(0, 0)]  # (end, profit)
    for s, e, p in jobs:
        i = bisect.bisect_right(dp, (s, float('inf'))) - 1
        if dp[i][1] + p > dp[-1][1]:
            dp.append((e, dp[i][1] + p))
    return dp[-1][1]
```

---

## Key Takeaways
- DP with binary search is optimal for weighted job scheduling.
- Always sort jobs by end time.

---

## Follow-up
- How would you handle jobs with dependencies?
  - Build a dependency graph and use topological sort before scheduling.
- Can you do this with less space?
  - Optimize DP to use only necessary previous states or compress the DP array.

---

## Related Problems
- Weighted Interval Scheduling
- Non-overlapping Intervals

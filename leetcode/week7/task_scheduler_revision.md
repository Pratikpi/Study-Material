# LeetCode: Task Scheduler - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/task-scheduler/description/)

## Problem Statement
Given a list of tasks and a non-negative integer n, representing the cooldown period, return the least number of units of time that the CPU will take to finish all the given tasks.

### Example
- Input: tasks = ["A","A","A","B","B","B"], n = 2
  Output: 8

- Input: tasks = ["A","A","A","B","B","B"], n = 0
  Output: 6

### Constraints
- 1 <= tasks.length <= 10^4
- tasks[i] is an uppercase English letter.
- 0 <= n <= 100

---

## Concepts Required
- Greedy
- Heap (Priority Queue)
- Counting

---

## Greedy Approach
- Count task frequencies, schedule most frequent first, fill idle slots.
- Time Complexity: O(n)

### Pseudocode
```
count = Counter(tasks)
max_freq = max(count.values())
max_count = number of tasks with max_freq
intervals = (max_freq-1)*(n+1) + max_count
return max(len(tasks), intervals)
```

---

## Python Code
```python
from collections import Counter

def leastInterval(tasks, n):
    count = Counter(tasks)
    max_freq = max(count.values())
    max_count = sum(1 for v in count.values() if v == max_freq)
    intervals = (max_freq - 1) * (n + 1) + max_count
    return max(len(tasks), intervals)
```

---

## Key Takeaways
- Greedy is optimal for minimizing idle time.
- Practice both heap and formula-based solutions.

---

## Follow-up
- How would you return the actual schedule?
  - Simulate the scheduling process, keeping track of time and idle slots, and build the schedule as you assign tasks.
- Can you do it with a heap?
  - Yes, use a max-heap to always pick the task with the highest remaining count.

---

## Related Problems
- Reorganize String
- Rearrange Barcodes
- Distant Barcodes

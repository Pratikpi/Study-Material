# Hash Map - Interview Preparation Guide

## Theory & Intuition
A hash map (or hash table/dictionary) is a data structure that stores key-value pairs and allows for fast insertion, deletion, and lookup, typically in O(1) average time.

- **Hash function**: Maps keys to indices in an array.
- **Collision resolution**: Handles cases where multiple keys map to the same index (e.g., chaining, open addressing).

### When to Use
- When you need to associate values with unique keys.
- When you need fast lookups, insertions, or deletions.

## Example 1: Basic Usage
```python
hm = {}
hm['a'] = 1
hm['b'] = 2
print(hm['a'])  # Output: 1
```

## Example 2: Counting Frequencies
```python
from collections import Counter
arr = [1,2,2,3,3,3]
cnt = Counter(arr)
print(cnt[2])  # Output: 2
```

## Example 3: Grouping Anagrams
```python
def group_anagrams(strs):
    hm = {}
    for s in strs:
        key = tuple(sorted(s))
        hm.setdefault(key, []).append(s)
    return list(hm.values())
```

## Diagram
```
Key:   "cat"  "dog"  "bat"
Index:   2      5      7
Table: [ , ,"cat", , ,"dog", ,"bat", ...]
```

## Extra Study Material
- [Hash Table (GeeksforGeeks)](https://www.geeksforgeeks.org/hashing-data-structure/)
- [Hash Map - LeetCode Explore](https://leetcode.com/explore/learn/card/hash-table/)

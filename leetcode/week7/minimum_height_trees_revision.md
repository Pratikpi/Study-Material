# LeetCode: Minimum Height Trees - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/minimum-height-trees/description/)

## Problem Statement
Given a tree with n nodes labeled from 0 to n-1, and a list of edges, return all the root labels for minimum height trees.

### Example
- Input: n = 4, edges = [[1,0],[1,2],[1,3]]
  Output: [1]

- Input: n = 6, edges = [[3,0],[3,1],[3,2],[3,4],[5,4]]
  Output: [3,4]

### Constraints
- 1 <= n <= 2 * 10^4
- edges.length == n - 1
- 0 <= ai, bi < n

---

## Concepts Required
- Graph
- Topological Sort
- Tree Pruning

---

## Tree Pruning Approach
- Remove leaves layer by layer until 1 or 2 nodes remain.
- Time Complexity: O(n)

### Pseudocode
```
build graph
leaves = all nodes with 1 neighbor
while n > 2:
    n -= len(leaves)
    remove leaves, update new leaves
return remaining nodes
```

---

## Python Code
```python
from collections import defaultdict, deque

def findMinHeightTrees(n, edges):
    if n == 1: return [0]
    graph = defaultdict(set)
    for a, b in edges:
        graph[a].add(b)
        graph[b].add(a)
    leaves = [i for i in range(n) if len(graph[i]) == 1]
    while n > 2:
        n -= len(leaves)
        new_leaves = []
        for leaf in leaves:
            neighbor = graph[leaf].pop()
            graph[neighbor].remove(leaf)
            if len(graph[neighbor]) == 1:
                new_leaves.append(neighbor)
        leaves = new_leaves
    return leaves
```

---

## Key Takeaways
- Tree pruning is optimal for minimum height trees.
- Practice both BFS and DFS approaches.

---

## Follow-up
- How would you return the actual tree structure?
  - Track parent/child relationships as you trim leaves, or reconstruct the tree from the remaining nodes.
- Can you do it with DFS?
  - Yes, use DFS to find the longest path (diameter) and identify the center(s) as roots.

---

## Related Problems
- Centroid of a Tree
- Tree Diameter
- Graph Valid Tree

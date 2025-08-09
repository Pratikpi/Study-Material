# Cycle Detection - Interview Preparation Guide

## Theory & Intuition
Cycle detection is the process of determining whether a cycle exists in a graph or linked list. A cycle occurs when a path leads back to a previously visited node.

- **Directed vs. Undirected**: Techniques differ for each.
- **DFS coloring**: For directed graphs, use colors (white, gray, black) to track node states.
- **Union Find**: For undirected graphs, use disjoint set to detect cycles.
- **Floyd's Tortoise and Hare**: For linked lists, use two pointers.

### When to Use
- To detect infinite loops, deadlocks, or validate acyclic structures (e.g., course schedule, linked list cycle).

## Example 1: Cycle Detection in Directed Graph (DFS Coloring)
```python
def has_cycle(graph):
    WHITE, GRAY, BLACK = 0, 1, 2
    color = {u: WHITE for u in graph}
    def dfs(u):
        color[u] = GRAY
        for v in graph[u]:
            if color[v] == GRAY:
                return True
            if color[v] == WHITE and dfs(v):
                return True
        color[u] = BLACK
        return False
    return any(dfs(u) for u in graph if color[u] == WHITE)
```

## Example 2: Cycle Detection in Undirected Graph (Union Find)
```python
def has_cycle_undirected(n, edges):
    parent = list(range(n))
    def find(x):
        if parent[x] != x:
            parent[x] = find(parent[x])
        return parent[x]
    for u, v in edges:
        pu, pv = find(u), find(v)
        if pu == pv:
            return True
        parent[pu] = pv
    return False
```

## Example 3: Cycle Detection in Linked List (Floyd's Algorithm)
```python
def has_cycle(head):
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow == fast:
            return True
    return False
```

## Diagram
```
Graph: 0 → 1 → 2 → 0 (cycle)
Linked List: 1 → 2 → 3 → 4 ↘
                        ↑---
```

## Extra Study Material
- [Cycle Detection (GeeksforGeeks)](https://www.geeksforgeeks.org/detect-cycle-in-a-graph/)
- [Linked List Cycle - LeetCode](https://leetcode.com/problems/linked-list-cycle/)

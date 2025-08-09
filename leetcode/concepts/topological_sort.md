# Topological Sort - Interview Preparation Guide

## Theory & Intuition
Topological sort is an ordering of the vertices in a directed acyclic graph (DAG) such that for every directed edge u → v, vertex u comes before v in the ordering.

- **Only possible for DAGs**
- **Used for scheduling, dependency resolution, course order, etc.**

### When to Use
- When you need to order tasks with dependencies (e.g., course schedule, build systems).

## Example 1: Kahn's Algorithm (BFS)
```python
from collections import deque

def topo_sort_kahn(graph):
    in_degree = {u: 0 for u in graph}
    for u in graph:
        for v in graph[u]:
            in_degree[v] += 1
    queue = deque([u for u in graph if in_degree[u] == 0])
    order = []
    while queue:
        u = queue.popleft()
        order.append(u)
        for v in graph[u]:
            in_degree[v] -= 1
            if in_degree[v] == 0:
                queue.append(v)
    return order if len(order) == len(graph) else []
```

## Example 2: DFS-Based Topological Sort
```python
def topo_sort_dfs(graph):
    visited = set()
    order = []
    def dfs(u):
        visited.add(u)
        for v in graph[u]:
            if v not in visited:
                dfs(v)
        order.append(u)
    for u in graph:
        if u not in visited:
            dfs(u)
    return order[::-1]
```

## Example 3: Course Schedule
```python
def can_finish(numCourses, prerequisites):
    graph = {i: [] for i in range(numCourses)}
    for a, b in prerequisites:
        graph[b].append(a)
    order = topo_sort_kahn(graph)
    return len(order) == numCourses
```

## Diagram
```
A → B → C
|         
→ D      
Topological order: A, D, B, C
```

## Extra Study Material
- [Topological Sorting (GeeksforGeeks)](https://www.geeksforgeeks.org/topological-sorting/)
- [Course Schedule - LeetCode](https://leetcode.com/problems/course-schedule/)

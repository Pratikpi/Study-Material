# Recursion with Graph - Interview Preparation Guide

## Theory & Intuition
Graphs are collections of nodes (vertices) and edges. Many graph algorithms (DFS, connected components, cycle detection) are naturally implemented with recursion, especially when exploring all reachable nodes from a starting point.

- Recursion is used for DFS, topological sort, and component labeling.
- Be careful to track visited nodes to avoid infinite loops in cyclic graphs.

### When to Use
- When you need to explore all nodes reachable from a source.
- When the problem involves connectivity, cycles, or pathfinding.

## Example 1: DFS for Connected Components
```python
def dfs(graph, node, visited):
    visited.add(node)
    for neighbor in graph[node]:
        if neighbor not in visited:
            dfs(graph, neighbor, visited)
```

## Example 2: Cycle Detection in Directed Graph
```python
def has_cycle(graph):
    visited, rec_stack = set(), set()
    def dfs(node):
        visited.add(node)
        rec_stack.add(node)
        for neighbor in graph[node]:
            if neighbor not in visited:
                if dfs(neighbor):
                    return True
            elif neighbor in rec_stack:
                return True
        rec_stack.remove(node)
        return False
    for node in graph:
        if node not in visited:
            if dfs(node):
                return True
    return False
```

## Example 3: Topological Sort
```python
def topo_sort(graph):
    visited, stack = set(), []
    def dfs(node):
        visited.add(node)
        for neighbor in graph[node]:
            if neighbor not in visited:
                dfs(neighbor)
        stack.append(node)
    for node in graph:
        if node not in visited:
            dfs(node)
    return stack[::-1]
```

## Diagram
```
A -> B -> C
|         |
+----> D -+
```

## Extra Study Material
- [Graph Recursion (LeetCode Explore)](https://leetcode.com/explore/learn/card/graph/)
- [Graph Recursion (GeeksforGeeks)](https://www.geeksforgeeks.org/depth-first-search-or-dfs-for-a-graph/)

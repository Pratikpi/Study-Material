# LeetCode: Clone Graph - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/clone-graph/description/)

## Problem Statement
Given a reference of a node in a connected undirected graph, return a deep copy (clone) of the graph.

Each node contains a value and a list of its neighbors.

### Example
- Input: adjList = [[2,4],[1,3],[2,4],[1,3]]
  Output: [[2,4],[1,3],[2,4],[1,3]]

### Constraints
- The number of nodes in the graph is in the range [0, 100].
- 1 <= Node.val <= 100
- Node.val is unique for each node.
- The graph is connected and undirected.

---

## Concepts Required
- Graph Traversal (DFS/BFS)
- Hash Map (for visited nodes)
- Recursion

---

## DFS Approach
- Use a hash map to map original nodes to their clones.
- Recursively clone neighbors.
- Time Complexity: O(N), N = number of nodes

### Pseudocode
```
visited = {}
def clone(node):
    if node in visited:
        return visited[node]
    copy = Node(node.val)
    visited[node] = copy
    for neighbor in node.neighbors:
        copy.neighbors.append(clone(neighbor))
    return copy
```

---

## Python Code
```python
def cloneGraph(node):
    if not node:
        return None
    visited = {}
    def dfs(n):
        if n in visited:
            return visited[n]
        copy = Node(n.val)
        visited[n] = copy
        for neighbor in n.neighbors:
            copy.neighbors.append(dfs(neighbor))
        return copy
    return dfs(node)
```

---

## Key Takeaways
- Use a hash map to avoid infinite loops and duplicate nodes.
- Practice both DFS and BFS approaches.

---

## Follow-up
- How would you handle a directed or disconnected graph?
- Can you do it iteratively?

---

## Related Problems
- Copy List with Random Pointer
- Course Schedule
- Graph Valid Tree

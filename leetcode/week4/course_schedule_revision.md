# LeetCode: Course Schedule - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/course-schedule/description/)

## Problem Statement
There are a total of numCourses courses you have to take, labeled from 0 to numCourses - 1. Some courses have prerequisites. Return true if you can finish all courses.

### Example
- Input: numCourses = 2, prerequisites = [[1,0]]
  Output: true

- Input: numCourses = 2, prerequisites = [[1,0],[0,1]]
  Output: false

### Constraints
- 1 <= numCourses <= 2000
- 0 <= prerequisites.length <= 5000
- prerequisites[i].length == 2

---

## Concepts Required
- Graph
- Topological Sort
- Cycle Detection

---

## BFS (Kahn's Algorithm) Approach
- Build graph, count in-degrees, process nodes with zero in-degree.
- Time Complexity: O(V + E)

### Pseudocode
```
graph = adjacency list
in_degree = [0]*numCourses
for prereq in prerequisites:
    build graph, update in_degree
queue = all nodes with in_degree 0
count = 0
while queue:
    node = queue.pop()
    count += 1
    for neighbor in graph[node]:
        in_degree[neighbor] -= 1
        if in_degree[neighbor] == 0:
            queue.append(neighbor)
return count == numCourses
```

---

## Python Code
```python
from collections import deque, defaultdict

def canFinish(numCourses, prerequisites):
    graph = defaultdict(list)
    in_degree = [0] * numCourses
    for dest, src in prerequisites:
        graph[src].append(dest)
        in_degree[dest] += 1
    queue = deque([i for i in range(numCourses) if in_degree[i] == 0])
    count = 0
    while queue:
        node = queue.popleft()
        count += 1
        for neighbor in graph[node]:
            in_degree[neighbor] -= 1
            if in_degree[neighbor] == 0:
                queue.append(neighbor)
    return count == numCourses
```

---

## Key Takeaways
- Topological sort is key for course scheduling.
- Practice both BFS and DFS cycle detection.

---

## Follow-up
- How would you return the order of courses?
  - Use topological sort (Kahn's algorithm or DFS postorder) to return a valid course order.
- Can you detect cycles with DFS?
  - Yes, by marking nodes as visiting/visited and checking for back edges during DFS traversal.

---

## Related Problems
- Course Schedule II
- Alien Dictionary
- Minimum Height Trees

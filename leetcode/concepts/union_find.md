# Union Find (Disjoint Set) - Interview Preparation Guide

## Theory & Intuition
Union Find, or Disjoint Set Union (DSU), is a data structure that keeps track of a set of elements partitioned into disjoint (non-overlapping) subsets. It supports two main operations efficiently:
- **Find**: Determine which subset a particular element is in.
- **Union**: Join two subsets into a single subset.

Optimizations:
- **Path compression**: Flattens the structure of the tree whenever Find is called.
- **Union by rank/size**: Always attach the smaller tree to the root of the larger tree.

### When to Use
- When you need to efficiently track connected components (e.g., Kruskal's MST, cycle detection in graphs, accounts merge).

## Example 1: Basic Union Find
```python
class UnionFind:
    def __init__(self, n):
        self.parent = list(range(n))
    def find(self, x):
        if self.parent[x] != x:
            self.parent[x] = self.find(self.parent[x])
        return self.parent[x]
    def union(self, x, y):
        self.parent[self.find(x)] = self.find(y)
```

## Example 2: Union by Rank
```python
class UnionFind:
    def __init__(self, n):
        self.parent = list(range(n))
        self.rank = [0]*n
    def find(self, x):
        if self.parent[x] != x:
            self.parent[x] = self.find(self.parent[x])
        return self.parent[x]
    def union(self, x, y):
        xr, yr = self.find(x), self.find(y)
        if xr == yr: return
        if self.rank[xr] < self.rank[yr]:
            self.parent[xr] = yr
        else:
            self.parent[yr] = xr
            if self.rank[xr] == self.rank[yr]:
                self.rank[xr] += 1
```

## Example 3: Connected Components in a Graph
```python
def count_components(n, edges):
    uf = UnionFind(n)
    for u, v in edges:
        uf.union(u, v)
    return len(set(uf.find(x) for x in range(n)))
```

## Diagram
```
Initial: 0 1 2 3 4
Union(0,1): 0-1 2 3 4
Union(1,2): 0-1-2 3 4
...
```

## Extra Study Material
- [Disjoint Set Union (GeeksforGeeks)](https://www.geeksforgeeks.org/disjoint-set-data-structures/)
- [Union Find - LeetCode Explore](https://leetcode.com/explore/learn/card/graph/618/disjoint-set/)

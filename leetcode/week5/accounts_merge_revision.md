# LeetCode: Accounts Merge - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/accounts-merge/description/)

## Problem Statement
Given a list of accounts where each element accounts[i] is a list of strings, where the first element is a name, and the rest are emails. Merge accounts with common emails.

### Example
- Input: accounts = [["John","johnsmith@mail.com","john_newyork@mail.com"],["John","johnsmith@mail.com","john00@mail.com"],["Mary","mary@mail.com"],["John","johnnybravo@mail.com"]]
  Output: [["John", 'john00@mail.com', 'john_newyork@mail.com', 'johnsmith@mail.com'], ["Mary", "mary@mail.com"], ["John", "johnnybravo@mail.com"]]

### Constraints
- 1 <= accounts.length <= 1000
- 2 <= accounts[i].length <= 10
- 1 <= accounts[i][j].length <= 30

---

## Concepts Required
- Union Find (Disjoint Set)
- Hash Map
- Graph

---

## Union Find Approach
- Map each email to an account, union emails with the same owner.
- Time Complexity: O(N log N)

### Pseudocode
```
for each account:
    for each email:
        union(email, first_email)
for each email:
    find root, group emails
return grouped emails with names
```

---

## Python Code
```python
def accountsMerge(accounts):
    from collections import defaultdict
    parent = {}
    def find(x):
        if parent.setdefault(x, x) != x:
            parent[x] = find(parent[x])
        return parent[x]
    for acc in accounts:
        for email in acc[1:]:
            parent[email] = find(acc[1])
    unions = defaultdict(list)
    for email in parent:
        unions[find(email)].append(email)
    res = []
    email_to_name = {email: acc[0] for acc in accounts for email in acc[1:]}
    for root, emails in unions.items():
        res.append([email_to_name[root]] + sorted(emails))
    return res
```

---

## Key Takeaways
- Union Find is optimal for merging overlapping groups.
- Practice both DFS and Union Find approaches.

---

## Follow-up
- How would you handle millions of accounts?
  - Use Union-Find (Disjoint Set Union) for efficient merging and scalability.
- Can you do it with DFS?
  - Yes, treat accounts as a graph and use DFS to find connected components (all emails belonging to the same person).

---

## Related Problems
- Merge Intervals
- Connected Components in a Graph
- Find Duplicate File in System

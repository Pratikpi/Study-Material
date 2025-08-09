# LeetCode: Implement Trie (Prefix Tree) - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/implement-trie-prefix-tree/description/)

## Problem Statement
Implement a trie with insert, search, and startsWith methods.

### Example
- Input: ["Trie","insert","search","search","startsWith","insert","search"]
         [[],["apple"],["apple"],["app"],["app"],["app"],["app"]]
  Output: [null,null,true,false,true,null,true]

### Constraints
- 1 <= word.length <= 2000
- word consists only of lowercase English letters.
- At most 3 * 10^4 calls will be made to insert, search, and startsWith.

---

## Concepts Required
- Trie (Prefix Tree)
- Hash Map
- Tree

---

## Trie Node Approach
- Each node is a dict of children and a boolean for end of word.
- Time Complexity: O(m) per operation, m = word length

### Pseudocode
```
class TrieNode:
    children = {}
    is_end = False
insert(word): traverse/create nodes, mark end
search(word): traverse, check is_end
startsWith(prefix): traverse, return True if path exists
```

---

## Python Code
```python
class TrieNode:
    def __init__(self):
        self.children = {}
        self.is_end = False

class Trie:
    def __init__(self):
        self.root = TrieNode()
    def insert(self, word):
        node = self.root
        for c in word:
            if c not in node.children:
                node.children[c] = TrieNode()
            node = node.children[c]
        node.is_end = True
    def search(self, word):
        node = self.root
        for c in word:
            if c not in node.children:
                return False
            node = node.children[c]
        return node.is_end
    def startsWith(self, prefix):
        node = self.root
        for c in prefix:
            if c not in node.children:
                return False
            node = node.children[c]
        return True
```

---

## Key Takeaways
- Trie is optimal for prefix search.
- Practice both array and dict-based implementations.

---

## Follow-up
- How would you support delete?
- Can you store additional data at each node?

---

## Related Problems
- Add and Search Word
- Word Search II
- Replace Words

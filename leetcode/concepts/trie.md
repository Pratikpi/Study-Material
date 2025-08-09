# Trie (Prefix Tree) - Interview Preparation Guide

## Theory & Intuition
A Trie (pronounced "try") is a tree-like data structure used to efficiently store and retrieve keys in a dataset of strings. Each node represents a character, and paths from the root to leaves represent words.

- **Efficient prefix search**: O(L) time, where L is the length of the word.
- **Space efficient for many shared prefixes.**

### When to Use
- When you need to store a large dictionary of words and support fast prefix queries (e.g., autocomplete, spell-check).

## Example 1: Basic Trie Implementation
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

## Example 2: Word Search with Trie
```python
def findWords(board, words):
    trie = Trie()
    for word in words:
        trie.insert(word)
    # ...DFS using trie for prefix pruning...
```

## Example 3: Autocomplete System
```python
# Store all words in a trie, then traverse down the prefix to collect completions.
```

## Diagram
```
Insert: "cat", "car", "dog"
Trie:
root
 ├─c
 │ ├─a
 │ │ ├─t*
 │ │ └─r*
 └─d
   └─o
     └─g*
(* = end of word)
```

## Extra Study Material
- [Trie Data Structure (GeeksforGeeks)](https://www.geeksforgeeks.org/trie-insert-and-search/)
- [Implement Trie (LeetCode)](https://leetcode.com/problems/implement-trie-prefix-tree/)

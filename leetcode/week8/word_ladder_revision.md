# LeetCode: Word Ladder - Interview Revision Guide

[LeetCode Problem Link](https://leetcode.com/problems/word-ladder/description/)

## Problem Statement
Given two words, beginWord and endWord, and a dictionary wordList, return the length of the shortest transformation sequence from beginWord to endWord, such that:
- Only one letter can be changed at a time.
- Each transformed word must exist in the wordList.

### Example
- Input: beginWord = "hit", endWord = "cog", wordList = ["hot","dot","dog","lot","log","cog"]
  Output: 5

- Input: beginWord = "hit", endWord = "cog", wordList = ["hot","dot","dog","lot","log"]
  Output: 0

### Constraints
- 1 <= beginWord.length <= 10
- 1 <= wordList.length <= 5000
- All words have the same length.
- All words consist of lowercase English letters.

---

## Concepts Required
- Breadth-First Search (BFS)
- Graph Traversal
- String Manipulation

---

## Approach
- Use BFS to find the shortest path from beginWord to endWord.
- For each word, generate all possible one-letter transformations.
- Use a set for fast lookup and to avoid revisiting words.
- Time Complexity: O(N * M^2), N = wordList size, M = word length

### Pseudocode
```
queue = [(beginWord, 1)]
wordSet = set(wordList)
while queue:
    word, length = queue.pop(0)
    if word == endWord: return length
    for each position:
        for each letter:
            nextWord = word with one letter changed
            if nextWord in wordSet:
                queue.append((nextWord, length+1))
                wordSet.remove(nextWord)
return 0
```

---

## Python Code
```python
def ladderLength(beginWord, endWord, wordList):
    wordSet = set(wordList)
    if endWord not in wordSet:
        return 0
    queue = [(beginWord, 1)]
    while queue:
        word, length = queue.pop(0)
        if word == endWord:
            return length
        for i in range(len(word)):
            for c in 'abcdefghijklmnopqrstuvwxyz':
                nextWord = word[:i] + c + word[i+1:]
                if nextWord in wordSet:
                    queue.append((nextWord, length+1))
                    wordSet.remove(nextWord)
    return 0
```

---

## Key Takeaways
- BFS finds the shortest transformation sequence.
- Use a set for O(1) lookups and to avoid revisiting.

---

## Follow-up
- How would you return all shortest transformation sequences?
  - Use BFS to build a graph, then backtrack to construct all shortest paths.
- Can you optimize with bidirectional BFS?
  - Yes, search from both begin and end words to reduce search space.

---

## Related Problems
- Word Ladder II
- Minimum Genetic Mutation

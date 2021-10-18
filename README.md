# Python-Practice

# Week 77 [2/14-2/20]

# [1971](https://leetcode.com/problems/find-if-path-exists-in-graph/)
```python
from collections import defaultdict as dd
def main(n, edges, start, end):
    if start == end:
        return True
    book = dd(set)
    for i, j in edges:
        book[i].add(j)
        book[j].add(i)
    
    def dfs(cur, visited):
        neighbors = book[cur]
        for neighbor in neighbors:
            if neighbor == end:
                return True
            if neighbor not in visited:
                visited.add(neighbor)
                if dfs(neighbor, visited):
                    return True
        return False

    for i in book[start]:
        if dfs(i, set()):
            return True
    return False            
```
#### Assumption: N = the number of edges
#### Complexity: runtime = O(N), space = O(N) with recursive callstack

# [1961](https://leetcode.com/problems/check-if-string-is-a-prefix-of-array/)
```python
def main(s, words):
    s_idx = 0
    s_size = len(s)
    for word in words:
        for letter in word:
            if s_idx == s_size or s[s_idx] != letter:
                return False
            s_idx += 1
        if s_idx == s_size:
            return True
    return False
```
#### Assumption: S = the target string length, W = the number of words to match target
#### Complexity: runtime = O(W+S), space = O(1)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)

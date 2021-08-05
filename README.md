# Python-Practice

# Week 65 [11/22-11/28]

# [1110](https://leetcode.com/problems/delete-nodes-and-return-forest/)
```python
def main(root, to_delete):
   res = []
   last = dfs(root, set(to_delete), res)
   if last:
      res += [last]
   return res

def dfs(root, to_delete, res):
   if not root: return
   root.left = dfs(root.left, to_delete, res)
   root.right = dfs(root.right, to_delete, res)
   if root.val in to_delete:
      if root.left:
         res += [root.left]
      if root.right:
         res += [root.right]
      return
   return root
```
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(N) recursive callstack

# [1026](https://leetcode.com/problems/maximum-difference-between-node-and-ancestor/)
```python
def main(root):
   res = [0]
   dfs(root, res, 0, sys.maxsize)
   return res[0]

def dfs(root, res, maxi, mini):
   if not root: return
   maxi = max(maxi, root.val)
   mini = min(mini, root.val)
   res[0] = max(res[0], maxi-mini)
   dfs(root.left, res, maxi, mini)
   dfs(root.right, res, maxi, mini)
```
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(N) recursive callstack

# [323](https://leetcode.com/problems/number-of-connected-components-in-an-undirected-graph/)
```python
from collections import defaultdict as dd
def main(n, edges):
   book = dd(set)
   for v1, v2 in edges:
      book[v1].add(v2)
      book[v2].add(v1)
   visited = set()
   cnt = 0
   for v1 in range(n):
      if v1 not in visited:
         cnt += 1
         visited.add(v1)
         dfs(book, v1, visited)
   return cnt

def dfs(book, v1, visited):
   for v2 in book[v1]:
      if v2 not in visited:
         visited.add(v2)
         dfs(book, v2, visited)
```
#### Assumption: V = the number of vertices, E = the number of edges
#### Complexity: runtime = O(V + E), space = O(V + E)

# [684](https://leetcode.com/problems/redundant-connection/)
```python
from collections import defaultdict as dd
def main(edges):
   book = dd(set)
   for v1, v2 in edges:
      if v1 in book and v2 in book and dfs(v1, v2, book, set()):
         return [v1, v2]
      book[v1].add(v2)
      book[v2].add(v1)

def dfs(v1, v2, book, visited):
   if v1 not in visited:
      visited.add(v1)
      if v1 == v2:
         return True # cycle
      for v3 in book[v1]:
         if dfs(v3, v2, book, visited):
            return True
```
#### Assumption: V = the number of vertices
#### Complexity: runtime = O(V^2), space = O(V)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)

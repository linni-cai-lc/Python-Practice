# Python-Practice

# Week 90 [5/16-5/22]

# 1. [272](https://leetcode.com/problems/closest-binary-search-tree-value-ii/)
```python
from heapq import heappush, heappop
def main(root, target, k):
   heap = []
        
   def recursiveHelper(cur):
      nonlocal target, k, heap
      if not cur:
         return
      diff = abs(cur.val - target)
      heappush(heap, (-diff, cur.val))
      if len(heap) > k:
         heappop(heap)
      recursiveHelper(cur.left)
      recursiveHelper(cur.right)
   
   recursiveHelper(root)
   res = []
   for diff, val in heap:
      res += [val]
   return res
```
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(N) with recursive callstack

# 2. [257](https://leetcode.com/problems/binary-tree-paths/)
```python
def main(root):
   res = []
        
   def recursiveHelper(cur, path):
      nonlocal res
      if not cur:
         return
      if path:
         path += "->"
      path += str(cur.val)
      if not cur.left and not cur.right:
         res += [path]
      recursiveHelper(cur.left, path)
      recursiveHelper(cur.right, path)
   
   recursiveHelper(root, "")
   return res
```
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(N) with recursive callstack

### Template
# N. []()
```sql
```

# N. []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)

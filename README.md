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

# 3. [270](https://leetcode.com/problems/closest-binary-search-tree-value/)
```python
def main(root, target):
   res = -1
        
   def recursiveHelper(cur):
      nonlocal res
      if not cur:
         return
      if res == -1:
         res = cur.val
      else:
         if abs(cur.val - target) * 100 < abs(res - target) * 100:
            res = cur.val
      recursiveHelper(cur.left)
      recursiveHelper(cur.right)
   
   recursiveHelper(root)
   return res
                    
```
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(N) with recursive callstack

# 4. [199](https://leetcode.com/problems/binary-tree-right-side-view/)
```python
def main(root):
   res = []
        
   def recursiveHelper(cur, level):
      nonlocal res
      if not cur:
         return
      if level == len(res):
         res += [None]
      res[level] = cur.val
      recursiveHelper(cur.left, level+1)
      recursiveHelper(cur.right, level+1)
   
   recursiveHelper(root, 0)
   return res
```
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(N) with recursive callstack

# 5. [337](https://leetcode.com/problems/house-robber-iii/)
```python
    #         rob
    #       /     \
    #   notRob    notRob
    
    #               notRob
    #              /      \
    #  [rob, notRob]      [rob, notRob]

def main(root):
   def recursiveHelper(cur):
      if not cur:
         return [0, 0] # rob, notRob
      left = recursiveHelper(cur.left)
      right = recursiveHelper(cur.right)
      rob = cur.val + left[1] + right[1]
      notRob = max(left) + max(right)
      return [rob, notRob]
   return max(recursiveHelper(root))
```
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(N) with recursive callstack

# 6. [255](https://leetcode.com/problems/verify-preorder-sequence-in-binary-search-tree/)
```python
def main(preorder):
   index = 0
   def recursiveHelper(mini, maxi):
      nonlocal index, preorder
      if index >= len(preorder):
         return True
      insert = preorder[index]
      if mini < insert < maxi:
         index += 1
         return recursiveHelper(mini, insert) or recursiveHelper(insert, maxi)
      else:
         return False
   return recursiveHelper(-sys.maxsize, sys.maxsize)
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

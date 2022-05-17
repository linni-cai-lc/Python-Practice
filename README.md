# Python-Practice

# Week 89 [5/9-5/15]

# 1. [102](https://leetcode.com/problems/binary-tree-level-order-traversal/)
```python
def main(root):
   res = []
        
   def recursiveHelper(cur, level):
      nonlocal res
      if not cur:
            return
      if level == len(res):
            res += [[]]
      res[level] += [cur.val]
      recursiveHelper(cur.left, level+1)
      recursiveHelper(cur.right, level+1)
      
   recursiveHelper(root, 0)
   return res
```
#### Note: recursive method
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(N) with recursive callstack
```python
def main(root):
   if not root:
      return []
   res = []
   stack = [(root, 0)]
   while stack:
      cur, level = stack.pop()
      if level == len(res):
         res += [[]]
      res[level] += [cur.val]
      if cur.right:
         stack += [(cur.right, level+1)]
      if cur.left:
         stack += [(cur.left, level+1)]
   return res
```
#### Note: iterative method
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(N)

# 2. [103](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/)
```python
res = []
        
def recursiveHelper(cur, level):
   nonlocal res
   if not cur:
      return
   if level == len(res):
      res += [[]]
   if level % 2 == 0:
      res[level] += [cur.val]
   else:
      res[level] = [cur.val] + res[level]
   recursiveHelper(cur.left, level+1)
   recursiveHelper(cur.right, level+1)
   
recursiveHelper(root, 0)
return res
```
#### Note: recursive method
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(N) with recursive callstack
```python
def main(root):
   if not root:
      return []
   res = []
   stack = [(root, 0)]
   while stack:
      cur, level = stack.pop()
      if level == len(res):
         res += [[]]
      if level % 2 == 0:
         res[level] += [cur.val]
      else:
         res[level] = [cur.val] + res[level]
      if cur.right:
         stack += [(cur.right, level+1)]
      if cur.left:
         stack += [(cur.left, level+1)]
   return res
```
#### Note: iterative method
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(N)

# 3. [107](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/)
```python
def main(root):
   res = []
        
   def recursiveHelper(cur, level):
      nonlocal res
      if not cur:
         return
      if level == len(res):
         res = [[]] + res
      res[len(res)-1-level] += [cur.val]
      recursiveHelper(cur.left, level+1)    
      recursiveHelper(cur.right, level+1)    
   
   recursiveHelper(root, 0)
   return res
```
#### Note: recursive method
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(N) with recursive callstack
```python
def main(root):
   if not root:
      return []
   res = []
   stack = [(root, 0)]
   while stack:
      cur, level = stack.pop()
      if level == len(res):
         res = [[]] + res
      res[len(res)-1-level] += [cur.val]
      if cur.right:
         stack += [(cur.right, level+1)]
      if cur.left:
         stack += [(cur.left, level+1)]
   return res
```
#### Note: iterative method
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(N)

# 4. [98](https://leetcode.com/problems/validate-binary-search-tree/)
```python
def main(root):
   def recursiveHelper(cur, mini, maxi):
      if not cur:
         return True
      return mini < cur.val < maxi and \
             recursiveHelper(cur.left, mini, cur.val) and \
             recursiveHelper(cur.right, cur.val, maxi)
      
   return recursiveHelper(root, -sys.maxsize, sys.maxsize)
```
#### Note: recursive method
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(N) with recursive callstack
```python
def main(root):
  stack = [(root, -sys.maxsize, sys.maxsize)]
   while stack:
      cur, mini, maxi = stack.pop()
      if mini < cur.val < maxi:
         if cur.left:
            stack += [(cur.left, mini, cur.val)]
         if cur.right:
            stack += [(cur.right, cur.val, maxi)]
      else:
         return False
   return True
```
#### Note: iterative method
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(N)

# 5. [99](https://leetcode.com/problems/recover-binary-search-tree/)
```python
def main(root):
   pred, change1, change2 = None, None, None

   def recursiveHelper(cur):
      nonlocal pred, change1, change2
      if not cur:
         return
      recursiveHelper(cur.left)
      if pred and cur.val < pred.val:
         change2 = cur
         if not change1:
            change1 = pred
         else:
            return
      pred = cur
      recursiveHelper(cur.right)

   recursiveHelper(cur)
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)


### Template
# N. []()
```sql
```

# N. []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)

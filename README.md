# Python-Practice

# Week 92 [5/30-6/5]

# 1. [2096](https://leetcode.com/problems/step-by-step-directions-from-a-binary-tree-node-to-another/)
```python
def main(root, startValue, destValue):
   book = {} 
   def recursive(cur, path, direction):
      nonlocal startValue, destValue
      if not cur:
         return
      curVal = cur.val
      path.add((curVal, direction))
      if curVal in (startValue, destValue):
         book[curVal] = path
      recursive(cur.left, path.copy(), 'L')
      recursive(cur.right, path.copy(), 'R')
   recursive(root, set(), 'ROOT')
   startPath = book[startValue]
   endPath = book[destValue]
   res = ""
   overlap = startPath.intersection(endPath)
   res += (len(startPath) - len(overlap)) * 'U'
   for val, direction in endPath[len(overlap):]:
      res += direction
   return res
```
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(N^2) memory exceed
```python
def main(root, startValue, destValue):
   def recursive(cur, target, path):
      if cur.val == target:
         return True
      if cur.left and recursive(cur.left, target, path):
         path += 'L'
      elif cur.right and recursive(cur.right, target, path):
         path += 'R'
      return path
   startPath = []
   endPath = []
   recursive(root, startValue, startPath)
   recursive(root, destValue, endPath)
   while startPath and endPath and startPath[-1] == endPath[-1]:
      startPath.pop()
      endPath.pop()
   return 'U' * len(startPath) + ''.join(endPath)[::-1]
```
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(N)

# 2. [366](https://leetcode.com/problems/find-leaves-of-binary-tree/)
```python
def main(root):
   res = []
        
   def recursive(cur):
      nonlocal res
      if not cur:
         return -1
      left = recursive(cur.left)
      right = recursive(cur.right)
      maxi = max(left, right) + 1
      if maxi == len(res):
         res += [[]]
      res[maxi] += [cur.val]
      return maxi
   
   recursive(root)
   return res
```
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(N)

# 3. [124](https://leetcode.com/problems/binary-tree-maximum-path-sum/)
```python
def main(root):
   maxi = -sys.maxsize
        
   def recursive(cur):
      nonlocal maxi
      if not cur:
         return 0
      left = max(recursive(cur.left), 0)
      right = max(recursive(cur.right), 0)
      maxi = max(maxi, cur.val + left + right)
      return cur.val + max(left, right)
   
   recursive(root)
   return maxi
```
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(N)

# 4. [235](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/)
```python
def main(root, p, q):
   res = None
        
   def recursive(cur, findP, findQ):
      nonlocal p, q, res
      if not cur or res:
         return False, False
      leftFindP, leftFindQ = recursive(cur.left, findP, findQ)
      rightFindP, rightFindQ = recursive(cur.right, findP, findQ)
      findP = cur.val == p.val or leftFindP or rightFindP
      findQ = cur.val == q.val or leftFindQ or rightFindQ
      if findP and findQ and not res:
         res = cur
      return findP, findQ
   
   recursive(root, False, False)
   return res
```
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(N)
```python
def main(root, p, q):
   cur = root.val
   pv = p.val
   qv = q.val
   if pv > cur and qv > cur:
      return self.lowestCommonAncestor(root.right, p, q)
   elif pv < cur and qv < cur:
      return self.lowestCommonAncestor(root.left, p, q)
   else:
      return root
```
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(N)

# 5. [236](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/)
```python
def main(root, p, q):
   res = None
        
   def recursive(cur, findP, findQ):
      nonlocal p, q, res
      if not cur or res:
         return False, False
      leftFindP, leftFindQ = recursive(cur.left, findP, findQ)
      rightFindP, rightFindQ = recursive(cur.right, findP, findQ)
      findP = cur.val == p.val or leftFindP or rightFindP
      findQ = cur.val == q.val or leftFindQ or rightFindQ
      if findP and findQ and not res:
         res = cur
      return findP, findQ
   
   recursive(root, False, False)
   return res
```
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(N)

# 6. [250](https://leetcode.com/problems/count-univalue-subtrees/)
```python
def main(root):
   if not root:
      return 0
   cnt = 0
   
   def recursive(cur, pre):
      nonlocal cnt
      if not cur:
         return True
      curV = cur.val
      left = recursive(cur.left, curV)
      right = recursive(cur.right, curV)
      if left and right:
         cnt += 1
      return left and right and curV == pre
      
   recursive(root, root.val)
   return cnt
```
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(N)

### Template
# N. []()
```sql
```

# N. []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)

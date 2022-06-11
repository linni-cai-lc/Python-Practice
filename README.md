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

### Template
# N. []()
```sql
```

# N. []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)

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


### Template
# N. []()
```sql
```

# N. []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)

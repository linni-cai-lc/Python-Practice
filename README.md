# Python-Practice

# Week 91 [5/23-5/29]

# 1. [156](https://leetcode.com/problems/binary-tree-upside-down/)
```python
def main(root):
   if not root or not root.left:
      return root
   left = root.left
   right = root.right
   res = self.upsideDownBinaryTree(left)
   left.left = right
   left.right = root
   root.left = None
   root.right = None
   return res
```
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(N)

# 2. [116](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/)
```python
def main(root):
   lst = []
        
   def recursiveHelper(cur, level):
      nonlocal lst
      if not cur:
         return
      if len(lst) == level:
         lst += [None]
      if lst[level]:
         lst[level].next = cur
      lst[level] = cur
      recursiveHelper(cur.left, level+1)
      recursiveHelper(cur.right, level+1)
      
   recursiveHelper(root, 0)
   return root
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

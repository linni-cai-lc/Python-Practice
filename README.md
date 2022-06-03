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

### Template
# N. []()
```sql
```

# N. []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)

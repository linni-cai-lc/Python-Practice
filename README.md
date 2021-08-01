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

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)

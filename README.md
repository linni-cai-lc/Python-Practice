# Python-Practice

# Week 63 [11/8-11/14]
# [114](https://leetcode.com/problems/flatten-binary-tree-to-linked-list/)
```python
def main(root):
   dfs(root, [None])

def dfs(root, pre):
   if not root: return
   dfs(root.right, pre)
   dfs(root.left, pre)
   root.right, pre[0] = pre[0], root
   root.left = None
```
#### Assumption: N = the number of nodes in the tree
#### Complexity: runtime = O(N), space = O(N) recursive call stack

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)

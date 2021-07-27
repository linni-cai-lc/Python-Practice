# Python-Practice

# Week 64 [11/15-11/21]

# [250](https://leetcode.com/problems/count-univalue-subtrees/)
```python
def main(root):
   res = [0]
   dfs(root, None,res)
   return res[0]

def dfs(root, target, res):
   if not root:
      return True
   left = dfs(root.left, root.val, res)
   right = dfs(root.right, root.val, res)
   if not left or not right:
      return False
   res[0] += 1
   return root.val == target
```
#### Assumption: N = the number of nodes in the tree
#### Complexity: runtime = O(N), space = O(N) recursive callstack

# [1660](https://leetcode.com/problems/correct-a-binary-tree/)
```python
def main(root):
   dfs(root, set())
   return root

def dfs(root, visited):
   if not root or (root.left and root.left.val in visited) or (root.right and root.right.val in visited): return None
   visited.add(root.val)
   root.right = dfs(root.right, visited)
   root.left = dfs(root.left, visited)
   return root
```
#### Assumption: N = the number of nodes
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

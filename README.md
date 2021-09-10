# Python-Practice

# Week 71 [1/3-1/9]

# [71](https://leetcode.com/problems/simplify-path/)
```python
def main(path):
   lst = path.split('/')
   stack = []
   for i in lst:
      if i == '' or i == '.':
         continue
      elif i == '..':
         if stack:
            stack.pop()
      else:
         stack += [i]
   return '/' + '/'.join(stack)
```
#### Assumption: N = the length of the given path
#### Complexity: runtime = O(N), space = O(N)

# [1676](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree-iv/)
```python
def main(root, nodes):
   nodes = set(nodes)
   ancestor = None
   def dfs(root):
      nonlocal ancestor
      if not root:
         return 0
      ancestor_cnt = dfs(root.left) + dfs(root.right)
      if root in nodes:
         ancestor_cnt += 1
      if ancestor_cnt == len(nodes) and not ancestor:
         ancestor = root
      return ancestor_cnt
   dfs(root)
   return ancestor
```
#### Assumption: N = the number of nodes
#### Complexity: runtime = O(N), space = O(N) with recursive callstack

# [1329](https://leetcode.com/problems/sort-the-matrix-diagonally/)
```python
def main(mat):
   nrow = len(mat)
   ncol = len(mat[0])
   for col in range(ncol):
      old_col = col
      row = 0
      diag = []
      while row < nrow and col < ncol:
         cur = mat[row][col]
         diag += [cur]
         row += 1
         col += 1
      diag.sort()
      col = old_col
      row = 0
      idx = 0
      while row < nrow and col < ncol:
         mat[row][col] = diag[idx]
         row += 1
         col += 1
         idx += 1
   for row in range(1, nrow):
      old_row = row
      col = 0
      diag = []
      while row < nrow and col < ncol:
         cur = mat[row][col]
         diag += [cur]
         row += 1
         col += 1
      diag.sort()
      row = old_row
      col = 0
      idx = 0
      while row < nrow and col < ncol:
         mat[row][col] = diag[idx]
         row += 1
         col += 1
         idx += 1
   return mat
```
#### Assumption: R = the number of rows, C = the number of columns
#### Complexity: runtime = O(ClogR+RlogC), space = O(C+R)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)

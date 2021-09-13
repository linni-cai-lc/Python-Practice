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
#### Complexity: runtime = O(CR(logR+logC)), space = O(C+R)

# [442](https://leetcode.com/problems/find-all-duplicates-in-an-array/)
```python
def main(nums):
   book = set()
   res = []
   for i in nums:
      if i in book:
         res += [i]
      else:
         book.add(i)
   return res
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(N), space = O(N)

# [1762](https://leetcode.com/problems/buildings-with-an-ocean-view/)
```python
def main(heights):
   size = len(heights)
   maxi = 0
   res = []
   for i in range(size-1, -1, -1):
      cur = heights[i]
      if cur > maxi:
         res += [i]
         maxi = cur
   return res[::-1]     
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(N), space = O(N) with final result

# [894](https://leetcode.com/problems/all-possible-full-binary-trees/)
```python
def main(n):
   res = {}
   def dfs(n):
      nonlocal res
      if n not in res:
         cur = []
         if n == 1:
            cur += [TreeNode(0)]
         elif n % 2 == 1:
            for i in range(n):
               rest = n - 1 - i
               left_path = dfs(i)
               right_path = dfs(rest)
               for left in left_path:
                  for right in right_path:
                     cur_node = TreeNode(0)
                     cur_node.left = left
                     cur_node.right = right
                     cur += [cur_node]
         res[n] = cur
      return res[n]
   dfs(n)
   return res[n]
```
#### Assumption: N = the given number size
#### Complexity: runtime = O(2^N), space = O(2^)

# [647](https://leetcode.com/problems/palindromic-substrings/)
```python
def main(s):
   cnt = 0
   book = {}
   size = len(s)
   visited = set()
   def dfs(start, end):
      nonlocal cnt, book, size, visited
      pair = (start, end)
      if 0 <= start < end <= size and pair not in visited:
         visited.add(pair)
         cur = s[start:end]
         if cur not in book:
            book[cur] = cur == cur[::-1]
         dfs(start+1, end)
         dfs(start+1, end-1)
         dfs(start, end-1)
         cnt += book[cur]
   dfs(0, size)
   return cnt
```
#### Assumption: N = the length of given string
#### Complexity: runtime = O(N^3), space = O(N^3)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)

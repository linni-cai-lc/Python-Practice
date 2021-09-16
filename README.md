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
```python
def main(s):
   if not s:
      return 0
   size = len(s)
   cnt = size
   dp = [[False] * size for _ in range(size)]
   for i in range(size):
      dp[i][i] = True
   for i in range(size-1):
      dp[i][i+1] = s[i] == s[i+1]
      cnt += dp[i][i+1]
   for cur_size in range(3, size+1):
      for i in range(size-cur_size+1):
         j = i + cur_size - 1
         dp[i][j] = dp[i+1][j-1] and s[i] == s[j]
         cnt += dp[i][j]
   return cnt
```
#### Assumption: N = the length of given string
#### Complexity: runtime = O(N^2), space = O(N^2)

# [1877](https://leetcode.com/problems/minimize-maximum-pair-sum-in-array/)
```python
def main(nums):
   nums.sort()
   maxi = 0
   for idx in range(len(nums)//2):
      maxi = max(maxi, nums[idx] + nums[-(idx+1)])
   return maxi
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(NlogN), space = O(1)

# [917](https://leetcode.com/problems/reverse-only-letters/)
```python
def main(s):
   res = list(s)
   size = len(s)
   left = 0
   right = size - 1
   while left < right:
      left_val = res[left]
      while not left_val.isalpha() and left < right:
         left += 1
         left_val = res[left]
      right_val = res[right]
      while not right_val.isalpha() and left < right:
         right -= 1
         right_val = res[right]
      res[left], res[right] = res[right], res[left]
      left += 1
      right -= 1
   return ''.join(res)
```
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N), space = O(N)

# [1557](https://leetcode.com/problems/minimum-number-of-vertices-to-reach-all-nodes/)
```python
def main(n, edges):
   return set(range(n)) - set(end for _, end in edges)
```
#### Assumption: N = the number of nodes
#### Complexity: runtime = O(N), space = O(N)

# [890](https://leetcode.com/problems/find-and-replace-pattern/)
```python
def main(words, pattern):
   def get_pattern(word):
      word_book = {}
      word_format = []
      word_cnt = 0
      for i in word:
         if i not in word_book:
            word_cnt += 1
            word_book[i] = word_cnt
         word_format += [word_book[i]]
      return word_format
   
   pattern_format = get_pattern(pattern)
   res = []
   for word in words:
      word_format = get_pattern(word)
      if word_format == pattern_format:
         res += [word]
   return res
```
#### Assumption: W = the number of words, L = the length of word
#### Complexity: runtime = O(WL), space = O(WL)


### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)

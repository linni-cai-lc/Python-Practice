# Python-Practice

# Week 69 [12/20-12/26]

# [39](https://leetcode.com/problems/combination-sum/)
```python
def main(candidates, target):
   res = []
   dfs(candidates, res, target, [], 0)
   return res

def dfs(candidates, res, target, path, cur):
   if target == 0:
      res += [path]
      return
   for i in range(cur, len(candidates)):
      val = candidates[i]
      if val <= target:
         path += [val]
         dfs(candidates, res, target - val, path[:], i)
         path.pop(-1)
```
#### Assumption: C = the number of candidates, T = the number size of target
#### Complexity: runtime = O(C^T), space = O(T)

# [1973](https://leetcode.com/problems/count-nodes-equal-to-sum-of-descendants/)
```python
def main(root):
   res = [0]
   dfs(root, res)
   return res[0]

def dfs(root, res):
   if not root:
      return 0
   left = dfs(root.left, res)
   right = dfs(root.right, res)
   if root.val == left + right:
      res[0] += 1
   return root.val + left + right
```
#### Assumption: N = the number of elements in the tree
#### Complexity: runtime = O(N), space = O(N) use recursive callstack

# [934](https://leetcode.com/problems/shortest-bridge/)
```python
def shortestBridge(self, grid: List[List[int]]) -> int:
   nrow = len(grid)
   ncol = len(grid[0])
   island1 = set()
   ISLAND = 1
   WATER = 0
   is_island1 = True
   cnt = 0
   DIR = [(-1, 0), (1, 0), (0, 1), (0, -1)]
   mini = sys.maxsize
   
   def dfs(row, col):
      nonlocal mini
      if 0 <= row < nrow and 0 <= col < ncol:
         cur = grid[row][col]
         if cur == ISLAND:
            grid[row][col] = WATER
            if is_island1:
               island1.add((row, col))
            else:
               for row1, col1 in island1:
                  mini = min(mini, abs(row1-row)+abs(col1-col)-int(row1 != row or col1 != col))
            for dr, dc in DIR:
               dfs(row+dr, col+dc)

   for i in range(nrow):
      for j in range(ncol):
         if cnt == 2:
            break
         if grid[i][j] == ISLAND:
            dfs(i, j)
            is_island1 = False
            cnt += 1
   return max(1, mini)
```
#### Note: pass majority 89/96 test, TLE
#### Assumption: R = the number of rows, C = the number of columns in the given grid
#### Complexity: runtime = O(R*C), space = O(R*C)

# [1347](https://leetcode.com/problems/minimum-number-of-steps-to-make-two-strings-anagram/)
```python
from collections import Counter
def main(s, t):
   sc = Counter(s)
   tc = Counter(t)
   cnt = 0
   for i in sc:
      diff = sc[i] - tc[i]
      if diff > 0:
         cnt += diff
   return cnt
```
#### Assumption: S = the length of the given string s, T = the length of the given string t
#### Complexity: runtime = O(S + T), space = O(S + T)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)

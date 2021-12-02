# Python-Practice

# Week 82 [3/21-3/27]

# [1817](https://leetcode.com/problems/finding-the-users-active-minutes/)
```python
from collections import defaultdict as dd
def main(logs, k):
   book = dd(set)
   res = [0] * k
   for i, j in logs:
      book[i].add(j)
   for i in book:
      size = len(book[i])
      if size <= k:
         res[size - 1] += 1
   return res
```
#### Assumption: N = the number of logs
#### Complexity: runtime = O(N), space = O(N)

# [1740](https://leetcode.com/problems/find-distance-in-a-binary-tree/)
```python
def main(root, p, q):
   if p == q:
      return 0
   def dfs(cur):
      if not cur:
         return
      val = cur.val
      if val == p or val == q:
         return cur
      left = dfs(cur.left)
      right = dfs(cur.right)
      if left and right:
         return cur
      else:
         return left or right
   
   def distance(cur, target):
      if not cur:
         return sys.maxsize
      if cur.val == target:
         return 0
      return 1 + min(distance(cur.left, target), distance(cur.right, target))
   
   ancestor = dfs(root)
   return distance(ancestor, p) + distance(ancestor, q)
```
#### Assumption: N = the number of nodes in the tree
#### Complexity: runtime = O(N), space = O(N) with recursive callstack

# [1925](https://leetcode.com/problems/count-square-sum-triples/)
```python
def main(n):
   cnt = 0
   for i in range(1, n+1):
      for j in range(i, n+1):
         sumi = i**2 + j**2
         sq = int(math.sqrt(sumi))
         if 1 <= sumi <= n ** 2 and sq ** 2 == sumi:
            cnt += 1
            if i != j:
               cnt += 1
   return cnt
```
#### Assumption: N = the size of the given number
#### Complexity: runtime = O(N^2), space = O(1)

# [2078](https://leetcode.com/problems/two-furthest-houses-with-different-colors/)
```python
def main(colors):
   size = len(colors)
   right = size - 1
   maxi = 0
   while right > 0:
      if colors[right] != colors[0]:
         maxi = max(maxi, right)
         break
      right -= 1
   left = 0
   while left < size - 1:
      if colors[left] != colors[-1]:
         maxi = max(maxi, size - left - 1)
         break
      left += 1
   return maxi
```
#### Assumption: N = the number of elements in the colors
#### Complexity: runtime = O(N), space = O(1)

# [1472](https://leetcode.com/problems/design-browser-history/)
```python
class BrowserHistory:

    def __init__(self, homepage: str):
        self.lst = [homepage]
        self.idx = 0
        self.end = 0
        

    def visit(self, url: str) -> None:
        self.idx += 1
        if self.idx == len(self.lst):
            self.lst += [url]
        else:
            self.lst[self.idx] = url
        self.end = self.idx
        

    def back(self, steps: int) -> str:
        self.idx = max(0, self.idx - steps)
        return self.lst[self.idx]
        

    def forward(self, steps: int) -> str:
        self.idx = min(self.end, self.idx + steps)
        return self.lst[self.idx]
```
#### Assumption: N = the number of links
#### Complexity:
- space = O(N)
- visit: runtime = O(1)
- back: runtime = O(1)
- forward: runtime = O(1)

# [146](https://leetcode.com/problems/lru-cache/)
```python
from collections import OrderedDict as OD
class LRUCache:
   def __init__(self, capacity):
      self.capacity = capacity
      self.book = OD()
   
   def get(self, key):
      if key in self.book:
         self.book.move_to_end(key)
         return self.book[key]
      return -1

   def put(self, key, value):
      if key in self.book:
         self.book.move_to_end(key)
      self.book[key] = value
      if len(self.book) > self.capacity:
         self.book.popitem(False)
```
#### Assumption: N = the number of items to put/get, C = the cache capacity
#### Complexity: space = O(C)
- get: O(1)
- put: O(1)

# [56](https://leetcode.com/problems/merge-intervals/)
```python
def merge(intervals):
   intervals.sort(key=lambda x:(x[0], x[1]))
   res = []
   for start, end in intervals:
      if not res:
         res += [[start, end]]
      else:
         pre_start, pre_end = res[-1]
         if start <= pre_end:
            res[-1][1] = max(end, pre_end)
         else:
            res += [[start, end]]
   return res
```
#### Assumption: N = the number of intervals in the given list
#### Complexity: runtime = O(NlogN), space = O(N) include the return result space

# [200](https://leetcode.com/problems/number-of-islands/)
```python
def main(grid):
   nrow = len(grid)
   ncol = len(grid[0])
   DIR = ((-1, 0), (1, 0), (0, 1), (0, -1))
   LAND = '1'
   WATER = '0'
   def dfs(row, col):
      if 0 <= row < nrow and 0 <= col < ncol and grid[row][col] == LAND:
         grid[row][col] = WATER
         for dr, dc in DIR:
            dfs(row+dr, col+dc)
   
   cnt = 0
   for i in range(nrow):
      for j in range(ncol):
         if grid[i][j] == LAND:
            cnt += 1
            dfs(i, j)
   return cnt
```
#### Assumption: R = the number of rows in the grid, C = the number of columns in the grid
#### Complexity: runtime = O(R*C), space = O(R*C) with recursive callstack
```python
def main(grid):
   nrow = len(grid)
   ncol = len(grid[0])
   DIR = ((-1, 0), (1, 0), (0, 1), (0, -1))
   LAND = '1'
   WATER = '0'
   cnt = 0
   for i in range(nrow):
      for j in range(ncol):
         if grid[i][j] == LAND:
            cnt += 1
            queue = [(i, j)]
            while queue:
               row, col = queue.pop()
               if grid[row][col] == LAND:
                  grid[row][col] = WATER
                  for dr, dc in DIR:
                     new_row = row+dr
                     new_col = col+dc
                     if 0 <= new_row < nrow and \
                        0 <= new_col < ncol and \
                        grid[new_row][new_col] == LAND:
                        queue += [(row+dr, col+dc)]
   return cnt               
```
#### Assumption: R = the number of rows in the grid, C = the number of columns in the grid
#### Complexity: runtime = O(R*C), space = O(min(R, C))

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)

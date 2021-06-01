# Python-Practice

# Week 46 [7/12-7/18]

# [139](https://leetcode.com/problems/word-break/)
```python
def main(s, wordDict):
   words = set(wordDict)
   dp = [False] * (len(s) + 1)
   dp[0] = True
   for i in range(1, len(s) + 1):
      for j in range(i):
         if dp[j] and s[j:i] in words:
            dp[i] = True
            break
   return dp[len(s)]
```
#### Note: BFS iteration
#### Assumption: N = the length of the string
#### Complexity: runtime = O(N^3), space = O(N)
```python
def main(s, wordDict):
   @lru_cache
   def dfs(s, start, words):
      if start == len(s):
         return True
      for end in range(start+1, len(s)+1):
         if s[start:end] in words and dfs(s, end, words):
            return True
      return False
   
   return dfs(s, 0, frozenset(wordDict))
```
#### Note: DFS recursion
#### Assumption: N = the length of the string
#### Complexity: runtime = O(N^3), space = O(N)

# [140](https://leetcode.com/problems/word-break-ii/)
```python
def wordBreak(self, s: str, wordDict: List[str]) -> List[str]:
   return self.dfs(s, wordDict, {})

def dfs(self, s, wordDict, dp):
   if s in dp:
      return dp[s]
   if not s:
      return []
   res = []
   for word in wordDict:
      if not s.startswith(word):
         continue
      if len(word) == len(s):
         res.append(word)
      else:
         rest = self.dfs(s[len(word):], wordDict, dp)
         for item in rest:
            item = word + ' ' + item
            res += [item]
   dp[s] = res
   return res
```
#### Assumption: N = the length of the string
#### Complexity: runtime = O(N^3), space = O(N)

# [200](https://leetcode.com/problems/number-of-islands/)
```python
def numIslands(self, grid: List[List[str]]) -> int:
   self.DIR = [(-1, 0), (1, 0), (0, -1), (0, 1)]
   self.nrow = len(grid)
   if not self.nrow:
      return 0
   self.ncol = len(grid[0])
   cnt = 0
   for r in range(self.nrow):
      for c in range(self.ncol):
         if grid[r][c] == '1':
            cnt += 1
            self.dfs(grid, r, c)
   return cnt
   
def dfs(self, grid, r, c):
   grid[r][c] = '0'
   for dr, dc in self.DIR:
      if 0 <= r+dr < self.nrow and \
         0 <= c+dc < self.ncol and \
         grid[r+dr][c+dc] == '1':
         self.dfs(grid, r+dr, c+dc)
```
#### Assumption: M, N = dimensions of the given matrix
#### Complexity: runtime = O(MN), space = O(MN)
```python
from collections import deque
def numIslands(self, grid: List[List[str]]) -> int:
   DIR = [(-1, 0), (1, 0), (0, -1), (0, 1)]
   nrow = len(grid)
   if not nrow:
      return 0
   ncol = len(grid[0])
   cnt = 0
   for r in range(nrow):
      for c in range(ncol):
         if grid[r][c] == '1':
            cnt += 1
            grid[r][c] = '0'
            nex = [(r, c)]
            while nex:
               cur_r, cur_c = nex.pop(0)
               for dr, dc in DIR:
                  if 0 <= cur_r+dr < nrow and \
                     0 <= cur_c+dc < ncol and \
                     grid[cur_r+dr][cur_c+dc] == '1':
                     nex += [(cur_r+dr, cur_c+dc)]
                     grid[cur_r+dr][cur_c+dc] = '0'
   return cnt
```
#### Assumption: M, N = dimensions of the given matrix
#### Complexity: runtime = O(MN), space = O(MN)

# [121](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)
```python
def main(prices):
   max_diff = 0
   mini = sys.maxsize
   for idx, val in enumerate(prices):
      if val < mini:
         mini = val
      elif val - mini > max_diff:
         max_diff = val - mini
   return max_diff
```
#### Assumption: N = the number of prices
#### Complexity: runtime = O(N), space = O(1)

# [122](code.com/problems/best-time-to-buy-and-sell-stock-ii/)
```python
def main(prices):
   max_diff = 0
   for idx in range(1, len(prices)):
      if prices[idx] > prices[idx-1]:
         max_diff += prices[idx] - prices[idx-1]
   return max_diff
```
#### Assumption: N = the number of prices
#### Complexity: runtime = O(N), space = O(1)

# [123](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/)
```python
def main(prices):
   cost1 = sys.maxsize
   cost2 = sys.maxsize
   diff1 = 0
   diff2 = 0
   for i in prices:
      cost1 = min(cost1, i)
      diff1 = max(diff1, i - cost1)

      cost2 = min(cost2, i - diff1)
      diff2 = max(diff2, i - cost2)
   return diff2
```
#### Assumption: N = the number of prices
#### Complexity: runtime = O(N), space = O(1)
```python
def main(prices):
   k = 2
   cost = [sys.maxsize] * k
   diff = [0] * k
   for i in prices:
      for j in range(k):
         cost[j] = min(cost[j], i - (diff[j-1] if j > 0 else 0))
         diff[j] = max(diff[j], i - cost[j])
   return diff[k-1]
```
#### Assumption: N = the number of prices
#### Complexity: runtime = O(N), space = O(1)

# [188](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/)
```python
def main(k, prices)
   if k == 0:
      return 0
   cost = [sys.maxsize] * k
   diff = [0] * k
   for i in prices:
      for j in range(k):
         cost[j] = min(cost[j], i - (diff[j-1] if j > 0 else 0))
         diff[j] = max(diff[j], i - cost[j])
   return diff[k-1]
```
#### Assumption: K = the given k size, P = the number of prices
#### Complexity: runtime = O(KP), space = O(K)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)

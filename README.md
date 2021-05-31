# Python-Practice

# Week 45 [7/5-7/11]

# [120](https://leetcode.com/problems/triangle/)
```python
def main(triangle):
   @lru_cache(None)
   def dfs(idx, level):
      if level >= len(triangle) or idx >= len(triangle[level]):
         return 0
      return triangle[level][idx] + min(dfs(idx, level+1), dfs(idx+1, level+1))
   return dfs(0, 0)
```
#### Note: TOP DOWN with recursion
#### Assumption: N = the number of elements in the triangle list
#### Complexity: runtime = O(N^2), space = O(N^2) due to recursive call stack

```python
def main(triangle):
   for row in range(1, len(triangle)):
      for col in range(row + 1):
         cur = sys.maxsize
         if col > 0:
            cur = triangle[row - 1][col - 1]
         if col < row:
            cur = min(cur, triangle[row - 1][col])
         triangle[row][col] += cur
   return min(triangle[-1])
```
#### Note: BOTTOM UP with iteration, add previous min cost to the current location, which means the minimum cost from the top to the current location
#### Assumption: N = the number of elements in the triangle list
#### Complexity: runtime = O(N^2), space = O(1)

# [674](https://leetcode.com/problems/longest-continuous-increasing-subsequence/)
```python
def main(nums):
   cnt = 1
   maxi = 1
   for i in range(1, len(nums)):
      if nums[i] > nums[i-1]:
         cnt += 1
         maxi = max(maxi, cnt)
      else:
         cnt = 1
   return maxi
```
#### Note: no dp needed, since it is strictly increasing, easy for number increasing control
#### Assumption: N = the number of elements
#### Complexity: runtime = O(N), space = O(N)

# [1869](https://leetcode.com/problems/longer-contiguous-segments-of-ones-than-zeros/)
```python
def checkZeroOnes(s):
   maxi_ones = 0
   maxi_zeros = 0
   cnt_ones = 0
   cnt_zeros = 0
   pre = -1
   for i in s:
      if pre == -1:
         pre = i
         if i == '1':
            cnt_ones = 1
         else:
            cnt_zeros = 1
      else:
         if i == pre:
            if i == '1':
               cnt_ones += 1
            else:
               cnt_zeros += 1
         else:
            if i == '1':
               maxi_zeros = max(maxi_zeros, cnt_zeros)
               cnt_zeros = 0
               cnt_ones  = 1
            else:
               maxi_ones = max(maxi_ones, cnt_ones)
               cnt_ones = 0
               cnt_zeros = 1
      pre = i
   return max(maxi_ones, cnt_ones) > max(maxi_zeros, cnt_zeros)                
```
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N), space = O(1)

# [1873](https://leetcode.com/problems/calculate-special-bonus/)
```sql
SELECT employee_id,
    CASE WHEN employee_id % 2 = 1 AND name NOT LIKE "M%" THEN salary
    ELSE 0
    END AS bonus
FROM Employees;
```

# [1859](https://leetcode.com/problems/sorting-the-sentence/)
```python
def sortSentence(s):
   cur = ""
   book = []
   for i in s:
      if i.isdigit():
            book += [(cur, int(i))]
      elif i == " ":
            cur = ""
      else:
            cur += i
   book.sort(key=lambda x:x[1])
   return " ".join([i[0] for i in book])
```
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(NlogN), space = O(N)

# [1854](https://leetcode.com/problems/maximum-population-year/)
```python
from collections import Counter
def maximumPopulation(logs):
   logs.sort()
   book = Counter()
   maxi = sys.maxsize
   maxi_cnt = 0
   for born, dead in logs:
      for i in range(born, dead):
         book[i] += 1
         if book[i] > maxi_cnt or (book[i] == maxi_cnt and i < maxi):
            maxi_cnt = book[i]
            maxi = i
   return book.most_common()[0][0]
```
#### Assumption: N = the number of logs, R = the range of period
#### Complexity: runtime = O(NlogN+NR), space = O(NR)

# [1853](https://leetcode.com/problems/convert-date-format/)
```sql
SELECT DATE_FORMAT(day, "%W, %M %e, %Y") AS day
FROM Days;
```
#### Note: use DATE_FORMAT with appropriate format.

# [1844](https://leetcode.com/problems/replace-all-digits-with-characters/)
```python'
def replaceDigits(s):
   res = []
   letter = None
   for i in s:
      if not letter:
         letter = i
      else:
         res += [letter, chr(ord(letter) + int(i))]
         letter = None
   if letter:
      res += [letter]
   return "".join(res)
```
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N), space = O(N)

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

# [188](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/)
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

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)

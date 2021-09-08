# Python-Practice

# Week 70 [12/27-1/2]

# [253](https://leetcode.com/problems/meeting-rooms-ii/)
```python
from heapq import heappop, heappush
def main(intervals):
   intervals.sort(key=lambda x:x[0])
   room = []
   heappush(room, intervals[0][1])
   for idx in range(1, len(intervals)):
      start, end = intervals[idx]
      if room[0] <= start:
         heappop(room)
      heappush(room, end)
   return len(room)
```
#### Assumption: N = the number of intervals
#### Complexity: runtime = O(NlogN), space = O(N)

# [419](https://leetcode.com/problems/battleships-in-a-board/)
```python
def main(board):
   nrow = len(board)
   ncol = len(board[0])
   SHIP = 'X'
   EMPTY = '.'
   DIR = [(-1,0),(1,0),(0,-1),(0,1)]
   cnt = 0
   
   def dfs(row, col):
      if 0 <= row < nrow and 0 <= col < ncol and board[row][col] == SHIP:
            board[row][col] = EMPTY
            for dr, dc in DIR:
               dfs(row+dr, col+dc)
   
   for i in range(nrow):
      for j in range(ncol):
            if board[i][j] == SHIP:
               dfs(i, j)
               cnt += 1
   return cnt    
```
#### Assumption:
- R = the number of rows in the board
- C = the number of columsn in the board
#### Complexity: runtime = O(R * C), space = O(R * C) with recursive callstack

# [48](https://leetcode.com/problems/rotate-image/)
```python
def main(matrix):
   width = len(matrix)
   def swap(i1, j1, i2, j2):
      matrix[i1][j1], matrix[i2][j2] = matrix[i2][j2], matrix[i1][j1]
   
   def transpose():
      for i in range(width):
            for j in range(i+1, width):
               swap(i, j, j, i)
   
   def reverse():
      for i in range(width):
         for j in range(width // 2):
            swap(i, j, i, -1 - j)
   transpose()
   reverse()
```
#### Assumption: N = the width of matrix
#### Complexity: runtime = O(N^2), space = O(1)

# [582](https://leetcode.com/problems/kill-process/)
```python
from collections import defaultdict as dd
def main(pid, ppid, kill):
   res = set()
   parent_book = dd(list)
   for idx in range(len(pid)):
      cur_pid = pid[idx]
      cur_ppid = ppid[idx]
      if cur_ppid != 0:
         parent_book[cur_ppid] += [cur_pid]
   
   def dfs(cur_pid):
      res.add(cur_pid)
      for child_pid in parent_book[cur_pid]:
         dfs(child_pid)
   
   dfs(kill)
   return res
```
#### Assumption: N = the number of elements in pid/ppid
#### Complexity: runtime = O(N), space = O(N) with recursive callstack

# [91](https://leetcode.com/problems/decode-ways/)
```python
def main(s):
   size = len(s)
   dp = [0] * (size + 1)
   dp[0] = 1
   dp[1] = int(1 <= int(s[0]) <= 9)
   for i in range(2, size + 1):
      cur = int(s[i - 1:i])
      cur_pair = int(s[i - 2:i])
      dp[i] += dp[i - 1] * int(1 <= cur <= 9) + dp[i - 2] * int(10 <= cur <= 26)
   return dp[-1]
```
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N), space = O(N)

# [1268](https://leetcode.com/problems/search-suggestions-system/)
```python
def main(products, searchWord):
   cur = ""
   res = []
   products.sort()
   for i in searchWord:
      cur += i
      res += [list(filter(lambda x: x.startswith(cur), products))[:3]]
   return res
```
#### Assumption: W = the number of product words, S = the length of search word
#### Complexity: runtime = O(SW + WlogW), space = O(1) except return result

# [1353](https://leetcode.com/problems/maximum-number-of-events-that-can-be-attended/)
```python
from heapq import heappush, heappop
def main(events):
   events.sort(reverse=True) # max_start, max_end -> min_start, min_end
   heap = []
   cnt = 0
   end = 0
   while events or heap:
      if not heap:
         end = events[-1][0]
      while events and events[-1][0] <= end:
         heappush(heap, events.pop()[1])
      heappop(heap)
      cnt += 1
      end += 1
      while heap and heap[0] < end:
         heappop(heap)
   return cnt
```
#### Assumption: N = the number of events
#### Complexity: runtime = O(NlogN), space = O(N)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)

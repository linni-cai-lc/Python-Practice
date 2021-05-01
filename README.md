# Python-Practice

# Week 42 [6/14-6/20]

# [1741](https://leetcode.com/problems/find-total-time-spent-by-each-employee/)
```sql
SELECT event_day AS day, emp_id, SUM(out_time-in_time) AS total_time
FROM Employees
GROUP BY day, emp_id;
```

# [1688](https://leetcode.com/problems/count-of-matches-in-tournament/)
```python
from math import ceil
def main(n):
   match = 0
   total_match = 0
   while n >= 2:
      match = n // 2
      total_match += match
      n = ceil(n / 2)
   return total_match
```
#### Assumption: N = the given number size
#### Complexity: runtime = O(logN), space = O(1)

# [758](https://leetcode.com/problems/bold-words-in-string/)
```python
from collections import defaultdict as dd
def main(words, S):
   trie = dd(dict)
   size = len(S)
   intervals = []
   
   for i in words:
      cur = trie
      for j in i:
            if j not in cur:
               cur[j] = {}
            cur = cur[j]
      cur['#'] = 0
   
   def merge_interval(intervals, interval):
      if intervals and interval[0] <= intervals[-1][1]:
            intervals[-1][1] = max(intervals[-1][1], interval[1])
      else:
            intervals += [interval]
            
   for i in range(size):
      cur = trie
      maxi = 0
      for j in range(i, size):
            if S[j] not in cur:
               break
            cur = cur[S[j]]
            if '#' in cur:
               maxi = j + 1
      if maxi:
            merge_interval(intervals, [i, maxi])

   res = ""
   prev = 0
   for i, j in intervals:
      res += S[prev:i] + '<b>' + S[i:j] + '</b>'
      prev = j
   return res + S[prev:]
```
```
def main(words, S):
   trie = {}
   size = len(S)
   intervals = []
   
   for i in words:
      cur = trie
      for j in i:
            if j not in cur:
               cur[j] = {}
            cur = cur[j]
      cur['#'] = 0
   
   def merge_interval(intervals, interval):
      if intervals and interval[0] <= intervals[-1][1]:
            intervals[-1][1] = max(intervals[-1][1], interval[1])
      else:
            intervals += [interval]
            
   for i in range(size):
      cur = trie
      maxi = 0
      for j in range(i, size):
            if S[j] not in cur:
               break
            cur = cur[S[j]]
            if '#' in cur:
               maxi = j + 1
      if maxi:
            merge_interval(intervals, [i, maxi])

   res = ""
   prev = 0
   for i, j in intervals:
      res += S[prev:i] + '<b>' + S[i:j] + '</b>'
      prev = j
   return res + S[prev:]
```
#### Note: This is a difficult easy level problem, it is really confusing how to start with brute force intuitively. The trie and merge interval version is more organized, and the key is to utilize the trie structure to help find the longest valid word -> bold.
#### Assumption: W = the number of words, S = the length of the string
#### Complexity: runtime = O(W+S), space = O(WS)

# [1773](https://leetcode.com/problems/count-items-matching-a-rule/)
```python
def main(items, ruleKey, ruleValue):
   book = {
      "type": 0,
      "color": 1,
      "name": 2
   }
   target_key = book[ruleKey]
   cnt = 0
   for i in items:
      if i[target_key] == ruleValue:
         cnt += 1
   return cnt
```
#### Assumption: N = the number of items in the given list
#### Complexity: runtime = O(N), space = O(1)

# [616](https://leetcode.com/problems/add-bold-tag-in-string/)
```python
def main(s, dict):
   def merge_interval(intervals, interval):
      if intervals and interval[0] <= intervals[-1][1]:
            intervals[-1][1] = max(intervals[-1][1], interval[1])
      else:
            intervals += [interval]

   book = {}
   size = len(s)
   for i in dict:
      cur = book
      for j in i:
            if j not in cur:
               cur[j] = {}
            cur = cur[j]
      cur['#'] = 0

   intervals = []
   for i in range(size):
      cur = book
      maxi = 0
      for j in range(i, size):
            if s[j] not in cur:
               break
            cur = cur[s[j]]
            if '#' in cur:
               maxi = j + 1
      if maxi:
            merge_interval(intervals, [i, maxi])

   res = ""
   prev = 0
   for i, j in intervals:
      res += s[prev:i] + '<b>' + s[i:j] + '</b>'
      prev = j
   return res + s[prev:]
```
#### Note: this is the same as 758
#### Assumption: W = the number of words in the dict, S = the length of the given string
#### Complexity: runtime = O(W + S), space = O(WS)

#
# `ISLAND SERIES`
# [463](https://leetcode.com/problems/island-perimeter/)
```python
def main(grid):
   m = len(grid)
   n = len(grid[0])
   cnt = 0
   for i in range(m):
      for j in range(n):
            if grid[i][j] == 1:
               if i == 0:
                  cnt += 1
               if i == m-1:
                  cnt += 1
               if i > 0 and grid[i-1][j] == 0:
                  cnt += 1
               if i < m-1 and grid[i+1][j] == 0:
                  cnt += 1
               if j == 0:
                  cnt += 1
               if j == n-1:
                  cnt += 1
               if j > 0 and grid[i][j-1] == 0:
                  cnt += 1
               if j < n-1 and grid[i][j+1] == 0:
                  cnt += 1
   return cnt
```
#### Assumption: M = the number of rows of the grid, N = the number of columns of the grid
#### Complexity: runtime = O(MN), space = O(1)

# [2](https://leetcode.com/problems/add-two-numbers/)
```python
def main(l1, l2):
   h1 = l1
   h2 = l2
   add = 0
   p1 = l1
   while h1 and h2:
      sumi = h1.val+h2.val+add
      v1 = sumi%10
      if sumi < 10:
         add = 0
      else:
         add = sumi//10
      h1.val = v1
      p1 = h1
      if h2.next and not h1.next:
         h1.next = ListNode(0)
      if h1.next and not h2.next:
         h2.next = ListNode(0)
      h1 = h1.next
      h2 = h2.next  
   if add:
      p1.next = ListNode(add)
   return l1
```
#### Assumption: N1 = the number of linked list 1, N2 = the number of linked list 2
#### Complexity: runtime = O(max(N1, N2)), space = O(max(N1, N2))

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)

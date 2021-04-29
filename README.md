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
#### Note: This is a difficult easy level problem, it is really confusing how to start with brute force intuitively. The trie and merge interval version is more organized, and the key is to utilize the trie structure to help find the longest valid word -> bold.
#### Assumption: W = the number of words, S = the length of the string
#### Complexity: runtime = O(W+S), space = O(W)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)

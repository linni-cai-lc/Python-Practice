# Python-Practice

# Week 40 [5/31-6/6]

# [1624](https://leetcode.com/problems/largest-substring-between-two-equal-characters/)
```python
def main(s):
   book = {}
   idx = 0
   maxi = -1
   for i in s:
      if i not in book:
         book[i] = idx
      else:
         maxi = max(maxi, idx-book[i]-1)
      idx += 1
   return maxi
```
#### Assumption: N = the given string length
#### Complexity: runtime = O(N), space = O(N) store the first occurrence of each letter in the given string

# [1636](https://leetcode.com/problems/sort-array-by-increasing-frequency/)
```python
from collections import Counter
def main(nums):
   book = Counter(nums).most_common()
   book = sorted(book, key=lambda x:(x[1], -x[0]))
   res = []
   for val, cnt in book:
      res += [val] * cnt
   return res
```
#### Assumption: N = the number of elements in the given nums
#### Complexity: runtime = O(NlogN), space = O(N)

# [1380](https://leetcode.com/problems/lucky-numbers-in-a-matrix/)
```python
import numpy as np
def main(matrix):
   trans = np.transpose(matrix)
   nrow = len(matrix)
   ncol = len(matrix[0])
   res = []
   for i in range(nrow):
      mini_row = min(matrix[i])
      mini_row_idx = matrix[i].index(mini_row)
      if mini_row_idx < ncol:
         maxi_col = max(trans[mini_row_idx])
         if maxi_col == mini_row:
            res += [maxi_col]
   return res
```
#### Assumption: the matrix dimension M X N
#### Complexity: runtime = O(MN), space = O(MN)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
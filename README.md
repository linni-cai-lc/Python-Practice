# Python-Practice

# Week 25 [2/15-2/21]

# [498](https://leetcode.com/problems/diagonal-traverse/)
```python
from collections import defaultdict as dd
def main(matrix):
   if not matrix:
      return matrix
   row_size = len(matrix)
   col_size = len(matrix)
   res = dd(list)
   ans = []
   for i in range(row_size):
      for j in range(col_size):
         k = i + j
         if k % 2 == 0:
            res[k] = [matrix[i][j]] + res[k]
         else:
            res[k] += [matrix[i][j]]
   for i in res:
      ans += res[i]
   return ans
```
#### Assumption: M = the number of rows in the given matrix, N = the number of cols in the given matrix
#### Complexity: runtime = O(MN), space = O(MN)

### Template
# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
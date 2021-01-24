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

# [941](https://leetcode.com/problems/valid-mountain-array/)
```python
def main(arr):
   size = len(arr)
   if size < 3:
      return False
   idx = 1
   while idx < size and arr[idx] > arr[idx-1]:
      idx += 1
   if idx == 1 or idx == size:
      return False
   while idx < size and arr[idx] > arr[idx-1]:
      idx += 1
   return idx == size and arr[idx-1] < arr[idx-2]
```
#### Assumption: N = the number of elements in the given
#### Complexity: runtime = O(N), space = O(1)

### Template
# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
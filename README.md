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

# [59](https://leetcode.com/problems/spiral-matrix-ii/)
```python
def main(n):
   DIRS = [(0,1),(1,0),(0,-1),(-1,0)]
   # -> | <- ^
   #    v    |
   cur = 0
   res = [[0] * n for _ in range(n)]
   x, y = 0, 0
   for i in range(1, n**2+1):
      res[x][y] = i
      dx, dy = DIRS[cur % 4]
      if 0<=x+dx<n and 0<=y+dy<n and not res[x+dx][y+dy]:
            pass
      else:
            cur += 1
            dx, dy = DIRS[cur % 4]
      x += dx
      y += dy
   return res
```
#### Assumption: N = the matrix length size
#### Complexity: runtime = O(N*N), space = O(1)

# [453](https://leetcode.com/problems/minimum-moves-to-equal-array-elements/)
```python
def main(nums):
   return sum(nums) - min(nums) * len(nums)
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(1)

### Template
# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
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

```python
import numpy as np
def main(matrix):
   return set(np.max(matrix, axis=0)).intersection(set(np.min(matrix, axis=1)))
```
#### Find min for each row, find max for each column, use set intersection
#### Assumption: the matrix dimension M X N
#### Complexity: runtime = O(MN), space = O(M+N)

# [1464](https://leetcode.com/problems/maximum-product-of-two-elements-in-an-array/)
```python
def main(nums):
   max_one = max(nums[0], nums[1])
   max_two = min(nums[0], nums[1])
   for i in range(2, len(nums)):
      cur = nums[i]
      if cur > max_one:
         max_two = max_one
         max_one = cur
      elif cur > max_two:
         max_two = cur
   return (max_one-1)*(max_two-1)
```
#### Assumption: N = the number of elements in the given nums
#### Complexity: runtime = O(N), space = O(1)

# [812](https://leetcode.com/problems/largest-triangle-area/)
```python
from math import sqrt

def dist(p1, p2):
   return sqrt((p1[0]-p2[0])**2+(p1[1]-p2[1])**2)
   
def main(points):
   maxi = 0
   for i in range(len(points)):
      for j in range(i, len(points)):
         for k in range(j, len(points)):
            a = dist(points[i], points[j])
            b = dist(points[i], points[k])
            c = dist(points[j], points[k])
            semi = (a+b+c)/2
            area = sqrt(semi*abs(semi-a)*abs(semi-b)*abs(semi-c))
            maxi = max(maxi, area)
   return maxi
```
#### Assumption: N = the number of points
#### Complexity: runtime = O(N^3), space = O(1)

# [1752](https://leetcode.com/problems/check-if-array-is-sorted-and-rotated/)
```python
def main(nums):
   sort_str = ",".join(list(map(str,sorted(nums))))
   sort_str = sort_str + "," + sort_str
   return ",".join(list(map(str,nums))) in sort_str
```
#### Assumption: N = the number of elements in the given nums
#### Complexity: runtime = O(NlogN), space = O(N)

# [1560](https://leetcode.com/problems/most-visited-sector-in-a-circular-track/)
```python
def main(n, rounds):
   arr = [0] * (n + 1)
   maxi = 0
   res = []
   for i in range(len(rounds)-1):
      cur = rounds[i]
      nex = rounds[i+1]
      if cur > nex:
            for j in range(cur, n+1):
               arr[j] += 1
               maxi = max(maxi, arr[j])
            for j in range(1, nex):
               arr[j] += 1
               maxi = max(maxi, arr[j])
      else:
            for j in range(cur, nex):
               arr[j] += 1
               maxi = max(maxi, arr[j])
   last = rounds[-1]
   arr[last] += 1
   maxi = max(maxi, arr[last])
   for idx, val in enumerate(arr):
      if val == maxi:
            res += [idx]
   return res
```
#### Assumption: N = the length of total track, R = the number of rounds
#### Complexity: runtime = O(NR), space = O(N)

# [914](https://leetcode.com/problems/x-of-a-kind-in-a-deck-of-cards/)
```python
from collections import Counter
def main(deck):
   book = Counter(deck)
   size = len(deck)
   vals = book.values()
   for i in range(2, size+1):
      if size % i == 0:
         same = True
         for j in vals:
            same = same and j % i == 0
         if same:
            return True
   return False
```
#### Assumption: N = the number of cards in the deck
#### Complexity: runtime = O(N^2), space = O(N)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)